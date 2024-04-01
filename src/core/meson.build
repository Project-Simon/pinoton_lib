boost_dep = dependency('boost', modules : ['program_options'], required : true)
thread_dep = dependency('threads', required : true)

core_dep = [boost_dep, thread_dep]

core_src = files([
    'buffer_sync.cpp',
    'dma_heaps.cpp',
    'rpicam_app.cpp',
    'options.cpp',
    'post_processor.cpp',
])

# Generate a version string.
version_cmd = [meson.project_source_root() / 'utils' / 'version.py']

# Check if a version.gen file is present.
# This would have been generated from the meson dist command.
fs = import('fs')
dist_version_file = meson.project_source_root() / 'version.gen'
if fs.is_file(dist_version_file)
    version_cmd += fs.read(dist_version_file)
endif

version_cpp = vcs_tag(command : version_cmd,
                      replace_string: '@VER@',
                      input : 'version.cpp.in',
                      output : 'version.cpp',
                      fallback : meson.project_version())

core_src += version_cpp

# Install symlinks to the old header directories and names for legacy purposes.
# install_symlink('libcamera-apps',
#                 install_dir: get_option('includedir'),
#                 pointing_to: 'rpicam-apps')

# inc_install_dir = get_option('includedir') / meson.project_name() / 'core'
# install_symlink('libcamera_app.h',
#                 install_dir: inc_install_dir,
#                 pointing_to: 'rpicam_app.hpp')

# install_symlink('libcamera_encoder.h',
#                 install_dir: inc_install_dir,
#                 pointing_to: 'rpicam_encoder.hpp')