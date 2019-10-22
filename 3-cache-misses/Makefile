CC = gcc
ICS = ..
CFLAGS =  -Og  # -Wall

PROGS = sumvec \
    sumarrayrows\
	sumarraycols\
	sumarray3d\

all: $(PROGS)

$(PROGS): timing.h 

#Note that the following are not necessary and covered by the above line
# sumvec: timing.h

# sumarrayrows: timing.h

# sumarraycols: timing.h

# sumarray3d: timing.h

mountaintarfile:
	tar cvf - mountain > mountain.tar

matmulttarfile:
	tar cvf - matmult > matmult.tar

clean:
	rm -f $(PROGS) *.o *~


