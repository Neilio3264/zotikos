BIN_DIR = ../bin
OBJS_DIR = ../obj
INCL_DIR = ../include

OBJS	= $(OBJS_DIR)/zotikos.o $(OBJS_DIR)/logger.o $(OBJS_DIR)/log_stream.o
SOURCE	= zotikos.cpp logger.cpp log_stream.cpp
HEADER	= $(INCL_DIR)/logger.h $(INCL_DIR)/log_stream.h $(INCL_DIR)/log_states.h $(INCL_DIR)/timeutil.h
OUT	= $(BIN_DIR)/zotikos
CC	 = g++
FLAGS	 = -g -c -std=c++11 -Wall
LFLAGS	 = -lpthread

all: $(OBJS)
	$(CC) -g $(OBJS) -o $(OUT) $(LFLAGS)

$(OBJS_DIR)/zotikos.o: zotikos.cpp
	$(CC) $(FLAGS) -c $< -o $@

$(OBJS_DIR)/logger.o: logger.cpp
	$(CC) $(FLAGS) -c $< -o $@

$(OBJS_DIR)/log_stream.o: log_stream.cpp
	$(CC) $(FLAGS) -c $< -o $@

clean:
	rm -f $(OBJS) $(OUT)