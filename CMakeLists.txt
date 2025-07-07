cmake_minimum_required(VERSION 3.14)
project(fastp VERSION 1.0 LANGUAGES C CXX)

# Pick a C++ standard
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)
option(BUILD_TESTING "Enable test building" OFF)

option(HWY_ENABLE_RUNTIME_DISPATCH
       "Enable runtime detection of best SIMD implementation in Highway"
       ON)

set(HWY_TARGETS
    "sse4;avx2;avx512f"
    CACHE STRING
    "List of Highway instruction-set targets to compile (e.g. sse4;avx2;avx512f;neon)")

mark_as_advanced(HWY_ENABLE_RUNTIME_DISPATCH HWY_TARGETS)

### Third‐party libraries ###
add_subdirectory(lib/libdeflate)
add_subdirectory(lib/libisal)
add_subdirectory(lib/libhwy)

add_subdirectory(src)
 
