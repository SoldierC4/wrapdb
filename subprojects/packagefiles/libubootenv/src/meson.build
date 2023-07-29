install_headers('libuboot.h')

libubootenv_lib = library(
  'ubootenv',
  ['uboot_env.c', 'uboot_private.h'],
  version: meson.project_version(),
  dependencies: [yaml_dep, zlib_dep],
  install: true
)

fw_printenv = executable(
  'fw_printenv',
  'fw_printenv.c',
  link_with: libubootenv_lib,
  install: true
)

fw_setenv = install_symlink(
  'fw_setenv',
  pointing_to: 'fw_printenv',
  install_dir: get_option('bindir')
)
