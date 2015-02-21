all: CUDA/leukocyte 

CUDA/leukocyte:
	cd CUDA; make

clean:
	rm -f *.log _cuobj* _ptx*
	cd CUDA; make clean
	rm -f meschach_lib/meschach.a
