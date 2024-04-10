output_src = files([
    'circular_output.cpp',
    'file_output.cpp',
    'net_output.cpp',
    'output.cpp',
])

output_headers = [
    meson.project_source_root() / 'include/pinotonlib/output/circular_output.hpp',
    meson.project_source_root() / 'include/pinotonlib/output/file_output.hpp',
    meson.project_source_root() / 'include/pinotonlib/output/net_output.hpp',
    meson.project_source_root() / 'include/pinotonlib/output/output.hpp',
]

output_dep = [exif_dep, jpeg_dep, tiff_dep, png_dep]

install_headers(files(output_headers), subdir: meson.project_name() / 'output')
