CFLAGS=-O3 -march=native -mtune=native -ggdb
RELIC_ROOT = ../..

all: lib
	gcc ${CFLAGS} -c test-bench.c -o test-bench.o -I ${RELIC_ROOT}/include -I target/include
	gcc ${CFLAGS} -o test-bench test-bench.o target/lib/librelic_s.a -lgmp

lib:
	mkdir -p target
	cd target; ${RELIC_ROOT}/../preset/x64-ecc-128.sh ${RELIC_ROOT}/../; cmake -DEP_METHD='JACOB;LWNAF;COMBS;INTER' -DEP_ENDOM=off -DBN_METHD=' COMBA;COMBA;MONTY;SLIDE;LEHME;BASIC' -DWITH="MD;BC;DV;BN;FP;EP;ED;EC;CP"  .; make

clean:
	rm -rf target *.o test-bench
