preview_src = files([
    'null_preview.cpp',
    'preview.cpp',
])
preview_dep = []

enable_drm = get_option('enable_drm')
drm_deps = dependency('libdrm', required : false)

if enable_drm and drm_deps.found()
    preview_dep += drm_deps
    preview_src += files('drm_preview.cpp')
    cpp_arguments += '-DLIBDRM_PRESENT=1'
else
    enable_drm = false
endif

enable_egl = get_option('enable_egl')
x11_deps = dependency('x11', required : false)
epoxy_deps = dependency('epoxy', required : false)

if enable_egl and x11_deps.found() and epoxy_deps.found()
    preview_dep += [x11_deps, epoxy_deps]
    preview_src += files('egl_preview.cpp')
    cpp_arguments += '-DLIBEGL_PRESENT=1'
else
    enable_egl = false
endif

enable_qt = get_option('enable_qt')
qt_dep = dependency('qt5', modules : ['Core', 'Widgets'], required : false)

if enable_qt and qt_dep.found()
    preview_dep += qt_dep
    preview_src += files('qt_preview.cpp')
    cpp_arguments += '-DQT_PRESENT=1'
else
    enable_qt = false
endif