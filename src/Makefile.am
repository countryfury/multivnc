## Process this file with automake to produce Makefile.in



SUBDIRS = \
	wxServDisc/src\
	libvncclient \
	gui


AM_CPPFLAGS = \
	-IwxServDisc/src \
	$(WX_CXXFLAGS) \
	-DPACKAGE_LOCALE_DIR=\""$(prefix)/$(DATADIRNAME)/locale"\" \
	-DPACKAGE_SRC_DIR=\""$(srcdir)"\" \
	-DPACKAGE_DATA_DIR=\""$(datadir)"\" $(MULTIVNC_CFLAGS)

AM_CFLAGS =\
	 -Wall \
	 -g \
	 $(WX_CPPFLAGS)

bin_PROGRAMS = multivnc

multivnc_SOURCES = \
	MultiVNCApp.cpp   \
	MultiVNCApp.h   \
	VNCConn.cpp   \
	VNCConn.h   \
	dfltcfg.h \
	msgqueue.h

multivnc_LDADD = \
	gui/libMultiVNCgui.a \
	wxServDisc/src/libwxservdisc.la \
	libvncclient/libvncclient.a \
	$(GTK_LIBS) \
	$(WX_LIBS)

if MINGW
multivnc_SOURCES += winres.rc
multivnc_LDADD += -lws2_32

.rc.o:
	 $(WX_RESCOMP) -o $@ $<
endif

if HAVE_GNUTLS
multivnc_LDADD += @GNUTLS_LIBS@
else
if HAVE_LIBSSL
multivnc_LDADD +=  @SSL_LIBS@ @CRYPT_LIBS@
endif
endif


EXTRA_DIST = \
	winres.rc\
	icon.ico
