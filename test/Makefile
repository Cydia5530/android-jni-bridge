JAVA_HOME ?= $(shell /usr/libexec/java_home -v 1.7)

OBJDIR    := build

CPPFLAGS  := ${CPPFLAGS} -Iinclude -I${JAVA_HOME}/include -I${JAVA_HOME}/include/darwin -std=c++11 -Wall -Werror
CXXFLAGS  := ${CXXFLAGS} -fno-rtti -fno-exceptions -g
LDFLAGS   := ${LDFLAGS} -L${OBJDIR} -Ldarwin -ljdk-7-jni -ljvm -L${JAVA_HOME}/jre/lib/server -Wl,-rpath,${JAVA_HOME}/jre/lib/server
SRCS      := $(wildcard *.cpp)
OBJS      := $(addprefix $(OBJDIR)/,$(SRCS:%.cpp=%.o))

LD         = g++ ${LDFLAGS}

all: ${OBJDIR}/test
	${OBJDIR}/test

${OBJDIR}/test: ${OBJS}
	${LD} ${LDFLAGS} -o $@ $^

${OBJDIR}/%.o: %.cpp
	$(COMPILE.cpp) $(OUTPUT_OPTION) $<

${OBJS}: | ${OBJDIR}
     
${OBJDIR}:
	mkdir -p ${OBJDIR}

clean:
	rm -fr ${OBJDIR}
