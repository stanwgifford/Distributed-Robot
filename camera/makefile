
CFLAGS +=  -g -O3 -Wall #-Werror
LDFLAGS += -lmosquitto -lv4l2 

# Uncomment this to print out debugging info.
#CFLAGS += -DDEBUG

PROJECT=camera

all: ${PROJECT}

camera: camera.o

camera.o: camera.c

clean:
	rm -rf *.o ${PROJECT}
