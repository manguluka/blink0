# customize the following paths for your computer
CC = xc8
LIB_INC_PATH = "./include"

CHIP = 16F1454

CFLAGS = --chip=$(CHIP) -Q -G  --double=24 --float=24
CFLAGS += --rom=default,-0-FFF,-1FFF-2000
CFLAGS += --codeoffset=0x1000
CFLAGS += --opt=default,+asm,-asmfile,+speed,-space,-debug --addrqual=ignore
CFLAGS += --mode=pro -N64 -I. -I$(LIB_INC_PATH) --warn=0 --asmlist --summary=default,-psect,-class,+mem,-hex,-file --output=default,-inhx032 
CFLAGS += --runtime=default,+clear,+init,-keep,-no_startup,+osccal,-resetbits,-download,-stackcall,+clib

BLINK0_OBJS = usb.p1 usb_hid.p1 usb_descriptors.p1 main.p1 usb_helpers.p1

BLINK0_HDRS = usb_config.h

all: blink0.hex

blink0.hex: $(BLINK0_OBJS)
	$(CC) $(CFLAGS) -o./$@ $(BLINK0_OBJS)

%.p1: %.c $(BLINK0_HDRS) Makefile blink0.h usb_config.h
	$(CC) --pass1 $(CFLAGS) -o./$@ $<

clean:
#	rm -f blink0.hex
	rm -f *.p1 *.d *.pre *.sym *.cmf *.cof *.hxl *.lst *.obj *.rlf *.sdb
	rm -f funclist
