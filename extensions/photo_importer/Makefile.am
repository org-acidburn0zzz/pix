SUBDIRS = data

extensiondir = $(pkglibdir)/extensions
extension_LTLIBRARIES = libphoto_importer.la

libphoto_importer_la_SOURCES = 		\
	actions.c			\
	actions.h			\
	callbacks.c			\
	callbacks.h			\
	dlg-photo-importer.c		\
	dlg-photo-importer.h		\
	main.c				\
	preferences.h
	
libphoto_importer_la_CFLAGS = $(PIX_CFLAGS) -I$(top_srcdir) -I$(top_builddir)/pix 
libphoto_importer_la_LDFLAGS = $(EXTENSION_LIBTOOL_FLAGS)
libphoto_importer_la_LIBADD = $(PIX_LIBS) ../catalogs/libcatalogs.la ../importer/libimporter.la
if ENABLE_JPEG_TOOLS
libphoto_importer_la_LIBADD += ../image_rotation/libimage_rotation.la
endif 
libphoto_importer_la_DEPENDENCIES = $(top_builddir)/pix/pix$(EXEEXT)

extensioninidir = $(extensiondir)
extensionini_in_files = photo_importer.extension.in.in
extensionini_DATA = $(extensionini_in_files:.extension.in.in=.extension)

@PIX_EXTENSION_IN_RULE@
@PIX_EXTENSION_RULE@

EXTRA_DIST = $(extensionini_in_files) 
DISTCLEANFILES = $(extensionini_DATA) 

dist-hook:
	cd $(distdir); rm -f $(CLEANFILES)

-include $(top_srcdir)/git.mk
