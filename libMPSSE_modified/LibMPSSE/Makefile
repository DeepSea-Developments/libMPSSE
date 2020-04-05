# Makefile to build the libMPSSE.dll
# --- macros

EXTERNAL_INC_DIR = ../External/Linux/release
ALL_INC = .
ALL_INC_DIR = -I$(EXTERNAL_INC_DIR) -I$(ALL_INC)

ALL_SRC = .
ALL_SRC_DIR = -I$(ALL_SRC)

#Put macros here
#MACROS = -DINFRA_DEBUG_ENABLE
MACROS = 

CC=gcc
AR=ar
LD=ld
#use only o0 during debugging

#flags for release mode compilation
CFLAGS= -O3 -Wall $(MACROS) $(ALL_INC_DIR) -D __linux -D __linux__

#without profiling & coverage
#CFLAGS=  -g -O0 -Wall $(MACROS) $(ALL_INC_DIR)

#with profiling & coverage
#CFLAGS=  -g -O0 -Wall -fprofile-arcs -ftest-coverage D$(MACROS) $(ALL_INC_DIR)

# i2c only
#OBJECTS= ftdi_infra.o ftdi_mid.o ftdi_i2c.o

# spi only
#OBJECTS= ftdi_infra.o ftdi_mid.o ftdi_spi.o

# i2c and spi
OBJECTS= ftdi_infra.o ftdi_mid.o ftdi_i2c.o ftdi_spi.o

LIBS = -L /x86/lib

# --- targets
all:    libMPSSE
libMPSSE:   $(OBJECTS)
		$(AR) -rcs libMPSSE.a $(OBJECTS)
#		$(CC)  -o libMPSSE.so -shared $(OBJECTS) $(LIBS) -W

ftdi_infra.o: $(INFRA_INC_DIR)
		$(CC) $(CFLAGS) -c $(ALL_SRC)/ftdi_infra.c
		
ftdi_mid.o: $(MIDDLE_INC_DIR)
		$(CC) $(CFLAGS) -c $(ALL_SRC)/ftdi_mid.c
		
ftdi_i2c.o: $(I2C_INC_DIR)
		$(CC) $(CFLAGS) -c $(ALL_SRC)/ftdi_i2c.c

ftdi_spi.o: $(SPI_INC_DIR)
		$(CC) $(CFLAGS) -c $(ALL_SRC)/ftdi_spi.c

# --- remove binary and executable files
#clean:
#		del -f tst $(OBJECTS)

clean :
	rm -f *.i *.o *.exe *.bak *.txt *.dll *.lib *.a *.def *.exp
#	rm tst.o serial.o tst.exe


