WARNING = -Wall -Wshadow --pedantic
ERROR = -Wvla -Werror
GCC = gcc -std=c99 -g $(WARNING) $(ERROR)
VAL = valgrind --tool=memcheck --log-file=memcheck.txt --leak-check=full --verbose

TESTFALGS = -DTEST_DIVIDE -DTEST_INTERLEAVE -DTEST_SHUFFLE

SRCS = main.c shuffle.c
OBJS = $(SRCS:%.c=%.o)

hw09: $(OBJS)
	$(GCC) $(TESTFALGS) $(OBJS) -o hw09

.c.o:
	$(GCC) $(TESTFALGS) -c $*.c

testall: test1 test2 test3

test1: hw09
	./hw09 4 | sort > output4
	diff -w output4 expected/expected4

test2: hw09
	./hw09 8 | sort > output8
	diff -w output8 expected/expected8

test3: hw09
	./hw09 11 | sort > output11
	diff -w output11 expected/expected11

clean: # remove all machine generated files
	rm -f hw09 *.o output? *~