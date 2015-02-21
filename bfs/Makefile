include ../../common/make.config

CS := $(CUDA_DIR)/din/nvcc 

CUDA_DIR := /usr/local/cuda-6.5

CC := $(CUDA_DIR)/bin/nvcc -pg -keep 

CL := $(CUDA_DIR)/bin/nvcc -pg -keep -clean

INCLUDE := $(CUDA_DIR)/include

ARCH = sm_30

SRC = bfs.cu

EXE = bfs

sim: $(SRC)
	$(CS) $(SRC) -arch $(ARCH) -o $(EXE) -I$(INCLUDE) -L$(CUDA_LIB_DIR) 

release: $(SRC)
	$(CC) $(SRC) -arch $(ARCH) -o $(EXE) -I$(INCLUDE) -L$(CUDA_LIB_DIR) 

cgarb: $(SRC)
	$(CL) $(SRC) -arch $(ARCH) -o $(EXE) -I$(INCLUDE) -L$(CUDA_LIB_DIR) 


enum: $(SRC)
	$(CC) -deviceemu $(SRC) -o $(EXE) -I$(INCLUDE) -L$(CUDA_LIB_DIR) 

debug: $(SRC)
	$(CC) -g $(SRC) -o $(EXE) -I$(INCLUDE) -L$(CUDA_LIB_DIR) 

debugenum: $(SRC)
	$(CC) -g -deviceemu $(SRC) -o $(EXE) -I$(INCLUDE) -L$(CUDA_LIB_DIR) 

clean: $(SRC)
	rm -f 	*.log \
		./_cuobj* \
		./_ptxplus* 
	rm -f $(EXE) $(EXE).linkinfo result.txt
