headers = [
  'base.h',
  'pldm_types.h',
  'platform.h',
  'bios.h',
  'states.h',
]

sources = [
  'base.c',
  'platform.c',
  'bios.c'
]

libpldm_headers = ['.', '..']

if get_option('oem-ibm').enabled()
  headers += [
    '../oem/ibm/libpldm/file_io.h'
  ]
  sources += [
    '../oem/ibm/libpldm/file_io.c'
  ]
  libpldm_headers += ['../oem/ibm']
endif

install_headers(
  headers,
  subdir: 'libpldm')

libpldm = library(
  'libpldm',
  sources,
  implicit_include_directories: false,
  include_directories: include_directories(libpldm_headers),
  version: meson.project_version(),
  install: true)

libpldm = declare_dependency(
  include_directories: include_directories(libpldm_headers),
  link_with: libpldm)

import('pkgconfig').generate(
  name: 'libpldm',
  description: 'PLDM protocol encode/decode C lib',
  version: meson.project_version(),
  libraries: libpldm)