vorbis_sources = [
  'analysis.c',
  'bitrate.c',
  'block.c',
  'codebook.c',
  'envelope.c',
  'floor0.c',
  'floor1.c',
  'info.c',
  'lookup.c',
  'lpc.c',
  'lsp.c',
  'mapping0.c',
  'mdct.c',
  'psy.c',
  'registry.c',
  'res0.c',
  'sharedbook.c',
  'smallft.c',
  'synthesis.c',
  'window.c',
]

vorbisfile_sources = ['vorbisfile.c']

vorbisenc_sources = ['vorbisenc.c']

if host_machine.system() == 'windows'
    # Seems a bit weird, but this is what upstream does.
    vorbis_sources += vorbisenc_sources
endif

math_dep = meson.get_compiler('c').find_library('m', required: false)

vorbis_lib = library('vorbis', vorbis_sources,
  include_directories : [incdir],
  dependencies : [ogg_dep, math_dep],
  vs_module_defs: '../win32/vorbis.def',
)

vorbis_dep = declare_dependency(link_with : vorbis_lib,
  include_directories : incdir,
  dependencies: math_dep)

vorbisfile_lib = library('vorbisfile', vorbisfile_sources,
  include_directories : [incdir],
  link_with: vorbis_lib,
  dependencies : [ogg_dep, math_dep],
  vs_module_defs: '../win32/vorbisfile.def',
)

vorbisfile_dep = declare_dependency(link_with : vorbisfile_lib,
  include_directories : incdir)

vorbisenc_lib = library('vorbisenc', vorbisenc_sources,
  include_directories : [incdir],
  link_with: vorbis_lib,
  dependencies : [ogg_dep, math_dep],
  vs_module_defs: '../win32/vorbisenc.def',
)

vorbisenc_dep = declare_dependency(link_with : vorbisenc_lib,
  include_directories : incdir)

test_sharedbook = executable('test_sharedbook', 'sharedbook.c',
  c_args : '-D_V_SELFTEST',
  include_directories : [incdir],
  link_with : vorbis_lib,
  dependencies: [ogg_dep, math_dep],
)

test('sharedbook', test_sharedbook)
