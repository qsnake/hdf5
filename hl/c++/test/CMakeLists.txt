cmake_minimum_required (VERSION 2.8)
PROJECT (HDF5_HL_CPP_TEST)

#-----------------------------------------------------------------------------
# Setup include Directories
#-----------------------------------------------------------------------------
INCLUDE_DIRECTORIES (${HDF5_HL_SRC_DIR}/src)
INCLUDE_DIRECTORIES (${HDF5_HL_SRC_DIR}/c++/src)

# --------------------------------------------------------------------
# Add in the unit tests for the packet table c++ wrapper
# --------------------------------------------------------------------

IF (BUILD_TESTING)
  INCLUDE_DIRECTORIES (${HDF5_TEST_SRC_DIR})
  INCLUDE_DIRECTORIES (${HDF5_HL_SRC_DIR}/test)
  INCLUDE_DIRECTORIES (${HDF5_CPP_SRC_DIR}/src)

  ADD_EXECUTABLE (hl_ptableTest ${HDF5_HL_CPP_TEST_SOURCE_DIR}/ptableTest.cpp)
  H5_NAMING (hl_ptableTest)
  TARGET_WIN_PROPERTIES (hl_ptableTest)
  TARGET_LINK_LIBRARIES (
      hl_ptableTest
      ${HDF5_LIB_TARGET}
      ${HDF5_TEST_LIB_TARGET}
      ${HDF5_CPP_LIB_TARGET}
      ${HDF5_HL_LIB_TARGET}
      ${HDF5_HL_CPP_LIB_TARGET}
  )
  GET_TARGET_PROPERTY (hl_ptableTestpath hl_ptableTest LOCATION)
  GET_FILENAME_COMPONENT (hl_ptableTestexe ${hl_ptableTestpath} NAME)
  
  ADD_TEST (NAME hl_ptableTest COMMAND $<TARGET_FILE:hl_ptableTest>)
ENDIF (BUILD_TESTING)
