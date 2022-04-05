# This is the CMake file for the src directory of IO-meter.
#
# Ed Hartnett, 4/5/22

add_executable(tst_compress_par tst_compress_par.c)
target_include_directories(tst_compress_par INTERFACE NetCDF_INCLUDE_DIRS)
target_link_libraries(tst_compress_par NetCDF::NetCDF_C)


