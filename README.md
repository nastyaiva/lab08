# lab02

~/nastyaiva/workspace ~/nastyaiva/workspace
```
```
source scripts/activate
```
```
git clone https://github.com/${GITHUB_USERNAME}/lab02.git projects/lab03

Клонирование в «projects/lab03»...
remote: Enumerating objects: 15, done.
remote: Counting objects: 100% (15/15), done.
remote: Compressing objects: 100% (9/9), done.
remote: Total 15 (delta 0), reused 12 (delta 0), pack-reused 0
Получение объектов: 100% (15/15), готово.

```
```
 cd projects/lab03
```
```
git remote remove origin
```
```
git remote add origin https://github.com/${GITHUB_USERNAME}/lab03.git
```
```
g++ -std=c++11 -I./include -c sources/print.cpp
```
```
ls print.o

print.o
```
```
nm print.o | grep print

00000000000000aa t _GLOBAL__sub_I__Z5printRKNSt7__cxx1112basic_stringIcSt11char_traitsIcESaIcEEERSo
0000000000000000 T _Z5printRKNSt7__cxx1112basic_stringIcSt11char_traitsIcESaIcEEERSo
000000000000002a T _Z5printRKNSt7__cxx1112basic_stringIcSt11char_traitsIcESaIcEEERSt14basic_ofstreamIcS2_E

```
```
ar rvs print.a print.o

ar: создаётся print.a
a - print.o
```
```
file print.a

print.a: current ar archive
```
```
g++ -std=c++11 -I./include -c examples/example1.cpp
```
```
ls example1.o

example1.o
```
```
g++ example1.o print.a -o example1
```
```
./example1 && echo

hello
```
```
g++ -std=c++11 -I./include -c examples/example2.cpp
```
```
nm example2.o

                 U __cxa_atexit
                 U __dso_handle
0000000000000000 V DW.ref.__gxx_personality_v0
                 U _GLOBAL_OFFSET_TABLE_
000000000000017e t _GLOBAL__sub_I_main
                 U __gxx_personality_v0
0000000000000000 T main
                 U __stack_chk_fail
                 U _Unwind_Resume
0000000000000128 t _Z41__static_initialization_and_destruction_0ii
                 U _Z5printRKNSt7__cxx1112basic_stringIcSt11char_traitsIcESaIcEEERSt14basic_ofstreamIcS2_E
                 U _ZNSaIcEC1Ev
                 U _ZNSaIcED1Ev
                 U _ZNSt14basic_ofstreamIcSt11char_traitsIcEEC1EPKcSt13_Ios_Openmode
                 U _ZNSt14basic_ofstreamIcSt11char_traitsIcEED1Ev
                 U _ZNSt7__cxx1112basic_stringIcSt11char_traitsIcESaIcEEC1EPKcRKS3_
                 U _ZNSt7__cxx1112basic_stringIcSt11char_traitsIcESaIcEED1Ev
                 U _ZNSt8ios_base4InitC1Ev
                 U _ZNSt8ios_base4InitD1Ev
0000000000000000 r _ZStL19piecewise_construct
0000000000000000 b _ZStL8__ioinit
```
```
g++ example2.o print.a -o example2
```
```
./example2
```
```
cat log.txt && echo

hello
```
```
rm -rf example1.o example2.o print.o
```
```
rm -rf print.a
```
```
rm -rf example1 example2
```
```
rm -rf log.txt
```
```
cat > CMakeLists.txt <<EOF
> cmake_minimum_required(VERSION 3.4)
> project(print)
> EOF
```
```
cat >> CMakeLists.txt <<EOF
> set(CMAKE_CXX_STANDARD 11)
> set(CMAKE_CXX_STANDARD_REQUIRED ON)
> EOF
```
```
cat >> CMakeLists.txt <<EOF
> add_library(print STATIC \${CMAKE_CURRENT_SOURCE_DIR}/sources/print.cpp)
> EOF
```
```
cat >> CMakeLists.txt <<EOF
> include_directories(\${CMAKE_CURRENT_SOURCE_DIR}/include)
> EOF
```
```
cmake -H. -B_build
-- The C compiler identification is GNU 11.4.0
-- The CXX compiler identification is GNU 11.4.0
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Check for working C compiler: /usr/bin/cc - skipped
-- Detecting C compile features
-- Detecting C compile features - done
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- Check for working CXX compiler: /usr/bin/c++ - skipped
-- Detecting CXX compile features
-- Detecting CXX compile features - done
-- Configuring done
-- Generating done
-- Build files have been written to: /home/nastya/nastyaiva/workspace/projects/lab03/_build
```
```
cmake --build _build
[ 50%] Building CXX object CMakeFiles/print.dir/sources/print.cpp.o
[100%] Linking CXX static library libprint.a
[100%] Built target print
```
```
cat >> CMakeLists.txt <<EOF

> add_executable(example1 \${CMAKE_CURRENT_SOURCE_DIR}/examples/example1.cpp)
> add_executable(example2 \${CMAKE_CURRENT_SOURCE_DIR}/examples/example2.cpp)
> EOF
```
```
cat >> CMakeLists.txt <<EOF

> target_link_libraries(example1 print)
> target_link_libraries(example2 print)
> EOF
```
```
cmake --build _build

-- Configuring done
-- Generating done
-- Build files have been written to: /home/nastya/nastyaiva/workspace/projects/lab03/_build
Consolidate compiler generated dependencies of target print
[ 33%] Built target print
[ 50%] Building CXX object CMakeFiles/example1.dir/examples/example1.cpp.o
[ 66%] Linking CXX executable example1
[ 66%] Built target example1
[ 83%] Building CXX object CMakeFiles/example2.dir/examples/example2.cpp.o
[100%] Linking CXX executable example2
[100%] Built target example2
```
```
cmake --build _build --target print

[100%] Built target print
```
```
cmake --build _build --target example1

[ 50%] Built target print
Consolidate compiler generated dependencies of target example1
[100%] Built target example1
```
```
cmake --build _build --target example2

[ 50%] Built target print
Consolidate compiler generated dependencies of target example2
[100%] Built target example2
```
```
ls -la _build/libprint.a

-rw-rw-r-- 1 nastya nastya 3126 апр 28 16:42 _build/libprint.a
```
```
_build/example1 && echo

hello
```
```
_build/example2
```
```
cat log.txt && echo

hello
```
```
rm -rf log.txt
```
```
git clone https://github.com/tp-labs/lab03 tmp

Клонирование в «tmp»...
remote: Enumerating objects: 91, done.
remote: Counting objects: 100% (30/30), done.
remote: Compressing objects: 100% (9/9), done.
remote: Total 91 (delta 23), reused 21 (delta 21), pack-reused 61
Получение объектов: 100% (91/91), 1.02 МиБ | 2.65 МиБ/с, готово.
Определение изменений: 100% (41/41), готово.

```
```
mv -f tmp/CMakeLists.txt .
```
```
rm -rf tmp
```
```
cat CMakeLists.txt

cmake_minimum_required(VERSION 3.4)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

option(BUILD_EXAMPLES "Build examples" OFF)

project(print)

add_library(print STATIC ${CMAKE_CURRENT_SOURCE_DIR}/sources/print.cpp)

target_include_directories(print PUBLIC
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
  $<INSTALL_INTERFACE:include>
)

if(BUILD_EXAMPLES)
  file(GLOB EXAMPLE_SOURCES "${CMAKE_CURRENT_SOURCE_DIR}/examples/*.cpp")
  foreach(EXAMPLE_SOURCE ${EXAMPLE_SOURCES})
    get_filename_component(EXAMPLE_NAME ${EXAMPLE_SOURCE} NAME_WE)
    add_executable(${EXAMPLE_NAME} ${EXAMPLE_SOURCE})
    target_link_libraries(${EXAMPLE_NAME} print)
    install(TARGETS ${EXAMPLE_NAME}
      RUNTIME DESTINATION bin
    )
  endforeach(EXAMPLE_SOURCE ${EXAMPLE_SOURCES})
endif()

install(TARGETS print
    EXPORT print-config
    ARCHIVE DESTINATION lib
    LIBRARY DESTINATION lib
)

install(DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/include/ DESTINATION include)
install(EXPORT print-config DESTINATION cmake)
```
```
cmake -H. -B_build -DCMAKE_INSTALL_PREFIX=_install

-- Configuring done
-- Generating done
-- Build files have been written to: /home/nastya/nastyaiva/workspace/projects/lab03/_build
```
```
make --build _build --target install

Consolidate compiler generated dependencies of target print
[100%] Built target print
Install the project...
-- Install configuration: ""
-- Installing: /home/nastya/nastyaiva/workspace/projects/lab03/_install/lib/libprint.a
-- Installing: /home/nastya/nastyaiva/workspace/projects/lab03/_install/include
-- Installing: /home/nastya/nastyaiva/workspace/projects/lab03/_install/include/print.hpp
-- Installing: /home/nastya/nastyaiva/workspace/projects/lab03/_install/cmake/print-config.cmake
-- Installing: /home/nastya/nastyaiva/workspace/projects/lab03/_install/cmake/print-config-noconfig.cmake

```
```
tree _install

_install
├── cmake
│   ├── print-config.cmake
│   └── print-config-noconfig.cmake
├── include
│   └── print.hpp
└── lib
    └── libprint.a

3 directories, 4 files
```
```
git add CMakeLists.txt
```
```
git commit -m"added CMakeLists.txt"

[main bd5e0e1] added CMakeLists.txt
 1 file changed, 36 insertions(+)
 create mode 100644 CMakeLists.txt
```
```
git push --set-upstream origin main

Перечисление объектов: 6, готово.
Подсчет объектов: 100% (6/6), готово.
При сжатии изменений используется до 8 потоков
Сжатие объектов: 100% (4/4), готово.
Запись объектов: 100% (6/6), 1.57 КиБ | 1.57 МиБ/с, готово.
Всего 6 (изменений 0), повторно использовано 3 (изменений 0), повторно использовано пакетов 0
To github.com:nastyaiva/lab03.git
 * [new branch]      main -> main
Ветка «main» отслеживает внешнюю ветку «main» из «origin».
```
