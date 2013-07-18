CXX=g++
#CXXFLAGS=-g -O2 -fopenmp -D_PRINT_WARNINGS
CXXFLAGS=-g -O2 -fopenmp

BLITZINC=`pkg-config --cflags blitz`
BLITZLIB=`pkg-config --libs blitz`

BLASDIR=
BLASINC=-I$(BLASDIR)/include
BLASLIB=-L/usr/lib/atlas-base/ -lcblas -llapack

BOOSTDIR=
BOOSTINC=
BOOSTLIB=-lboost_serialization

BTASDIR=..
BTASINC=-I$(BTASDIR)/include
BTASLIB=  $(BTASDIR)/lib

INCLUDEFLAGS=-I. $(BLITZINC) $(BLASINC) $(BOOSTINC) $(BTASINC)
LIBRARYFLAGS=    $(BLITZLIB) $(BLASLIB) $(BOOSTLIB)

SRC_SAMPLE = main.C dmrg.C driver.C btas_template_specialize.C

OBJ_SAMPLE = $(SRC_SAMPLE:.C=.o)

.C.o	:
	$(CXX) $(CXXFLAGS) $(INCLUDEFLAGS) -c $< -o $@

all	: dmrg.x

dmrg.x	: $(OBJ_SAMPLE)
	$(CXX) $(CXXFLAGS) -o dmrg.x $(OBJ_SAMPLE) $(BTASLIB)/libbtas.a $(LIBRARYFLAGS)

clean	:
	rm *.o *.x *.a;
