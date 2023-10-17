CC = g++
SRC = src/
CFLAGS = -Wall -pg -O2

.DEFAULT_GOAL = MD.exe

test:
	$(CC) $(CFLAGS) $(SRC)MD.cpp -lm -o MD.exe
	srun --partition=cpar perf stat -e L1-dcache-load-misses -M cpi ./MD.exe < inputdata.txt

test2:
	$(CC) $(CFLAGS) $(SRC)MD2.cpp -lm -o MD2.exe
	srun --partition=cpar perf stat -e L1-dcache-load-misses -M cpi ./MD2.exe < inputdata.txt

gprof1:
	$(CC) $(CFLAGS) $(SRC)MD.cpp -lm -o MD.exe
	./MD.exe < inputdata.txt
	gprof MD.exe gmon.out > analysis1.txt
	cat analysis1.txt

gprof2:
	$(CC) $(CFLAGS) $(SRC)MD2.cpp -lm -o MD2.exe
	./MD2.exe < inputdata.txt
	gprof MD2.exe gmon.out > analysis2.txt
	cat analysis2.txt

clean:
	find . -type f \( ! -path "./src/*" ! -name "Makefile" ! -name "inputdata.txt" \) -exec rm -v {} \;

run:
	./MD.exe < inputdata.txt
