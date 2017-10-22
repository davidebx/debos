HOST = i686-elf
AS = $(HOST)-as
CC = $(HOST)-gcc
CFLAGS = -std=gnu99 -ffreestanding -O2 -Wall -Wextra
LDFLAGS = -ffreestanding -O2 -nostdlib
SRC_DIR = src
PREFIX := bin
DIR := $(PREFIX)

kobjects = $(PREFIX)/boot.o \
	   $(PREFIX)/kernel.o

lscript = ${SRC_DIR}/linker.ld

$(PREFIX)/bbos.bin : $(kobjects) $(lscript)  | $(DIR)
	$(CC) -T $(lscript) -o $(PREFIX)/bbos.bin $(LDFLAGS) $(kobjects)

$(PREFIX)/kernel.o : $(SRC_DIR)/kernel.c | $(DIR)
	$(CC) -c $(SRC_DIR)/kernel.c -o $(PREFIX)/kernel.o $(CFLAGS)

$(PREFIX)/boot.o : $(SRC_DIR)/boot.s | $(DIR)
	$(AS) $(SRC_DIR)/boot.s -o $(PREFIX)/boot.o

$(DIR):
	mkdir -p $(PREFIX)

clean:
	rm -rf bin
