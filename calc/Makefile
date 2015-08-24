QPCLOC	:=    ..
QPCLIB	:= $(QPCLOC)/ports/posix/rel/libqp.a
QPCCONF	:= dbg
SRCS	:= calc.c bsp.c main.c
OBJS	:= $(SRCS:%.c=%.o)
CC	:= gcc
FLAGS	:= -DQ_SPY -Wall -g -I$(QPCLOC)/include -I$(QPCLOC)/ports/posix
LIB	:= -lncurses -L$(QPCLOC)/ports/posix/$(QPCCONF)/ -lqp

all: bin bin/calc

bin:
	mkdir -p bin

bin/calc: ${OBJS}
	( cd $(QPCLOC)/ports/posix; make )
	${CC} ${FLAGS} -Wl,-Map=bin/calc.map -o $@ $^ ${LIB}

.c.o: ${SRCS}
	${CC} ${FLAGS} -c $<

.PHONY:
	clean

clean:
	rm -f bin/calc* *.o

