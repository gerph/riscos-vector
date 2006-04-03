TARGET = vector
LIBS = 
INCS = 
CDEFINES = 
OBJS = \
  vector.o

.SUFFIXES: .s .c .cpp .o

.PHONY: all checklinks clean

# Every time we're run we check that the links are sensible. This keeps
# us consistent
all: $(TARGET) checklinks

.s.o:
	objasm -predefine "No26bitCode SETL {FALSE}" -predefine "No32bitCode SETL {TRUE}" -o ../o/$* ^.$?
	cp ../o/$* $*.o
.c.o:
	cc -funsigned-char $(CDEFINES) $(INCS) -I. -I.. -c -o $@ $<
.cpp.o:
	c++ -funsigned-char $(CDEFINES) $(INCS) -I. -I.. -c -o $@ $<

$(TARGET): $(OBJS) $(LIBS)
	cc -o $(TARGET) $(OBJS) $(LIBS)

clean:
	-rm *.o
	-rm $(TARGET)

# And an explicit check for this
checklinks:
	@mklinks

