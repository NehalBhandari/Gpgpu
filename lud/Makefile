all: lud_cuda 

lud_cuda:
	cd cuda; make

clean:
	rm -f *.log _cuobj* _ptx*
	cd cuda; make clean
