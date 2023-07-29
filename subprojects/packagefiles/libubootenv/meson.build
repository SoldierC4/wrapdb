project(
  'libubootenv',
  'c',
  version: '0.3.4',
  license: 'LGPL-2.1-or-later',
  default_options: ['c_std=gnu99'],
  meson_version: '>=0.61.0'
)

add_project_arguments('-DVERSION="' + meson.project_version() + '"', language: 'c')
add_project_arguments('-DDEFAULT_CFG_FILE="' + get_option('default_cfg_file') + '"', language: 'c')
add_project_arguments('-DDEFAULT_ENV_FILE="' + get_option('default_env_file') + '"', language: 'c')

yaml_dep = dependency('yaml-0.1')
zlib_dep = dependency('zlib')

incdir = include_directories('src')

subdir('src')

pkg = import('pkgconfig')
pkg.generate(libubootenv_lib,
  name: 'libubootenv',
  description: 'Library to access U-Boot environment',
  filebase: 'libubootenv'
)

libubootenv_dep = declare_dependency(
  link_with: libubootenv_lib,
  include_directories: incdir,
  version: meson.project_version(),
)

meson.override_dependency('libubootenv', libubootenv_dep)
