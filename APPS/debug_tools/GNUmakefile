TOPDIR=..

include $(TOPDIR)/GNUmakeconfig

#
# You should put your special stuff here to override the ones defined
# in $(TOPDIR)/GNUmakeconfig.
#
include $(TOPDIR)/GNUmakerules

LOCAL_CFLAGS=-g
LDFLAGS=

ifeq ($(GUESS_HOST),Darwin)
LOCAL_LIBS+= -L/usr/local/lib -L/usr/lib  -L../../KERN/usr.lib  -lreadline -lm -lpthread -lsctp
else
ifeq ($(GUESS_HOST),LynxOS)
LOCAL_LIBS+= -L/usr/local/v6/lib -mthreads -lnetinet -lnsl -lm  -lsctp
else
ifeq ($(GUESS_HOST),Linux)
LOCAL_LIBS+= -lnsl -lm -ltermcap -lreadline  -lsctp
else
ifeq ($(GUESS_HOST),FreeBSD)
LOCAL_LIBS+= -L/usr/local/v6/lib -lm -lreadline   -lpthread
#LOCAL_LIBS+= /usr/local/v6/lib/libsctp.a -lm -lreadline
else
ifeq ($(GUESS_HOST),NetBSD)
LOCAL_LIBS+= -L/usr/local/v6/lib -lm -lreadline -ltermcap   -lpthread -lsctp
else
ifeq ($(GUESS_HOST),OpenBSD)
LOCAL_LIBS+= -L/usr/local/v6/lib -lm -lreadline -ltermcap  -lsctp
else
ifeq ($(GUESS_HOST),AIX)
LOCAL_LIBS+= -L/usr/local/v6/lib -lm -lsctp
else
ifeq ($(GUESS_HOST),SunOS)
LOCAL_LIBS+= -L/usr/local/v6/lib -lsocket -lnsl -lm -lposix4 -lpthread -ltermcap -lreadline -lhistory  -lsctp
else
LOCAL_LIBS+= -L/usr/local/v6/lib -lsocket -lnsl -lm -lposix4 -lpthread  -lsctp
endif
endif
endif
endif
endif
endif
endif
endif

PROGSRCS= dump_apple_log.c prtcwndlog.c gdbdump_to_bin.c cntcwndlog.c \
parse_log.c to_pcap.c hexdump.c  do_hash.c

OBJSRCS=hashWalk.c primelist.c stdintest.c

SRCS= $(OBJSRCS) $(PROGSRCS) # for creating depend 

OBJS=	$(OBJSRCS:%.c=$(OBJDIR)/%.o) 

PROGS=	$(PROGSRCS:%.c=$(EXEDIR)/%)

all::   $(OBJDIR) $(PROGS) 

include $(TOPDIR)/GNUmaketargets
