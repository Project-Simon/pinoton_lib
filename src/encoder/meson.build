encoder_src = files([
    'encoder.cpp',
    'h264_encoder.cpp',
    'mjpeg_encoder.cpp',
    'null_encoder.cpp',
])

encoder_headers = files([
    meson.project_source_root() / 'include/pinotonlib/encoder/encoder.hpp',
    meson.project_source_root() / 'include/pinotonlib/encoder/h264_encoder.hpp',
    meson.project_source_root() / 'include/pinotonlib/encoder/mjpeg_encoder.hpp',
    meson.project_source_root() / 'include/pinotonlib/encoder/null_encoder.hpp',
])

encoder_dep = []

enable_libav = get_option('enable_libav')
libav_dep_names = ['libavcodec', 'libavdevice', 'libavformat', 'libavutil', 'libswresample']
libav_deps = []

if enable_libav
    foreach name : libav_dep_names
        dep = dependency(name, required : false)
        if not dep.found()
            enable_libav = false
            break
        endif
        libav_deps += dep
    endforeach
endif

if enable_libav
        encoder_src += files('libav_encoder.cpp')
        encoder_headers += files(meson.project_source_root() / 'include/pinotonlib/encoder/libav_encoder.hpp')
        encoder_dep += libav_deps
        cpp_arguments += '-DLIBAV_PRESENT=1'
endif

install_headers(encoder_headers, subdir: meson.project_name() / 'encoder')
