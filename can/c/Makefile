CANTOOLS_PREFIX ?= /tmp/cantools

CPPFLAGS = \
	$(shell pkg-config --cflags babeltrace2) \
	-I$(CANTOOLS_PREFIX)/include

CFLAGS = -g3 -O0 -Werror -Wall -fPIC -std=c++11
LDFLAGS = \
	  -L$(CANTOOLS_PREFIX)/lib \
	  -lcandbc
CC ?= gcc
CXX ?= g++

.PHONY: all
all: babeltrace-plugin-can.so

babeltrace-plugin-can.so: can.o
	$(CXX) -o $@ $^ -shared $(LDFLAGS)

can.o: can.cpp
	$(CXX) -c $< $(CPPFLAGS) $(CFLAGS)

.PHONY: clean
clean:
	rm -f babeltrace-plugin-can.so can.o
