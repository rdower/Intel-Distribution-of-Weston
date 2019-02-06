srcs_libdesktop = [
	'libweston-desktop.c',
	'client.c',
	'seat.c',
	'surface.c',
	'xwayland.c',
	'wl-shell.c',
	'xdg-shell-v6.c',
	xdg_shell_unstable_v6_server_protocol_h,
	xdg_shell_unstable_v6_protocol_c,
]
lib_desktop = shared_library(
	'weston-desktop-@0@'.format(libweston_major),
	srcs_libdesktop,
	include_directories: include_directories('..', '../shared'),
	install: true,
	version: '0.0.@0@'.format(libweston_revision),
	dependencies: dep_libweston
)
dep_lib_desktop = declare_dependency(
	link_with: lib_desktop,
	dependencies: dep_libweston
)

install_headers('libweston-desktop.h', subdir: dir_include_libweston)

pkgconfig.generate(
	lib_desktop,
	filebase: 'libweston-desktop-@0@'.format(libweston_major),
	name: 'libweston-desktop',
	version: version_weston,
	description: 'Desktop shells abstraction library for libweston compositors',
	requires_private: [ lib_weston, dep_wayland_server ],
	subdirs: dir_include_libweston
)