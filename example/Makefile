##
## Variables
##


TOPDIR = ../
INCLUDEDIR = -I $(TOPDIR)/include 
LIBDIRS = -L $(TOPDIR)/lib 
#LIBS = 
LIBS = -lm  
.SUFFIXES: .c
CC = gcc
CFLAGS =-Wall 
AVOID = 
SRCS = $(filter-out $(AVOID) ,$(wildcard *.c))
OBJS = $(patsubst %.c,%.o,$(SRCS))
EXAMPLES= $(patsubst %.c,%,$(SRCS))

all: $(EXAMPLES)

##
## local rules
##

$(OBJS): %.o :%.c
	$(CC) -o $@ -c $(CFLAGS) $(INCLUDEDIR)  $< 

$(EXAMPLES): % : %.o
	$(CC) -o $@ $(CFLAGS) $(LIBDIRS) $< $(LIBS)

clean:
	rm $(OBJS) $(EXAMPLES)

rtxt:
	rm *.txt
