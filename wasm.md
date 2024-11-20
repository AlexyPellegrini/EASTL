To build:

```sh
emcmake ../EASTL-build-wasm -DCMAKE_CXX_FLAGS="-pthread -Wno-deprecated-literal-operator" -DCMAKE_EXE_LINKER_FLAGS="-sSTACK_SIZE=1048576 -sALLOW_MEMORY_GROWTH" -DEASTL_BUILD_TESTS=ON
```
Or
```sh
cmake -S EASTL -B EASTL-build-wasm -DCMAKE_TOOLCHAIN_FILE=.../emsdk/upstream/emscripten/cmake/Modules/Platform/Emscripten.cmake -DCMAKE_CROSSCOMPILING_EMULATOR=node -G Ninja -DCMAKE_CXX_FLAGS="-pthread -Wno-deprecated-literal-operator" -DCMAKE_EXE_LINKER_FLAGS="-sSTACK_SIZE=1048576 -sALLOW_MEMORY_GROWTH" -DEASTL_BUILD_TESTS=ON
```

Run tests:

```sh
node EASTL-build-wasm\test\EASTLTest.js
```

Known issues with bitset (probably an emscripten bug with some intrinsics on 64-bits integers)
