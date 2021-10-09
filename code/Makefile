VPATH = ../bin/
BINPATH = ../bin/
LOGPATH = ../log/
LIBRARYS = -lboost_system -lboost_thread -lboost_chrono -lpthread -lboost_filesystem -lssl -lcrypto 

release_node: node.o miner.o verify.o MyServer.o Blockchain.o transactions.o crypto_stuff.o get_ip.o requests.o process_buffer.o misc.o configuration.o 
	g++ -O3 -std=c++11 $^ ${LIBRARYS} -o ${BINPATH}/$@

debug_node: node.o miner.o verify.o MyServer.o Blockchain.o transactions.o crypto_stuff.o get_ip.o requests.o process_buffer.o misc.o configuration.o 
	g++ -g -Ddebug -std=c++11 $^ ${LIBRARYS} -o ${BINPATH}/$@

node.o: node.cpp
	g++ -c $^ -o ${BINPATH}/$@

miner.o: miner.cpp
	g++ -c $^ -o ${BINPATH}/$@

verify.o: verify.cpp
	g++ -c $^ -o ${BINPATH}/$@

MyServer.o: MyServer.cpp
	g++ -c $^ -o ${BINPATH}/$@

Blockchain.o: Blockchain.cpp
	g++ -c $^ -o ${BINPATH}/$@

transactions.o: transactions.cpp
	g++ -c $^ -o ${BINPATH}/$@

crypto_stuff.o: crypto_stuff.cpp
	g++ -c $^ -o ${BINPATH}/$@

get_ip.o: get_ip.cpp
	g++ -c $^ -o ${BINPATH}/$@

requests.o: requests.cpp
	g++ -c $^ -o ${BINPATH}/$@

process_buffer.o: process_buffer.cpp
	g++ -c $^ -o ${BINPATH}/$@

misc.o: misc.cpp
	g++ -c $^ -o ${BINPATH}/$@

configuration.o: configuration.cpp
	g++ -c $^ -o ${BINPATH}/$@


# 这非常不符合Makefile的指定初衷，但是为了方便，并且不想使用quicktest.sh，因此还是利用Make脚本来执行一些东西。
clean:
	rm -f ${BINPATH}/*.o
	
delete:
	rm -rf _Blockchains
	rm -rf _Blocks
	rm -rf _Hashes
	rm -rf _Pings
	rm -rf _Sessions
	rm outputnode*

run:
	${BINPATH}/release_node 800${index} _peers 127.0.0.1 > ${LOGPATH}/outputnode${index}.txt

run_debug:
	${BINPATH}/debug_node 800${index} _peers 127.0.0.1 > ${LOGPATH}/outputnode${index}.txt