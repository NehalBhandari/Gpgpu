
ifdef OUTPUT
override OUTPUT = -DOUTPUT
endif
CUDA_DIR:= /usr/local/cuda
NVCC 	:= $(CUDA_DIR)/bin/nvcc
ARCHFLAG:= arch=compute_11,code=sm_11
CCFLAGS := -pg -m64 -gencode $(ARCHFLAG)

INCLUDE	:= $(CUDA_DIR)/include

EXE 	:= heartwall

# link objects(binaries) together
heartwall: main.o ./AVI/avilib.o ./AVI/avimod.o 
	$(NVCC) main.o ./AVI/avilib.o ./AVI/avimod.o -I$(INCLUDE) -lm -o $(EXE) 

# compile main function file into object (binary)
main.o: main.cu kernel.cu define.c
	$(NVCC) $(CCFLAGS) $(OUTPUT) $(KERNEL_DIM) main.cu -I./AVI -c -O3

./AVI/avilib.o ./AVI/avimod.o:
	cd AVI; make;

# delete all object files
clean:
	rm -f *.log _cuobj* _ptx*
	rm -f *.o AVI/*.o heartwall *.linkinfo
