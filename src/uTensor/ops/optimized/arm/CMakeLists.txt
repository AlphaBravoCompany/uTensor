#TODO Add support for other compilers HERE
#TODO Add device config bits, for super futre
add_subdirectory("${PROJECT_SOURCE_DIR}/extern/CMSIS_5/CMSIS/DSP/Source" "extern/cmsis_dsp")
#include("${PROJECT_SOURCE_DIR}/extern/CMSIS_5/CMSIS/DSP/config")
add_subdirectory("${PROJECT_SOURCE_DIR}/extern/CMSIS_5/CMSIS/NN/Source" "extern/cmsis_nn")
set(hdr_optimized_ops 
    FFT.hpp
   )
set(src_optimized_ops 
    FFT.cpp
   )
add_library(optimized_ops ${src_optimized_ops} ${hdr_optimized_ops})
target_link_libraries(optimized_ops utensor_core CMSISNN)
target_compile_features(optimized_ops PUBLIC cxx_std_11)
