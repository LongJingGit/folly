## folly 源码阅读笔记

### 编译

```sh
mkdir _build
cd _build
cmake ..
make -j2
```

如果要编译 test case, 则需要手动修改 CMakeLists.txt 文件，或者在命令行指定 BUILD_TESTS

```sh
option(BUILD_TESTS "If enabled, compile the tests." OFF)
```

需要注意的是，编译 test case 时有些 case 会编译失败，可以先将这些编译失败的 case 从 CMakeLists.txt 中注释掉:

```sh
# DIRECTORY detail/base64_detail/tests/
#   TEST base64_detail_test
#   SOURCES
#     Base64AgainstScalarTest.cpp
#     Base64PlatformTest.cpp
#     Base64SpecialCasesTest.cpp

# TEST autotimer_test SOURCES AutoTimerTest.cpp

# BENCHMARK lang_to_ascii_benchmark SOURCES ToAsciiBench.cpp

# TEST base64_test SOURCES base64_test.cpp

# TEST fbstring_test WINDOWS_DISABLED SOURCES FBStringTest.cpp

# TEST fixed_string_test SOURCES FixedStringTest.cpp
```

