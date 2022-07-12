# This is the CMake file for the src directory of IO-meter.
#
# Ed Hartnett, 4/5/22

add_executable(tst_compress_par tst_compress_par.c nc_tests.h err_macros.h)
target_include_directories(tst_compress_par PUBLIC ${CMAKE_SOURCE_DIR/src} . PUBLIC ${HDF5_C_INCLUDE_DIRS} PUBLIC ${NetCDF_INCLUDE_DIRS})
target_link_libraries(tst_compress_par NetCDF::NetCDF_C ${HAVE_LIBM})


