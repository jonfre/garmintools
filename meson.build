project('garmintools', ['c'], version : '0.12.0')

cc = meson.get_compiler('c')

build_config = configuration_data()
if host_machine.endian() == 'big'
    build_config.set('WORDS_BIGENDIAN', '1')
endif
build_config.set_quoted('GETTEXT_PACKAGE', meson.project_name())
build_config.set_quoted('LOCALE_DIR', join_paths(get_option('prefix'), get_option('localedir')))

usb = dependency('libusb-1.0')
math = cc.find_library('m', required: false)

# generate config.h include header
configure_file(output: 'config.h', configuration: build_config)
config = declare_dependency(include_directories : include_directories('.'))

subdir('po')
subdir('src')
subdir('python')
subdir('doc')
