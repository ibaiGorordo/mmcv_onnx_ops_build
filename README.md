# MMCV ONNX Custom Ops build (WIP)
 Repository for building the ONNX compatible ops in MMCV to run them in onnxruntime.

# Requirements
* A C/C++ compiler for your operating system (gcc on Linux, Visual Studio on Windows, CLang on Mac)
* [Cmake](https://cmake.org/)
* [Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)


# Installation
1. Download the appropriate ONNX Runtime library for your system from the **[Releases](https://github.com/microsoft/onnxruntime/releases)** and extract the contents of the **lib** folder into the **[libs/onnxruntime](https://github.com/ibaiGorordo/mmcv_onnx_ops_build/tree/main/libs/onnxruntime)** folder.

2. Clone repository with submodules (Note the **--recursive** part)
```
git clone https://github.com/ibaiGorordo/mmcv_onnx_ops_build.git --recursive
cd mmcv_onnx_ops_build
```

3. Compile the library
