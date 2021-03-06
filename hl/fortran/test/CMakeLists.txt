cmake_minimum_required (VERSION 2.8)
PROJECT (HDF5_HL_FORTRAN_TESTS C CXX Fortran)

#-----------------------------------------------------------------------------
# Add Tests
#-----------------------------------------------------------------------------
INCLUDE_DIRECTORIES (${CMAKE_Fortran_MODULE_DIRECTORY} ${HDF5_F90_BINARY_DIR} ${HDF5_F90_SRC_DIR}/src)
LINK_DIRECTORIES (
    ${CMAKE_Fortran_MODULE_DIRECTORY}
    ${HDF5_HL_F90_BINARY_DIR}
    ${HDF5_F90_BINARY_DIR}
    ${CMAKE_LIBRARY_OUTPUT_DIRECTORY}
)

#-- Adding test for hl_f90_tstlite
ADD_EXECUTABLE (hl_f90_tstlite tstlite.f90)
H5_NAMING (hl_f90_tstlite)
TARGET_FORTRAN_WIN_PROPERTIES (hl_f90_tstlite)
TARGET_LINK_LIBRARIES (hl_f90_tstlite ${HDF5_HL_F90_LIB_TARGET} ${HDF5_F90_LIB_TARGET})
SET_TARGET_PROPERTIES (hl_f90_tstlite PROPERTIES LINKER_LANGUAGE Fortran)

ADD_TEST (NAME hl_f90_tstlite COMMAND $<TARGET_FILE:hl_f90_tstlite>)

#-- Adding test for hl_f90_tstimage
ADD_EXECUTABLE (hl_f90_tstimage tstimage.f90)
H5_NAMING (hl_f90_tstimage)
TARGET_FORTRAN_WIN_PROPERTIES (hl_f90_tstimage)
TARGET_LINK_LIBRARIES (hl_f90_tstimage  ${HDF5_HL_F90_LIB_TARGET} ${HDF5_F90_LIB_TARGET})
SET_TARGET_PROPERTIES (hl_f90_tstimage PROPERTIES LINKER_LANGUAGE Fortran)

ADD_TEST (NAME hl_f90_tstimage COMMAND $<TARGET_FILE:hl_f90_tstimage>)

#-- Adding test for hl_f90_tsttable
ADD_EXECUTABLE (hl_f90_tsttable tsttable.f90)
H5_NAMING (hl_f90_tsttable)
TARGET_FORTRAN_WIN_PROPERTIES (hl_f90_tsttable)
TARGET_LINK_LIBRARIES (hl_f90_tsttable ${HDF5_HL_F90_LIB_TARGET} ${HDF5_F90_LIB_TARGET})
SET_TARGET_PROPERTIES (hl_f90_tsttable PROPERTIES LINKER_LANGUAGE Fortran)

ADD_TEST (NAME hl_f90_tsttable COMMAND $<TARGET_FILE:hl_f90_tsttable>)
