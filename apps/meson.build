pinoton_still = executable('pinoton-still', files('pinoton_still.cpp'),
                          include_directories : include_directory,
                          dependencies: [libcamera_dep, boost_dep],
                          link_with : pinotonlib,
                          install : false)

pinoton_vid = executable('pinoton-vid', files('pinoton_vid.cpp'),
                        include_directories : include_directory,
                        dependencies: [libcamera_dep, boost_dep],
                        link_with : pinotonlib,
                        install : false)

pinoton_hello = executable('pinoton-hello', files('pinoton_hello.cpp'),
                          include_directories : include_directory,
                          dependencies: libcamera_dep,
                          link_with : pinotonlib,
                          install : false)

pinoton_raw = executable('pinoton-raw', files('pinoton_raw.cpp'),
                        include_directories : include_directory,
                        dependencies: [libcamera_dep, boost_dep],
                        link_with : pinotonlib,
                        install : false)

pinoton_jpeg = executable('pinoton-jpeg', files('pinoton_jpeg.cpp'),
                         include_directories : include_directory,
                         dependencies: [libcamera_dep, boost_dep],
                         link_with : pinotonlib,
                         install : false)

if enable_tflite
    pinoton_detect = executable('pinoton-detect', files('pinoton_detect.cpp'),
                               include_directories : include_directory,
                               dependencies: [libcamera_dep, boost_dep],
                               link_with : pinotonlib,
                               install : false)
endif