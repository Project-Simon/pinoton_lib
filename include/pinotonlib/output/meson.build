output_headers = [
    'circular_output.hpp',
    'file_output.hpp',
    'net_output.hpp',
    'output.hpp',
]

output_dep += [exif_dep, jpeg_dep, tiff_dep, png_dep]

install_headers(files(output_headers), subdir: meson.project_name() / 'output')
