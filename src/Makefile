MF=	Makefile

CC=cc
CFLAGS+= -g -I$(PROJ_INCLUDE) -DDEBUG 
LDLAGS+= -lm
TEST_LDFLAGS=$(LDFLAGS) -lcunit

EXE=puma

CODE=\
	io.c \
	pde.c \
	randgen.c \
	puma.c

SRC=\
	$(CODE) \
	main.c

TEST_SRC=\
	$(PROJ_TEST)/test.c \
	$(CODE)

TEST_OBJ=$(TEST_SRC:.c=.o)

OBJ=	$(SRC:.c=.o)

.SUFFIXES:
.SUFFIXES: .c .o

.c.o:
	$(CC) $(CFLAGS) -c $<

all:	$(EXE) test

test: $(TEST_OBJ) $(TEST_SRC)
	$(CC) $(CFLAGS) -c $(PROJ_TEST)/test.c -o $(PROJ_TEST)/test.o
	$(CC) $(CFLAGS) -o $@ $(TEST_OBJ) $(TEST_LDFLAGS)

$(EXE):	$(OBJ)
	$(CC) $(FFLAGS) -o $@ $(OBJ) $(LDFLAGS)

$(OBJ) $(TEST_OBJ):	$(MF) $(INC)

all:
	cp -f $(EXE) test $(PROJ_BIN)

clean:
	rm -f $(OBJ) $(EXE) test $(TEST_OBJ) core $(PROJ_BIN)/*
