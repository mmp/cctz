
cmake_minimum_required (VERSION 3.0)

project(cctz)

set(cctz_src
    src/civil_time_detail.cc
    src/time_tool.cc
    src/time_zone_fixed.cc
    src/time_zone_format.cc
    src/time_zone_if.cc
    src/time_zone_impl.cc
    src/time_zone_info.cc
    src/time_zone_libc.cc
    src/time_zone_lookup.cc
    src/time_zone_posix.cc
)

set (cctz_headers
    include/cctz/civil_time.h
    include/cctz/civil_time_detail.h
    include/cctz/time_zone.h
    include/cctz/zone_info_source.h
)

add_library(cctz
    ${cctz_src}
    ${cctz_headers}
)

include_directories(include)

set(CCTZ_INCLUDE_DIRS ${CMAKE_CURRENT_SOURCE_DIR}/include)

target_compile_features (cctz PRIVATE
  # Want to be able to do "using foo = bar;". There doesn't seem to
  # be a good feature for that.
  cxx_auto_type
)
