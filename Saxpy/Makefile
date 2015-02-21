CUDA_DIR:=/usr/local/cuda
CC	:=$(CUDA_DIR)/bin/nvcc -keep
CL	:=$(CUDA_DIR)/bin/nvcc -keep -clean
CS	:=/home/archit/Soft/cuda/bin/nvcc

ARCH 	:= sm_30
PG	:= -pg
EXE 	:= saxpy

compute:
	$(CC) -o $(EXE) -arch $(ARCH)  saxpy.cu
	nvdisasm -cfg $(EXE).$(ARCH).cubin | dot -ocfg.png -Tpng 

clear:
	$(CL) saxpy.cu

sim:	
	$(CS) saxpy.cu

clean:
	rm -f *.log \
	rm -f _cuobjdump_*
