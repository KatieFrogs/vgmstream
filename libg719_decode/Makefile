.PHONY : clean

SHELL = /bin/sh
CC = gcc
FLAGS = -std=gnu99
CFLAGS = -fPIC -march=native -ggdb3 -I. -Ireference_code/include -DVAR_ARRAYS
LDFLAGS = -shared
DEBUGFLAGS = -O0 -D _DEBUG
RELEASEFLAGS = -O2 -D NDEBUG -combine -fwhole-program

TARGET = libg719_decode.so
SOURCES = $(shell echo reference_code/common/*.c reference_code/decoder/*.c g719.c)
HEADERS = $(shell echo reference_code/include/*.h *.h)
OBJECTS = $(SOURCES:.c=.o)

PREFIX = $(DESTDIR)/usr/local
BINDIR = $(PREFIX)/bin

all: $(TARGET)

clean:
	rm -f $(OBJECTS) $(TARGET)

$(TARGET): $(OBJECTS)
	$(CC) $(FLAGS) $(CFLAGS) $(DEBUGFLAGS) $(OBJECTS) -o $@ $(LDFLAGS)
