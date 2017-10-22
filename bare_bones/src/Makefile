HOST = i686-elf
AS = ${HOST}-as
CC = ${HOST}-gcc
CFLAGS = -std=gnu99 -ffreestanding -O2 -Wall -Wextra
LDFLAGS = -ffreestanding -O2 -nostdlib

kobjects = boot.o kernel.o
lscript = linker.ld

bbos.bin : $(kobjects) $(lscript)
	$(CC) -T $(lscript) -o bbos.bin $(LDFLAGS) $(kobjects)

kernel.o : kernel.c
	$(CC) -c kernel.c -o kernel.o $(CFLAGS)

boot.o : boot.s
	$(AS) boot.s -o boot.o


