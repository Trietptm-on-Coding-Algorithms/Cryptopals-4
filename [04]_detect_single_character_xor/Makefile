include ../target.mk

vpath %.c $(TOOLS)
vpath %.o $(TMP)
vpath %.d $(TMP)

OBJS := ifreq.o xor.o hex.o main.o
OBJS := $(addprefix $(TMP)/, $(OBJS))
DEP = $(OBJS:.o=.d)  



all: build_dir build solve

build: build_dir $(OBJS)
	$(CC) $(CFLAGS) $(OBJS) -o $(TARGET) 

.PHONY : solve
solve: build
	$(TARGET) encoded.txt