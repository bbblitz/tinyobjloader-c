.PHONY: clean all

# OS specific linker flags for GLFW
UNAME_S := $(shell uname -s)
ifeq ($(UNAME_S),Darwin)
LDFLAGS=-framework OpenGL -lglfw3 -lglew -framework Cocoa -framework IOKit -framework CoreVideo
CFLAGS=-Wall -Wextra -Wshadow -Wformat=2 -pedantic -ansi -O2 -g
endif
ifeq ($(UNAME_S),Linux)
LDFLAGS=-lGL -lGLU -lGLEW -lm -pthread -ldl `pkg-config --libs glfw3`
CFLAGS=-Wall -Wextra -Wshadow -Wformat=2 -pedantic -ansi -O2 -g `pkg-config --cflags glfw3`
endif

all: viewer

viewer: viewer.o trackball.o

viewer.o: viewer.c ../../tinyobj_loader_c.h trackball.h

trackball.o: trackball.c trackball.h

clean:
	@rm -rf viewer viewer.o trackball.o
