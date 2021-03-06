cmake_minimum_required (VERSION 2.8)
PROJECT (HDF5_TOOLS_H5JAM)

#-----------------------------------------------------------------------------
# Setup include Directories
#-----------------------------------------------------------------------------
INCLUDE_DIRECTORIES (${HDF5_TOOLS_SRC_DIR}/lib)
INCLUDE_DIRECTORIES (${HDF5_PROJECT_DIR}/test)

# --------------------------------------------------------------------
# Add the h5jam executables
# --------------------------------------------------------------------
ADD_EXECUTABLE (h5jam ${HDF5_TOOLS_H5JAM_SOURCE_DIR}/h5jam.c)
H5_NAMING (h5jam)
TARGET_WIN_PROPERTIES (h5jam)
TARGET_LINK_LIBRARIES (h5jam  ${HDF5_TOOLS_LIB_TARGET} ${HDF5_LIB_TARGET})

ADD_EXECUTABLE (getub ${HDF5_TOOLS_H5JAM_SOURCE_DIR}/getub.c)
H5_NAMING (getub)
TARGET_WIN_PROPERTIES (getub)
TARGET_LINK_LIBRARIES (getub  ${HDF5_TOOLS_LIB_TARGET} ${HDF5_LIB_TARGET})

ADD_EXECUTABLE (tellub ${HDF5_TOOLS_H5JAM_SOURCE_DIR}/tellub.c)
H5_NAMING (tellub)
TARGET_WIN_PROPERTIES (tellub)
TARGET_LINK_LIBRARIES (tellub  ${HDF5_TOOLS_LIB_TARGET} ${HDF5_LIB_TARGET})

ADD_EXECUTABLE (h5unjam ${HDF5_TOOLS_H5JAM_SOURCE_DIR}/h5unjam.c)
H5_NAMING (h5unjam)
TARGET_WIN_PROPERTIES (h5unjam)
TARGET_LINK_LIBRARIES (h5unjam  ${HDF5_TOOLS_LIB_TARGET} ${HDF5_LIB_TARGET})

SET (H5_DEP_EXECUTABLES
    h5jam
    getub
    tellub
    h5unjam
)

##############################################################################
##############################################################################
###           T E S T I N G                                                ###
##############################################################################
##############################################################################

IF (BUILD_TESTING)
  # --------------------------------------------------------------------
  # Add the h5jam test executables
  # --------------------------------------------------------------------
  IF (HDF5_BUILD_GENERATORS AND NOT BUILD_SHARED_LIBS)
    ADD_EXECUTABLE (h5jamgentest ${HDF5_TOOLS_H5JAM_SOURCE_DIR}/h5jamgentest.c)
    H5_NAMING (h5jamgentest)
    TARGET_WIN_PROPERTIES (h5jamgentest)
    TARGET_LINK_LIBRARIES (h5jamgentest ${HDF5_LIB_TARGET} ${HDF5_TOOLS_LIB_TARGET})
    
    #ADD_TEST (NAME h5jamgentest COMMAND $<TARGET_FILE:h5jamgentest>)
  ENDIF (HDF5_BUILD_GENERATORS AND NOT BUILD_SHARED_LIBS)
  
##############################################################################
##############################################################################
###           T H E   T E S T S  M A C R O S                               ###
##############################################################################
##############################################################################

##############################################################################
##############################################################################
###           T H E   T E S T S                                            ###
##############################################################################
##############################################################################

ENDIF (BUILD_TESTING)

##############################################################################
##############################################################################
###           I N S T A L L A T I O N                                      ###
##############################################################################
##############################################################################

#-----------------------------------------------------------------------------
# Rules for Installation of tools using make Install target
#-----------------------------------------------------------------------------
INSTALL (
    TARGETS
        h5jam h5unjam
    RUNTIME DESTINATION
        ${HDF5_INSTALL_BIN_DIR}/tools
    COMPONENT
        toolsapplications
)
