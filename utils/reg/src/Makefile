CC = gcc
#CFLAGS += -I$(LINUX_DIR)/drivers/net/rt_rdm -I$(LINUX_DIR)/include
OBJS = reg.o

all: reg

%.o: %.c
	$(CC) $(CFLAGS) -c -o $@ $<

reg: $(OBJS)
	$(CC) -o $@ $(OBJS)

clean:
	rm -f reg
