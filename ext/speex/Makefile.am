plugin_LTLIBRARIES = libgstspeex.la

libgstspeex_la_SOURCES = gstspeex.c gstspeexdec.c gstspeexenc.c
libgstspeex_la_CFLAGS = \
	$(GST_PLUGINS_BASE_CFLAGS) \
	$(GST_BASE_CFLAGS) \
	$(GST_CFLAGS) \
	$(SPEEX_CFLAGS)
libgstspeex_la_LIBADD = \
	$(GST_PLUGINS_BASE_LIBS) -lgsttag-$(GST_MAJORMINOR) \
	$(GST_BASE_LIBS) \
	$(GST_LIBS) \
	$(SPEEX_LIBS)
libgstspeex_la_LDFLAGS = $(GST_PLUGIN_LDFLAGS) $(LIBM)
libgstspeex_la_LIBTOOLFLAGS = --tag=disable-static

noinst_HEADERS = gstspeexenc.h gstspeexdec.h 

Android.mk: Makefile.am $(BUILT_SOURCES)
	androgenizer \
	-:PROJECT libgstspeex -:SHARED libgstspeex \
	 -:TAGS eng debug \
         -:REL_TOP $(top_srcdir) -:ABS_TOP $(abs_top_srcdir) \
	 -:SOURCES $(libgstspeex_la_SOURCES) \
	 -:CFLAGS $(DEFS) $(DEFAULT_INCLUDES) $(libgstspeex_la_CFLAGS) \
                  -Iexternal/speex/include \
	 -:LDFLAGS $(libgstspeex_la_LDFLAGS) \
	           $(libgstspeex_la_LIBADD) \
	           -ldl \
	 -:PASSTHROUGH LOCAL_ARM_MODE:=arm LOCAL_STATIC_LIBRARIES:=libspeex \
		       LOCAL_MODULE_PATH:='$$(TARGET_OUT)/lib/gstreamer-0.10' \
	> $@
