CC=or1k-elf-gcc
CFLAGS=-Wall -mboard=de0_nano
all: hello.elf hello.s

hello.elf:
	${CC}  $(CFLAGS) -o hello.elf hello.c 

hello.s:
	$(CC) $(CFLAGS) -S -o hello.s hello.c

run: all
	or1k-elf-gdb --eval-command='target remote localhost:50001' --eval-command="load hello.elf"

clean:
	rm hello.elf hello.s

