##
## Variables
##

TOPDIR = ..
INCLUDEDIR =  -I $(TOPDIR)/include -I/usr/local/include  
.SUFFIXES: .c
CC = gcc
CFLAGS = -Wall -g

LIB = libPatternR.a 
AVOID =	

SRCS = $(filter-out $(AVOID) ,$(wildcard *.c))
OBJS = $(patsubst %.c,%.o,$(SRCS))

all: install 

install: build
	cp $(LIB) $(TOPDIR)/lib 

build: $(LIB)

clean:
	rm $(OBJS) $(LIB)

##
## local rules
##

$(LIB): $(OBJS)
	$(AR) r $(LIB) $(OBJS)
	ranlib $(LIB)

$(OBJS): %.o :%.c
	@echo COMPILING $< 
	$(CC) -o $@ -c $(CFLAGS) $(INCLUDEDIR)  $< 

