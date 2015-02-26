include ../../common/make.config

CUDA_DIR := /usr/local/cuda
CC := $(CUDA_DIR)/bin/nvcc -pg

ARCFLAGS := arch=compute_11,code=sm_11
CFARCH	 := arch=compute_37,code=sm_37
CCFLAGS := -m64 -gencode $(ARCFLAGS) 
CFFLAGS := -m64 -gencode $(CFARCH)

INCLUDE := $(CUDA_DIR)/include
CUDA_LIB_DIR := $(CUDA_DIR)/lib64 

SRC = gaussian.cu
EXE = gaussian

release: $(SRC)
	$(CC) $(CCFLAGS) $(KERNEL_DIM) $(SRC) -o $(EXE) -I$(INCLUDE) -L$(CUDA_LIB_DIR) 

cfg: $(SRC)	
	$(CC) $(CFFLAGS) -cubin $(KERNEL_DIM) $(SRC) 
	nvdisasm -cfg $(EXE).cubin|dot -o$(EXE).png -Tpng

clean:
	rm -f *.log _cuobj* _ptx*
	rm -f gaussian gmon.out
	rm -f $(EXE).png
