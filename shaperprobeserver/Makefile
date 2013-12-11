
CC=gcc

CFLAGS=-c -Wall -O3 -fno-strict-aliasing -Wno-unused-but-set-variable
LFLAGS=-lm

all: clean probeserver

prober: prober.o 
	$(CC) prober.o wrappers.o tcp_client.o tcpserver.o tbdetect.o -o prober $(LFLAGS)

prober.o: prober.c
	$(CC) $(CFLAGS) prober.c tcp_client.c tcpserver.c wrappers.c tbdetect.c

probeserver: probeserver.o
	$(CC) probeserver.o wrappers.o tcpserver.o tcp_client.o tbdetect.o measflow.o -o shaperprobeserver $(LFLAGS)

probeserver.o: probeserver.c
	$(CC) $(CFLAGS) -DDSERVER probeserver.c wrappers.c tcpserver.c tcp_client.c tbdetect.c measflow.c
tbtest: tbtest.o 
	$(CC) tbtest.o wrappers.o tcp_client.o tcpserver.o tbdetect.o -o tbtest $(LFLAGS) 

tbtest.o: prober.c
	$(CC) $(CFLAGS) tbtest.c tcp_client.c tcpserver.c wrappers.c tbdetect.c

clean:
	rm -rf *.o prober probeserver shaperprobeserver

