#!/bin/bash

TOP_DIR = $(shell pwd)

export CROSS_COMPILER := arm-none-eabi-
CC     := $(CROSS_COMPILER)gcc
AR     := $(CROSS_COMPILER)ar

SOURCES = $(wildcard source/common/*.c) $(wildcard source/h264/*.c)

OBJS = $(SOURCES:.c=.o)

LIB_NAME = libhantro-vc8000-nano-e.a

CFLAGS += -I$(TOP_DIR)/inc -I$(TOP_DIR)/source/common -I$(TOP_DIR)/source/h264
CFLAGS += -g -ggdb -O3 -Wall -std=gnu17 -nostdlib -mcpu=cortex-m55 -mcmse -mthumb
CFLAGS += -fno-short-enums -ffixed-r9
#CFLAGS += -DH264ENC_TRACE

.PHONY : all clean

all : $(OBJS)
	$(AR) rcs $(LIB_NAME) $(OBJS)

$(OBJS) : %.o : %.c
	$(CC) $(CFLAGS) -c $< -o $@

clean :
	@rm -rf $(OBJS) $(LIB_NAME)

