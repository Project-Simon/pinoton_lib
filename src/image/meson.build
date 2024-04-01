image_src = files([
    'bmp.cpp',
    'dng.cpp',
    'jpeg.cpp',
    'png.cpp',
    'yuv.cpp',
])

exif_dep = dependency('libexif', required : true)
jpeg_dep = dependency('libjpeg', required : true)
tiff_dep = dependency('libtiff-4', required : true)
png_dep = dependency('libpng', required : true)

image_dep = [exif_dep, jpeg_dep, tiff_dep, png_dep]