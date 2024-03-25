# Compiler Design article series - MathExpr toy language template

This is the template repository to start off leaning about compilers and implementing one yourself, without worrying about the setup stuff.

If you want to see, how the finished compiler for `MathExpr` looks like, check out the [main repo](https://github.com/marcauberer/compiler-design-series).

## Setup steps

1. Create repo from this template (Click the green `Use this template` button in the top right corner)
2. Clone it to your machine
3. Get yourself a C++ compiler, e.g. GCC or Clang (e.g. [winlibs.com](https://winlibs.com), not forget to add `bin` dir to system PATH variable)
4. Build LLVM (see below)
5. Set environment variable `LLVM_DIR` to `<llvm-build-dir>/lib/cmake/llvm`
6. Try running `./build.sh` (Linux) or `.\build.bat` (Windows)

## Build LLVM

### Prerequisites

- CMake
- C++ Compiler and Linker
- Generator, e.g. Ninja
- Optional: CCache (add this to the cmake command below: `-DCMAKE_C_COMPILER_LAUNCHER=ccache -DCMAKE_CXX_COMPILER_LAUNCHER=ccache`)

### Setup

Execute the following instructions in a directory, where you have a few spare gigabytes:

**Linux**
```bash
git clone --depth 1 --branch llvmorg-18.1.2 https://github.com/llvm/llvm-project llvm
mkdir ./llvm/build-release
cd ./llvm/build-release
cmake -DCMAKE_BUILD_TYPE=RelWithDebInfo -DCMAKE_C_COMPILER=gcc -DCMAKE_CXX_COMPILER=g++ -DCMAKE_CXX_FLAGS_RELWITHDEBINFO="-O2" -GNinja ../llvm
cmake --build .
```

**Windows**
```bash
git clone --depth 1 --branch llvmorg-18.1.2 https://github.com/llvm/llvm-project llvm
mkdir .\llvm\build-release
cd .\llvm\build-release
cmake -DCMAKE_BUILD_TYPE=RelWithDebInfo -DCMAKE_C_COMPILER=gcc -DCMAKE_CXX_COMPILER=g++ -DCMAKE_CXX_FLAGS_RELWITHDEBINFO="-O2" -GNinja ..\llvm
cmake --build .
```

© Marc Auberer 2023-2024