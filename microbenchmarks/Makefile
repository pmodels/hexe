CC = 	icc
CPP =  icpc
CFLAGS = -I/home/loden/host_libs/include

CFLAGS =   -O3 -xMIC-AVX512  -ipo -fast -static-intel  -restrict -fasm-blocks   \
		      -I/soft/perftools/tau/papi-knl/include\
			 -I/home/loden/hexe_c/include  -qopenmp 

CFLAGS  += -I../include/

LIBS =  -qopenmp -lpapi -L/soft/perftools/tau/papi-knl/lib/

CLINKFLAGS =	-O3 -fasm-blocks -ipo  -g -qopenmp -lnuma  -lhwloc -qopenmp -L/home/loden/host_libs/lib/ 

default: bin/stencil_5pt.bin\
		bin/stencil_5pt_move_pages.bin\
		bin/stencil_5pt_copy.bin\
		bin/stencil_5pt_fetch.bin\
		bin/stencil_7pt.bin\
		bin/stencil_7pt_copy.bin\
		bin/stencil_7pt_fetch.bin
 
obj/%.o: src/%.c ../libhexeknl.a ../include/hexe.h
	 $(CC) $(CFLAGS) -c -o $@ $<

obj/%_move_pages.o: src/%.c ../libhexeknl.a ../include/hexe.h
	 $(CC) $(CFLAGS) -DMOVE_PAGES -c -o $@ $<

obj/%_copy.o: src/%.c ../libhexeknl.a ../include/hexe.h
	 $(CC) $(CFLAGS) -DCOPY_DATA -c -o $@ $<

bin/%.bin: obj/%.o
	$(CC) $ $(CLINKFLAGS) -o $@ $<  ../libhexeknl.a  



