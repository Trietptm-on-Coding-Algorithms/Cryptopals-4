include ../target.mk

vpath %.c $(TOOLS)
vpath %.o $(TMP)
vpath %.d $(TOOLS)/$(TMP):$(TMP)


OBJS := b64.o pkcs7.o decrypt_msg.o edit_target.o main.o
OBJS := $(addprefix $(TMP)/, $(OBJS))
DEP = $(OBJS:.o=.d) 


all : solve build build_dir   

build: build_dir $(OBJS) libaes 
	$(CC) $(CFLAGS) -static -L$(TOOLS_LIB) $(OBJS) -o $(TARGET) -laes_128

.PHONY: solve
solve: build
	$(TARGET) input.txt "YELLOW SUBMARINE" | tee result.txt

.PHONY: libaes
libaes:
	@$(MAKE) -C $(TOOLS) aes_128