objs := head.o init.o nand.o main.o

nand.bin:$(objs)
	arm-linux-ld -Tnand.lds -o nand_elf $^
	arm-linux-objcopy -O binary -S nand_elf $@
	arm-linux-objdump -D -m arm nand_elf > nand.dis
%.o:%.c
	arm-linux-gcc -Wall -O2 -c -o $@ $<
%.o:%.S
	arm-linux-gcc -Wall -O2 -c -o $@ $<

clean:
	rm -f nand_elf nand.bin nand.dis *.o
