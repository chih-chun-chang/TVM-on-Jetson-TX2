# TVM Install from Source
This is my building steps of TVM and I'll provide my .bashrc and config.cmake for those who needs.

* Download Pre-built LLVM from [the website](http://releases.llvm.org/download.html) (AArch64 Linux (.sig))

1. Git clone the project </br>
`git clone --recursive https://github.com/apache/incubator-tvm`
2. Install dependencies </br>
`sudo apt-get update`
`sudo apt-get install -y python3 python3-dev python3-setuptools gcc libtinfo-dev zlib1g-dev build-essential cmake libedit-dev libxml2-dev`
3. Prepare to build tvm </br>
`cd tvm && mkdir build`
`cp cmake/config.cmake build`
`vim build/config.cmake`
    * Change `set(USE_CUDA OFF)` to `set(USE_CUDA ON)` to enable CUDA backend 
    * Change `set(USE_LLVM OFF)` to `set(USE_LLVM /path/to/your/llvm/bin/llvm-config)` (notice: absolute PATH is preferable)
4. Build </br>
`cd build`
`cmake ..`
`make -j4`
5. Python packages installation </br>
`pip3 install --user numpy decorator attrs`
    * to use RPC Tracker </br>
    `pip3 install --user tornado`
    * to use auto-tuning module </br>
    `pip3 install --user tornado psutil xgboost`
    * to build tvm to compile a model </br>
    `sudo apt install antlr4` </br>
    `pip3 install --user mypy orderedset antlr4-python3-runtime`
6. Test Installation </br>
`python apps/benchmark/gpu_imagenet_bench.py --model tx2`