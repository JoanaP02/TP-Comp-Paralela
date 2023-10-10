CC = g++
SRC = src/
CFLAGS = -Wall -pg -O3

.DEFAULT_GOAL = MD.exe

MD.exe: $(SRC)/MD.cpp
	$(CC) $(CFLAGS) $(SRC)MD.cpp -lm -o MD.exe

test:
	$(CC) $(CFLAGS) $(SRC)MD.cpp -lm -o MD.exe
	./MD.exe -i inputdata.txt
	gprof MD.exe gmon.out > analysis.txt
	cat analysis.txt

test2:
	$(CC) $(CFLAGS) $(SRC)MD2.cpp -lm -o MD2.exe
	./MD2.exe -i inputdata.txt
	gprof MD.exe gmon.out > analysis2.txt
	cat analysis2.txt

clean2:
	rm ./MD2.exe

clean:
	rm ./MD.exe
	rm ./MD2.exe

run:
	./MD.exe < inputdata.txt