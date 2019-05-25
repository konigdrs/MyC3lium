##
## Variables
##

# declaramos variables por ejemplo TOPDIR = ../
# Para usar la variable la tenemos que colocar entre parentesis y precedida por un signo de pesos 
# por ejemplo $(TOPDIR) = ../

TOPDIR = ../
INCLUDEDIR =  -I $(TOPDIR)include -I/usr/local/include  

# declaramos los sufijos que seran usados en las reglas implicitas 
.SUFFIXES: .c

# variable que contiene el compilador que se va a utilizar
CC = gcc

# caracteristicas o parametros (banderas) del compilador  que se le agregaran a los programas 
# -Wall = al momento de compilar muestre todos los warnings por ejemplo declaracion de variables que no se utilizan
# -g = depurador 
CFLAGS = -Wall -g

#declaramos otra variable
LIB = libVisioncv.a 

AVOID =

#igualamos la variable src a una lista de todos los archivos que sean .c 
#	quitando de la lista los que se encuentren en la variable avoid 
SRCS = $(filter-out $(AVOID) ,$(wildcard *.c))

#igualamos la variable OBJS a la lista que se encuentra en SRCS pero remplazamos la extencion .c por .o 
OBJS = $(patsubst %.c,%.o,$(SRCS))

#declaramos el objetivo all que compilara todo el programa
# este objetivo es el que se llama por defecto cuando ejecutamos make en la terminal
# su dependencia es install	
all: install 

install: build
# cp libVisioncv.a ../lib 
	cp $(LIB) $(TOPDIR)lib 

#build = libvisioncv.a
build: $(LIB)

clean:
	rm $(OBJS) $(LIB)

##
## local rules
##

# estructura de las reglas del makefile
#	 objetivo = dependencias
#  (TAB)  comandos     		

#libvisioncv.a (objetivo) = lista de archivos objeto (dependencias)	
$(LIB): $(OBJS)
# comandos					
# ar r libvisioncv.a (lista de archivos objeto)					
	$(AR) r $(LIB) $(OBJS)
	ranlib $(LIB)

# el target(objetivo)	: dependen de los %.o y los %.o dependen de los %.c
$(OBJS): %.o :%.c
# @echo COMPILING %.o					 
	@echo COMPILING $< 
	$(CC) -o $@ -c $(CFLAGS) $(INCLUDEDIR)  $< 
# gcc -o (OBJS) -c CFLAGS 	
# $<. El nombre del primer prerequisito
# $*. En la definición de una regla impl�cita, tiene el valor correspondiente al texto que reemplaza el s�mbolo %.
# $?. El nombre de todos los prerequisitos.
# $@. El nombre del archivo del objetivo de la regla. 
