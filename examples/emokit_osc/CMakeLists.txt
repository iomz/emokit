LIST(APPEND CMAKE_MODULE_PATH ${CMAKE_CURRENT_SOURCE_DIR})
FIND_PACKAGE(oscpack)

IF(NOT oscpack_FOUND)
  MESSAGE(STATUS "oscpack not found, not building emokit osc server")
ELSE()
  INCLUDE_DIRECTORIES(${oscpack_INCLUDE_DIR})
  ADD_EXECUTABLE(emokit_osc emokit_osc.cpp)
  ADD_DEPENDENCIES(emokit_osc emokit)
  TARGET_LINK_LIBRARIES(emokit_osc ${oscpack_LIBS} emokit ${LIBS})
ENDIF()
