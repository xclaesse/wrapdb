cappdata = configuration_data()

zlib_dep = dependency('zlib')

libpng_dep = dependency('libpng')
if libpng_dep.found()
  cappdata.set('OPJ_HAVE_LIBPNG', 1)
  cappdata.set('OPJ_HAVE_PNG_H', 1)
endif

libtiff_dep = dependency('libtiff-4')
if libtiff_dep.found()
  cappdata.set('OPJ_HAVE_LIBTIFF', 1)
  cappdata.set('OPJ_HAVE_TIFF_H', 1)
endif

liblcms2_dep = dependency('lcms2')
if liblcms2_dep.found()
  cappdata.set('OPJ_HAVE_LIBLCMS2', 1)
  cappdata.set('OPJ_HAVE_LCMS2_H', 1)
endif

#------------TODO
#if get_option('WITH_ASTYLE')
#  subdir('astyle')
#endif
