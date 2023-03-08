if(MSVC)
    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} /bigobj")
endif()

COLMAP_ADD_STATIC_LIBRARY(flann
    flann.hpp flann.cpp
    ext/lz4.h ext/lz4.c
    ext/lz4hc.h ext/lz4hc.c
)

if(USE_AVX2)
	message("--> [xy] USE_AVX2 ${USE_AVX2}")
	#target_compile_definitions(flann PUBLIC FLANN_USE_AVX2=1)
	target_compile_definitions(flann PUBLIC -DFLANN_USE_AVX2)
endif()
