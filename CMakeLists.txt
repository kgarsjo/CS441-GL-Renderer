cmake_minimum_required(VERSION 2.8)

PROJECT(project2A)
SET(VTK_DIR /home/kgarsjo/dev/VTK5.10.1)

find_package(VTK REQUIRED)
include(${VTK_USE_FILE} ${VTK_DIR}/Rendering)

add_executable(project2A MACOSX_BUNDLE project2A)

find_package(OpenGL REQUIRED)
include_directories( ${OPENGL_INCLUDE_DIRS} )
target_link_libraries( project2A ${OPENGL_INCLUDE_DIRS})

if(VTK_LIBRARIES)
  target_link_libraries(project2A ${VTK_LIBRARIES})
else()
  target_link_libraries(project2A vtkHybrid)
endif()

