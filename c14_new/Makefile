DEBUG = 0
BIN = c13_mbr.bin c14_core.bin c13.bin empty
A_DIR = /home/cjy/a.img
C_DIR = /home/cjy/c.img

all:$(BIN)

.PHONY:all clean

c13_mbr.bin:c13_mbr.asm
	nasm $< -o $@
	dd if=$@ of=$(A_DIR)
	
c14_core.bin:c14_core.asm
	nasm $< -o $@ 
	dd if=$@ of=$(C_DIR) bs=512 seek=1 conv=notrunc
	
c13.bin:c13.asm
	nasm $< -o $@
	dd if=$@ of=$(C_DIR) bs=512 seek=50 conv=notrunc
	
empty:diskdata.txt
	dd if=$< of=$(C_DIR) bs=512 seek=100 conv=notrunc
	touch $@
	
clean:
	$(RM) $(BIN)
