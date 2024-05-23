project(
  'libgdeflatestream',
  'cpp',
  license: 'Apache-2.0',
  default_options: [
    'prefix=/usr',
    'warning_level=3',
    'cpp_std=c++11'
  ],
  version: '1.0.2',
  meson_version: '>=0.63.0'
)

cpp_args = ['-DGDEFLATE_BUILDING']

gdeflate_static_dep = dependency('GDeflateStatic')

gdeflate_core = library(
  'GDeflateCore',
  [
    'src/GDeflateCompress.cpp',
    'src/GDeflateDecompress.cpp'
  ],
  install: true,
  version: '1.0.2',
  cpp_args: cpp_args,
  dependencies: [gdeflate_static_dep],
  gnu_symbol_visibility: 'hidden'
)

gdeflate_core_dep = declare_dependency(
  link_with: gdeflate_core,
  include_directories: 'include'
)

install_headers(
  'include/GDeflateCore.h'
)

pkg_mod = import('pkgconfig')
pkg_mod.generate(
	name: 'GDeflateCore',
	filebase: 'GDeflateCore',
	description: '',
	libraries: gdeflate_core_dep,
	version: '1.0.0',
)
