WARNING = -Wall -Wshadow --pedantic
ERROR = -Wvla -Werror
GCC = gcc -std=c99 -g $(WARNING) $(ERROR)
VAL = valgrind --tool=memcheck --log-file=memcheck.txt --leak-check=full --verbose

TESTFALGS = -DTEST_DIVIDE -DTEST_INTERLEAVE -DTEST_SHUFFLE

SRCS = main.c shuffle.c
OBJS = $(SRCS:%.c=%.o)

hw10: $(OBJS)
	$(GCC) $(TESTFALGS) $(OBJS) -o hw10

.c.o:
	$(GCC) $(TESTFALGS) -c $*.c

testall: test1 test2 test3 test4 test5 test6 test7 test8 test9 test10 test11

test1: hw10
	./hw10 4 3 | sort | uniq > output43
	diff -w output43 expected/expected_4_3

test2: hw10
	./hw10 4 5 | sort | uniq > output45
	diff -w output45 expected/expected_4_5

test3: hw10
	./hw10 5 2 | sort | uniq > output52
	diff -w output52 expected/expected_5_2

test4: hw10
	./hw10 6 2 | sort | uniq > output62
	diff -w output62 expected/expected_6_2

test5: hw10
	./hw10 7 3 | sort | uniq > output73
	diff -w output73 expected/expected_7_3

test6: hw10
	./hw10 8 2 | sort | uniq > output82
	diff -w output82 expected/expected_8_2

test7: hw10
	./hw10 11 2 | sort | uniq > output112
	diff -w output112 expected/expected_11_2

test8: hw10
	./hw10 3 1 | sort > output31
	diff -w output31 expected/expected31

test9: hw10
	./hw10 3 2 | sort > output32
	diff -w output32 expected/expected32

test10: hw10
	./hw10 4 2 | sort > output42
	diff -w output42 expected/expected42

test11: hw10
	./hw10 6 2 | sort > output62
	diff -w output62 expected/expected62

clean: # remove all machine generated files
	rm -f hw10 *.o output? *~