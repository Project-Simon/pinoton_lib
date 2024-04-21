project('pinotonlib', 'c', 'cpp',
        meson_version : '>= 0.64.0',
        version : '1.4.4',
        default_options : [
            'werror=true',
            'warning_level=3',
            'cpp_std=c++17',
            'c_std=c11',
            'buildtype=release',
        ],
        license : 'BSD-2-Clause')

meson.add_dist_script('utils' / 'gen-dist.sh')

cpp_arguments = ['-pedantic', '-Wno-unused-parameter', '-faligned-new']

# Needed for file sizes > 32-bits.
cpp_arguments += '-D_FILE_OFFSET_BITS=64'

cxx = meson.get_compiler('cpp')
cpu = host_machine.cpu()
neon = get_option('neon_flags')

if cxx.get_id() == 'gcc'
    cpp_arguments += '-Wno-psabi'
endif

if cpu == 'aarch64' or neon == 'arm64'
    cpp_arguments += '-ftree-vectorize'
elif neon == 'armv8-neon'
    cpp_arguments += ['-mfpu=neon-fp-armv8', '-ftree-vectorize']
endif

libcamera_dep = dependency('libcamera', required : true)

summary({
            'location' : libcamera_dep.get_variable('libdir'),
            'version' : libcamera_dep.version()
        },
        section : 'libcamera')

include_directory = include_directories('include')
subdir('src')
subdir('utils')

pinotonlib_src = [core_src, encoder_src, image_src, output_src, preview_src, post_processing_stages_src]
pinotonlib_dep = [ core_dep, encoder_dep, image_dep, output_dep, preview_dep, post_processing_stages_dep, libcamera_dep]

add_project_arguments(cpp_arguments, language : 'cpp')

pinotonlib = library(
    'pinotonlib',
    pinotonlib_src,
    soversion : meson.project_version(),
    include_directories : include_directory,
    install : true,
    name_prefix : '',
    dependencies : pinotonlib_dep,
)

# Install a symlink to the old library name for legacy purposes.
install_symlink('libcamera_app.so',
                install_dir: get_option('libdir'),
                pointing_to: 'rpicam_app.so')

subdir('apps')

summary({
            'libav encoder' : enable_libav,
            'drm preview' : enable_drm,
            'egl preview' : enable_egl,
            'qt preview' : enable_qt,
            'OpenCV postprocessing' : enable_opencv,
            'TFLite postprocessing' : enable_tflite,
        },
        bool_yn : true, section : 'Build configuration')