CC      = gcc
PROF    = -g3
C_FLAGS = -O -Wall $(PROF)
L_FLAGS = -O $(PROF) -lcrypt

#IMC2 - Comment out to disable IMC2 support
IMC = 1

O_FILES = act_comm.o act_info.o act_move.o act_obj.o act_wiz.o comm.o const.o \
          db.o fight.o handler.o interp.o magic.o mob_commands.o mob_prog.o   \
	  save.o special.o update.o

H_FILES = $(wildcard *.h) 

ifdef IMC
   O_FILES := imc.o sha256.o $(O_FILES)
   C_FLAGS := $(C_FLAGS) -DIMC -DIMCMERC
endif

merc: $(O_FILES)
	rm -f merc
	$(CC) -o merc $(O_FILES) $(L_FLAGS)

clean:
	rm -f *.o merc

.c.o: merc.h
	$(CC) -c $(C_FLAGS) $<
