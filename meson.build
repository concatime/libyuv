project('libyuv', 'cpp',
  license : 'BSD-3-Clause',
  version : '0.1.0',
  # override_options not yet supported by muon
  default_options : ['cpp_std=c++11']
)

subdir('include')
subdir('source')

libyuv = library('yuv', source,
  include_directories : include,
  version : meson.project_version(),
  install : true)

libyuv_dep = declare_dependency(
  link_with : libyuv,
  include_directories : include,
)

foreach k, v : headers
  install_headers(v, subdir : k)
endforeach

pkg = import('pkgconfig')
pkg.generate(libyuv,
  name : 'libyuv',
  description : 'YUV scaling and conversion library')

executable('yuvconvert', files('util/yuvconvert.cc'),
  include_directories : [include],
  link_with : [libyuv],
  install : true)
