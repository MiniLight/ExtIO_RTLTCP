project(ExtIO_RTLUDP)
cmake_minimum_required(VERSION 2.8)

aux_source_directory(. SRC_LIST)

if (WIN32)
    ENABLE_LANGUAGE(RC)
    set(SRC_LIST resource.rc ${SRC_LIST})
endif()

set(BUILD_SHARED_LIBS ON)
set(CMAKE_SHARED_LINKER_FLAGS "${CMAKE_SHARED_LINKER_FLAGS} -Wl,--kill-at -static-libgcc")

add_library(${PROJECT_NAME} ${SRC_LIST})
SET_TARGET_PROPERTIES(${PROJECT_NAME} PROPERTIES PREFIX "")
if(WIN32)
  target_link_libraries(${PROJECT_NAME} ws2_32)
endif()
