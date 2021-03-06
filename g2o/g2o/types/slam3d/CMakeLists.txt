ADD_LIBRARY(${LIB_PREFIX}types_slam3d ${G2O_LIB_TYPE}
  dquat2mat.cpp dquat2mat.h
  isometry3d_mappings.h
  isometry3d_mappings.cpp
  isometry3d_gradients.cpp
  isometry3d_gradients.h
  vertex_se3.cpp
  vertex_se3.h
  parameter_se3_offset.cpp
  parameter_se3_offset.h
  edge_se3.cpp
  edge_se3.h
  edge_se3_offset.cpp
  edge_se3_offset.h
  vertex_pointxyz.cpp
  vertex_pointxyz.h
  parameter_camera.cpp
  parameter_camera.h
  parameter_stereo_camera.cpp
  parameter_stereo_camera.h
  edge_se3_pointxyz.cpp
  edge_se3_pointxyz.h
  edge_se3_pointxyz_disparity.cpp
  edge_se3_pointxyz_disparity.h
  edge_se3_pointxyz_depth.cpp
  edge_se3_pointxyz_depth.h
  edge_se3_prior.cpp
  edge_se3_prior.h
  se3quat.h
  se3_ops.h se3_ops.hpp
  types_slam3d.cpp
  types_slam3d.h
)

TARGET_LINK_LIBRARIES(${LIB_PREFIX}types_slam3d ${LIB_PREFIX}core)
IF(OPENGL_FOUND)
  TARGET_LINK_LIBRARIES(${LIB_PREFIX}types_slam3d ${OPENGL_gl_LIBRARY})
ENDIF()

INSTALL(TARGETS ${LIB_PREFIX}types_slam3d
  RUNTIME DESTINATION ${CMAKE_INSTALL_PREFIX}/bin
  LIBRARY DESTINATION ${CMAKE_INSTALL_PREFIX}/lib
  ARCHIVE DESTINATION ${CMAKE_INSTALL_PREFIX}/lib
)

FILE(GLOB headers "${CMAKE_CURRENT_SOURCE_DIR}/*.h" "${CMAKE_CURRENT_SOURCE_DIR}/*.hpp")
INSTALL(FILES ${headers} DESTINATION ${CMAKE_INSTALL_PREFIX}/include/g2o/types/slam3d)
