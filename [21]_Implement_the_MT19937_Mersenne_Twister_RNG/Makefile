include ../target.mk

vpath %.o $(TMP)



all: build_dir mt_generate solve

mt_generate: build_dir
	$(MAKE) -C $(TOOLS)/ mt19937

.PHONY : solve
solve: mt_generate
	g++ -std=gnu++11 -Wall  -static -I$(TOOLS) -L$(TOOLS_LIB) main.cpp -lmt19937 -o $(TARGET)  
	
	
	$(TARGET) | tee result.txt
	@echo "\n"
	
	