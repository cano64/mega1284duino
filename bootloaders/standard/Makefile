#Makefile by Cano

CC         = avr-gcc
OBJCOPY        = avr-objcopy
OBJDUMP        = avr-objdump

CFLAGS        = -g -Wall $(OPTIMIZE) $(DEFS)
LDFLAGS       = -Wl,$(LDSECTION)
LDSECTION  = --section-start=.text=0x1F000
OPTIMIZE   = -O2
DEFS       = -DWATCHDOG_MODS -DLED_DDR=DDRB -DLED_PORT=PORTB -DLED_PIN=PINB -DLED=PINB7 -DMAX_TIME_COUNT='F_CPU>>1' -DADABOOT


# Common baud rates
# 9600
# 14400
# 19200
# 28800
# 38400
# 57600
# 76800
# 115200
# 153600
# 230400

# Baud rate friendly crystals
# 1843200L Hz
# 3686400L Hz
# 7372800L Hz
# 11059200L Hz
# 14745600L Hz
# 18432000L Hz
# 22118400L Hz

# Other common crystal freq
# 1000000L Hz
# 8000000L Hz
# 12000000L Hz
# 16000000L Hz
# 20000000L Hz
# 24000000L Hz

MCU_TARGET = atmega1284p
F_CPU = 16000000L
BAUD_RATE = 57600


all : 
	$(MAKE) MCU_TARGET=$(MCU_TARGET) F_CPU=$(F_CPU) BAUD_RATE=$(BAUD_RATE) $(MCU_TARGET)_$(F_CPU)_$(BAUD_RATE).hex
	$(RM) *.o *.elf

$(MCU_TARGET)_$(F_CPU)_$(BAUD_RATE).hex : $(MCU_TARGET)_$(F_CPU)_$(BAUD_RATE).elf
	$(OBJCOPY) -j .text -j .data -O ihex $< $@
	

$(MCU_TARGET)_$(F_CPU)_$(BAUD_RATE).elf : $(MCU_TARGET)_$(F_CPU)_$(BAUD_RATE).o
	$(CC) -mmcu=$(MCU_TARGET) -DBAUD_RATE=$(BAUD_RATE) $(CFLAGS) $(LDFLAGS) $^ -o $@

$(MCU_TARGET)_$(F_CPU)_$(BAUD_RATE).o : ATmegaBOOT.c
	avr-gcc -mmcu=$(MCU_TARGET) -DF_CPU=$(F_CPU) -DBAUD_RATE=$(BAUD_RATE) $(CFLAGS) $(LDFLAGS) -c -g -O2 -Wall  ATmegaBOOT.c -o $@

%.hex: %.elf
	$(OBJCOPY) -j .text -j .data -O ihex $< $@

%.elf: %.o
	$(CC) -DBAUD_RATE=$(BAUD_RATE) $(CFLAGS) $(LDFLAGS) -o $@ $^

%.lst: %.elf
	$(OBJDUMP) -h -S $< > $@

%.srec: %.elf
	$(OBJCOPY) -j .text -j .data -O srec $< $@

%.bin: %.elf
	$(OBJCOPY) -j .text -j .data -O binary $< $@

clean:
	$(RM) *.o

realclean: clean
	$(RM) *.elf *.lst *.map *.sym *.lss *.eep *.srec *.bin

