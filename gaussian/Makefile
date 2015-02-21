include ../../common/make.config

CC := $(CUDA_DIR)/bin/nvcc -pg

INCLUDE := $(CUDA_DIR)/include

SRC = gaussian.cu
EXE = gaussian

release: $(SRC)
	$(CC) $(KERNEL_DIM) $(SRC) -o $(EXE) -I$(INCLUDE) -L$(CUDA_LIB_DIR) 

clean:
	rm *.log _cuobj* _ptx*
	rm gaussian
