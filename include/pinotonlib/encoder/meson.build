encoder_headers = files([
    'encoder.hpp',
    'h264_encoder.hpp',
    'mjpeg_encoder.hpp',
    'null_encoder.hpp',
])

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
        encoder_headers += files('libav_encoder.hpp')
        cpp_arguments += '-DLIBAV_PRESENT=1'
endif

install_headers(encoder_headers, subdir: meson.project_name() / 'encoder')
