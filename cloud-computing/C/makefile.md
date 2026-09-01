**Makefiles**: These are essentially just blue prints for running code emsuring faster speeds
## How they work with example
1. CC = gcc;
2. CFLAGS = Wall, Wextra -02
3. TARGET = draw_line
4. SRCCS = main.c canvas.c
5. OBJS = $(SRCCS:.C=.O)
---
The above lines act just like constants in c for the code
INBUILT commands are .PHONY and all

---
.PHONY is used enable the compiler know the actions
`.PHONY:all run clean`
all: run

 