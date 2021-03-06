cmake_minimum_required (VERSION 2.8)
PROJECT (HDF5_HL_CPP_EXAMPLES)

#-----------------------------------------------------------------------------
# Setup include Directories
#-----------------------------------------------------------------------------
INCLUDE_DIRECTORIES (${HDF5_HL_SRC_DIR}/src)
INCLUDE_DIRECTORIES (${HDF5_HL_CPP_SRC_DIR}/src)

# --------------------------------------------------------------------
#  Add in the examples for the Packet Table codes
# --------------------------------------------------------------------
IF (HDF5_BUILD_EXAMPLES)
  ADD_EXECUTABLE (ptExampleFL ${HDF5_HL_CPP_EXAMPLES_SOURCE_DIR}/ptExampleFL.cpp)
  H5_NAMING (ptExampleFL)
  TARGET_WIN_PROPERTIES (ptExampleFL)
  TARGET_LINK_LIBRARIES (
      ptExampleFL
      ${HDF5_HL_CPP_LIB_TARGET}
      ${HDF5_HL_LIB_TARGET}
      ${HDF5_LIB_TARGET}
  )

  ADD_TEST (NAME cpp_hl_ex_ptExampleFL COMMAND $<TARGET_FILE:ptExampleFL>)

  ADD_EXECUTABLE (ptExampleVL ${HDF5_HL_CPP_EXAMPLES_SOURCE_DIR}/ptExampleVL.cpp)
  H5_NAMING (ptExampleVL)
  TARGET_WIN_PROPERTIES (ptExampleVL)
  TARGET_LINK_LIBRARIES (
      ptExampleVL
      ${HDF5_HL_CPP_LIB_TARGET}
      ${HDF5_HL_LIB_TARGET}
      ${HDF5_LIB_TARGET}
  )

  ADD_TEST (NAME cpp_hl_ex_ptExampleVL COMMAND $<TARGET_FILE:ptExampleVL>)

ENDIF (HDF5_BUILD_EXAMPLES)
