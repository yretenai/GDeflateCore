project(
  'libgdeflatestream',
  'cpp',
  license: 'Apache-2.0',
  default_options: [
    'prefix=/usr',
    'warning_level=3',
    'cpp_std=c++11'
  ],
  version: '1.0.1',
  meson_version: '>=0.63.0'
)

cpp_args = ['-DGDEFLATE_BUILDING']

gdeflate_dep = dependency('GDeflate')

gdeflate_core = library(
  'GDeflateCore',
  [
    'src/GDeflateCompress.cpp',
    'src/GDeflateDecompress.cpp'
  ],
  install: true,
  version: '1.0.0',
  cpp_args: cpp_args,
  dependencies: [gdeflate_dep],
  gnu_symbol_visibility: 'hidden'
)

gdeflate_core_dep = declare_dependency(
  link_with: gdeflate_core,
  include_directories: 'include'
)

install_headers(
  'include/GDeflate.h'
)

pkg_mod = import('pkgconfig')
pkg_mod.generate(
	name: 'GDeflateCore',
	filebase: 'GDeflateCore',
	description: '',
	libraries: gdeflate_core,
	version: '1.0.0',
)
