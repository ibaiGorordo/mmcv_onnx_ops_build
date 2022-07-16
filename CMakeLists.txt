cmake_minimum_required(VERSION 3.20)
project(build_mmcv_onnx_ops)

set(CMAKE_CXX_STANDARD 14)
set(LIB_NAME mmcv_onnx_ops)

set(ONNXRUNTIME_DIR ${PROJECT_SOURCE_DIR}/third-party/onnxruntime)
set(ONNXRUNTIME_INCLUDE_DIR ${ONNXRUNTIME_DIR}/include/onnxruntime/core/session/)
set(MMCV_ONNXRUNTIME_SRC_DIR ${PROJECT_SOURCE_DIR}/third-party/mmcv/mmcv/ops/csrc/onnxruntime/)

add_library(onnxruntime-lib SHARED IMPORTED )
if(WIN32)
    set_target_properties(onnxruntime-lib PROPERTIES IMPORTED_LOCATION "${PROJECT_SOURCE_DIR}/libs/onnxruntime/onnxruntime.dll")
    set_target_properties(onnxruntime-lib PROPERTIES IMPORTED_IMPLIB "${PROJECT_SOURCE_DIR}/libs/onnxruntime/onnxruntime.lib")
else()
    set_target_properties(onnxruntime-lib PROPERTIES IMPORTED_LOCATION "${PROJECT_SOURCE_DIR}/libs/onnxruntime/libonnxruntime.so")
endif()


file(GLOB MMCV_SRC "${MMCV_ONNXRUNTIME_SRC_DIR}/cpu/*.cpp")
add_library(${LIB_NAME} SHARED
          ${MMCV_SRC})

target_include_directories(${LIB_NAME} PUBLIC
        ${MMCV_ONNXRUNTIME_SRC_DIR}
        ${ONNXRUNTIME_INCLUDE_DIR})

target_link_libraries(${LIB_NAME}
                    onnxruntime-lib)

