plugin_LTLIBRARIES = libgstjpeg.la

libgstjpeg_la_SOURCES = \
	gstjpeg.c \
	gstjpegenc.c \
	gstjpegdec.c \
	gstsmokeenc.c \
	smokecodec.c \
	gstsmokedec.c

libgstjpeg_la_CFLAGS = $(GST_PLUGINS_BASE_CFLAGS) $(GST_BASE_CFLAGS) $(GST_CFLAGS)
libgstjpeg_la_LIBADD = $(GST_PLUGINS_BASE_LIBS) $(GST_BASE_LIBS) $(GST_LIBS) -lgstvideo-$(GST_MAJORMINOR) \
	$(JPEG_LIBS) $(LIBM)
libgstjpeg_la_LDFLAGS = $(GST_PLUGIN_LDFLAGS)
libgstjpeg_la_LIBTOOLFLAGS = --tag=disable-static

noinst_HEADERS = \
	gstjpeg.h \
	gstjpegdec.h gstjpegenc.h \
	gstsmokeenc.h gstsmokedec.h \
	smokecodec.h smokeformat.h

Android.mk: Makefile.am $(BUILT_SOURCES)
	androgenizer \
	-:PROJECT libgstjpeg -:SHARED libgstjpeg \
	 -:TAGS eng debug \
         -:REL_TOP $(top_srcdir) -:ABS_TOP $(abs_top_srcdir) \
	 -:SOURCES $(libgstjpeg_la_SOURCES) \
	 -:CFLAGS $(DEFS) $(DEFAULT_INCLUDES) $(libgstjpeg_la_CFLAGS) \
                  -Iexternal/jpeg \
	 -:LDFLAGS $(libgstjpeg_la_LDFLAGS) \
	           $(libgstjpeg_la_LIBADD) \
	           -ldl \
	 -:PASSTHROUGH LOCAL_ARM_MODE:=arm \
		       LOCAL_MODULE_PATH:='$$(TARGET_OUT)/lib/gstreamer-0.10' \
	> $@
