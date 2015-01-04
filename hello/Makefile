CC=or1k-elf-gcc
AS=or1k-elf-as
CFLAGS=-Wall -mboard=de0_nano -O0  
all: hello.elf

hello.i: hello.c
	${CC}  $(CFLAGS) -E -o hello.i hello.c 

hello.s: hello.i
	${CC} ${CFLAGS} -S -x cpp-output hello.i -o hello.s

hello.o: hello.s
	${AS} hello.s -o hello.o

hello.elf: hello.o
	${CC} ${CFLAGS} hello.o -o hello.elf

run: all
	or1k-elf-gdb --eval-command='target remote localhost:50001' --eval-command="load hello.elf"

clean:
	rm hello.elf hello.s hello.i hello.o

