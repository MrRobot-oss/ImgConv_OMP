cmake_minimum_required(VERSION 3.0)

project(imgconv_omp LANGUAGES C)
 
add_executable(imgconv_omp main.c)

find_package(OpenMP)
if (OPENMP_FOUND)
    set (CMAKE_C_FLAGS "${CMAKE_C_FLAGS} ${OpenMP_C_FLAGS}")
    set (CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} ${OpenMP_CXX_FLAGS}")
    set (CMAKE_EXE_LINKER_FLAGS "${CMAKE_EXE_LINKER_FLAGS} ${OpenMP_EXE_LINKER_FLAGS}")
endif()

target_link_libraries(imgconv_omp m)

install(TARGETS imgconv_omp RUNTIME DESTINATION bin)
