ifndef ROOT
$(info ROOT is not defined.)
ROOT=..
endif

include $(ROOT)/globals.mk

MODULES=console framebuffer

#CC = gcc
#CFLAGS = -m32 -nostdlib -nostdinc -fno-builtin -fno-stack-protector \
         -nostartfiles -nodefaultlibs -Wall -Wextra -Werror -c
#LDFLAGS = -T ../link.ld -melf_i386
#AS = nasm
#ASFLAGS = -f elf

all: modules

modules:
	for mm in $(MODULES) ; do \
                make -C $$mm ROOT=$(ROOT) OBJS_DIR=$(OBJS_DIR) INSTALL_DIR=$(INSTALL_DIR) ; \
                make -C $$mm ROOT=$(ROOT) OBJS_DIR=$(OBJS_DIR) INSTALL_DIR=$(INSTALL_DIR) install ; \
        done

install:
	

%.o: %.c
	$(CC) $(CFLAGS)  $< -o $@

%.o: %.s
	$(AS) $(ASFLAGS) $< -o $@

%.o: %.S
	$(AS) $(ASFLAGS) $< -o $@

clean:
	rm *.o loader

cleanall:
	for mm in $(MODULES) ; do \
                make -C $$mm ROOT=$(ROOT) OBJS_DIR=$(OBJS_DIR) INSTALL_DIR=$(INSTALL_DIR) clean; \
        done

