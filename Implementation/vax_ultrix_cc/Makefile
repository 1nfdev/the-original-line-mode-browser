#  Make WWW under unix for VAX/ultrix using cc
#
# This directory:
HERE = /userd/tbl/hypertext/WWW/LineMode/Implementation/ultrix_cc

# The directory with the deafult home page in:
DEFAULTS = /userd/tbl/hypertext/WWW/LineMode/Defaults

# Directory for installed binary:
BINDIR = /usr/local/unix


CMN = ../../../Implementation/
LM = ../
COMMON = HTParse.o HTAccess.o HTTP.o
OBJS = www.o $(COMMON) HTBufferFile.o

CFLAGS = -I$(CMN) -I$(LM) -DDEBUG
#CFLAGS = -I$(CMN) -I$(LM) -g  -DDEBUG

CC = cc

# include $(LM)CommonMakefile
#	Makefile for WorldWideWeb line mode browser (www)
#	(c) CERN 1990, 1991 -- see Copyright.html for conditions
#
# This file should be invariant between systems.
#
#	make		Compile and link the software (private version)
#	make install	Link it into the system (implies update and make)
#	make update	Copy installed version into installed version
#	make uninstall	Unlink installed version from the system
#	
# Macros required to be defined already for make:
#
# LM		Line Mode implementation directory with trailing slash
# CMN		Common code directory with trailing slash
# CC		The C compiler
# CFLAGS	Flags for $(CC)
# LFLAGS	Flags for ld
#
# Macros needed for make install:
#
# HERE		This directory
# DEFAULTS	The directory with the deafult home page in
# BINDIR	Directory for installed binary
#______________________________________________________________________

COMMON = HTParse.o HTAccess.o HTTP.o HTFile.o HTFTP.o HTTCP.o
OBJS = www.o $(COMMON) HTBufferFile.o HTFormatText.o

www : $(OBJS)
	$(CC) $(LFLAGS) -o www  $(OBJS)
www.o : $(LM)www.c $(LM)HTBufferFile.h $(CMN)HTUtils.h $(CMN)HTAccess.h
	$(CC) -c $(CFLAGS) $(LM)www.c  

HTBufferFile.o : $(LM)HTBufferFile.c $(LM)HTBufferFile.h $(CMN)HTUtils.h
	$(CC) -c $(CFLAGS) $(LM)HTBufferFile.c  

HTFormatText.o : $(LM)HTFormatText.c $(LM)HTFormatText.h $(CMN)HTUtils.h
	$(CC) -c $(CFLAGS) $(LM)HTFormatText.c  

# Common code:

HTTP.o : $(CMN)HTTP.c $(CMN)HTUtils.h
	$(CC) -c  $(CFLAGS) $(CMN)HTTP.c

HTTCP.o : $(CMN)HTTCP.c $(CMN)HTUtils.h
	$(CC) -c  $(CFLAGS) $(CMN)HTTCP.c

HTFile.o : $(CMN)HTFile.c $(CMN)HTUtils.h
	$(CC) -c  $(CFLAGS) $(CMN)HTFile.c

HTFTP.o : $(CMN)HTFTP.c $(CMN)HTUtils.h
	$(CC) -c  $(CFLAGS) $(CMN)HTFTP.c

HTAccess.o :  $(CMN)HTAccess.c $(CMN)HTUtils.h
	$(CC) -c  $(CFLAGS) $(CMN)HTAccess.c

HTParse.o : $(CMN)HTParse.c $(CMN)HTUtils.h
	$(CC) -c  $(CFLAGS) $(CMN)HTParse.c
#_________________________________________________________________
#
Works/www : www
	- mkdir Works
	- rm Works/www
	cp www Works/www

update : Works/www

install : Works/www
	ln -s $(HERE)/Works/www $(BINDIR)/www
	- mkdir /usr/local/lib
	ln -s $(DEFAULTS) /usr/local/lib/WWW

uninstall :
	rm -r $(BINDIR)/www
	rm -r /usr/local/lib/WWW


