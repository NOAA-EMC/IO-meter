# This is the cmake build file for the tests directory of the
# IO-meter project.
#
# Ed Hartnett, 7/12/22

# Include cmake to allow parallel I/O tests.
include (LibMPI)

include_directories(${PROJECT_SOURCE_DIR})

# Cause test to be run with MPI.
add_mpi_test(test1 EXECUTABLE ${CMAKE_BINARY_DIR}/src/tst_compress_par NUMPROCS 4 TIMEOUT 60)
