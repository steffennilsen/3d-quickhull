
CC=gcc
CXX=g++

CFLAGS=-g -O0 -DDEBUG
CFLAGS=-O3 -DRELEASE

all: qh.out quickhull_c99.out random_generation.out qh-test.out

clean:
	rm -rf *.out *.obj *.dSYM res*

quickhull_c99.out: quickhull.c ../quickhull.h
	${CC} -std=c99 ${CFLAGS} $< -Wall -Wno-null-dereference -o $@ -I..

qh.out: command_line.cpp ../quickhull.h
	${CXX} $< ${CFLAGS} -o $@ -I.. -I../tests -std=c++14

qh-test.out: generate-circle-hull.cpp ../quickhull.h
	${CXX} $< ${CFLAGS} -o $@ -I.. -I../tests -std=c++14

random_generation.out: random_generation.cpp ../quickhull.h
	${CXX} $< ${CFLAGS} -o $@ -I.. -Wall -Wno-null-dereference -Wno-unused-function -std=c++14

run-bench: qh.out
	./bench.sh
	cat log.txt

