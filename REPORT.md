```
export GITHUB_USERNAME=nastyaiva
```
```
alias gsed=sed
```
```
cd ${GITHUB_USERNAME}/workspace
```
```
pushd .

~/nastyaiva/workspace ~/nastyaiva/workspace ~/nastyaiva/workspace
```
```
source scripts/activate
```
```
git clone https://github.com/${GITHUB_USERNAME}/lab06 projects/lab07

Клонирование в «projects/lab07»...
remote: Enumerating objects: 70, done.
remote: Counting objects: 100% (70/70), done.
remote: Compressing objects: 100% (35/35), done.
remote: Total 70 (delta 24), reused 70 (delta 24), pack-reused 0
Получение объектов: 100% (70/70), 11.15 КиБ | 278.00 КиБ/с, готово.
Определение изменений: 100% (24/24), готово.
```
```
cd projects/lab07
```
```
git remote remove origin
```
```
git remote add origin https://github.com/${GITHUB_USERNAME}/lab07
```
```
mkdir -p cmake
```
```
wget https://raw.githubusercontent.com/cpp-pm/gate/master/cmake/HunterGate.cmake -O cmake/HunterGate.cmake

--2024-05-03 15:50:00--  https://raw.githubusercontent.com/cpp-pm/gate/master/cmake/HunterGate.cmake
Распознаётся raw.githubusercontent.com (raw.githubusercontent.com)… 185.199.111.133, 185.199.108.133, 185.199.109.133, ...
Подключение к raw.githubusercontent.com (raw.githubusercontent.com)|185.199.111.133|:443... соединение установлено.
HTTP-запрос отправлен. Ожидание ответа… 200 OK
Длина: 17227 (17K) [text/plain]
Сохранение в: ‘cmake/HunterGate.cmake’

cmake/HunterGate.cmake                                          100%[=====================================================================================================================================================>]  16,82K  --.-KB/s    за 0s      

2024-05-03 15:50:02 (42,0 MB/s) - ‘cmake/HunterGate.cmake’ сохранён [17227/17227]
```
```
gsed -i '/cmake_minimum_required(VERSION 3.4)/a\

include("cmake/HunterGate.cmake")
HunterGate(
 URL "https://github.com/cpp-pm/hunter/archive/v0.23.251.tar.gz"
 SHA1 "5659b15dc0884d4b03dbd95710e6a1fa0fc3258d"
)
' CMakeLists.txt
```
```
git rm -rf third-party/gtest

rm 'third-party/gtest'
```
```
gsed -i '/set(PRINT_VERSION_STRING "v\${PRINT_VERSION}")/a\

hunter_add_package(GTest)
find_package(GTest CONFIG REQUIRED)
' CMakeLists.txt
```
```
gsed -i 's/add_subdirectory(third-party/gtest)//' CMakeLists.txt
```
```
gsed -i 's/gtest_main/GTest::main/' CMakeLists.txt
```
```
cmake -H. -B_builds -DBUILD_TESTS=ON

-- [hunter] Calculating Toolchain-SHA1
-- [hunter] Calculating Config-SHA1
-- [hunter] HUNTER_ROOT: /home/nastya/.hunter
-- [hunter] [ Hunter-ID: a20151e | Toolchain-ID: 347e47c | Config-ID: 4abab25 ]
-- [hunter] GTEST_ROOT: /home/nastya/.hunter/_Base/a20151e/347e47c/4abab25/Install (ver.: 1.14.0)
-- Configuring done
-- Generating done
-- Build files have been written to: /home/nastya/nastyaiva/workspace/projects/lab07/_builds
```
```
cmake --build _builds

[ 25%] Building CXX object CMakeFiles/print.dir/sources/print.cpp.o
[ 50%] Linking CXX static library libprint.a
[ 50%] Built target print
[ 75%] Building CXX object CMakeFiles/check.dir/tests/test1.cpp.o
[100%] Linking CXX executable check
[100%] Built target check
```
```
cmake --build _builds --target test

Running tests...
Test project /home/nastya/nastyaiva/workspace/projects/lab07/_builds
    Start 1: check
1/1 Test #1: check ............................   Passed    0.01 sec

100% tests passed, 0 tests failed out of 1

Total Test time (real) =   0.01 sec
```
```
ls -la $HOME/.hunter

итого 12
drwxrwxr-x  3 nastya nastya 4096 мая  6 18:47 .
drwxr-x--- 23 nastya nastya 4096 мая 10 13:18 ..
drwxrwxr-x  7 nastya nastya 4096 мая 10 13:43 _Base
```
```
git clone https://github.com/cpp-pm/hunter $HOME/projects/hunter
Клонирование в «/home/nastya/projects/hunter»...
remote: Enumerating objects: 52843, done.
remote: Counting objects: 100% (1937/1937), done.
remote: Compressing objects: 100% (942/942), done.
remote: Total 52843 (delta 813), reused 1866 (delta 779), pack-reused 50906
Получение объектов: 100% (52843/52843), 13.76 МиБ | 799.00 КиБ/с, готово.
Определение изменений: 100% (33009/33009), готово.
```
```
export HUNTER_ROOT=$HOME/projects/hunter
```
```
rm -rf _builds
```
```
cmake -H. -B_builds -DBUILD_TESTS=ON

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
-- [hunter] Calculating Toolchain-SHA1
-- [hunter] Calculating Config-SHA1
-- [hunter] HUNTER_ROOT: /home/nastya/projects/hunter
-- [hunter] [ Hunter-ID: xxxxxxx | Toolchain-ID: 347e47c | Config-ID: 5a7c41e ]
-- [hunter] GTEST_ROOT: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Install (ver.: 1.14.0)
-- [hunter] Building GTest
loading initial cache file /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/cache.cmake
loading initial cache file /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/args.cmake
-- The C compiler identification is GNU 11.4.0
-- The CXX compiler identification is GNU 11.4.0
-- Check for working C compiler: /usr/bin/cc - skipped
-- Detecting C compile features
-- Detecting C compile features - done
-- Check for working CXX compiler: /usr/bin/c++ - skipped
-- Detecting CXX compile features
-- Detecting CXX compile features - done
-- Configuring done
-- Generating done
-- Build files have been written to: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Build
[  6%] Creating directories for 'GTest-Release'
[ 12%] Performing download step (download, verify and extract) for 'GTest-Release'
-- Downloading...
   dst='/home/nastya/projects/hunter/_Base/Download/GTest/1.14.0/2b28c2a/v1.14.0.tar.gz'
   timeout='none'
   inactivity timeout='none'
-- Using src='https://github.com/google/googletest/archive/v1.14.0.tar.gz'
-- [download 1% complete]
-- [download 3% complete]
-- [download 5% complete]
-- [download 10% complete]
-- [download 11% complete]
-- [download 14% complete]
-- [download 21% complete]
-- [download 24% complete]
-- [download 28% complete]
-- [download 36% complete]
-- [download 41% complete]
-- [download 44% complete]
-- [download 49% complete]
-- [download 55% complete]
-- [download 59% complete]
-- [download 75% complete]
-- [download 79% complete]
-- [download 81% complete]
-- [download 84% complete]
-- [download 85% complete]
-- [download 100% complete]
-- verifying file...
       file='/home/nastya/projects/hunter/_Base/Download/GTest/1.14.0/2b28c2a/v1.14.0.tar.gz'
-- Downloading... done
-- extracting...
     src='/home/nastya/projects/hunter/_Base/Download/GTest/1.14.0/2b28c2a/v1.14.0.tar.gz'
     dst='/home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Source'
-- extracting... [tar xfz]
-- extracting... [analysis]
-- extracting... [rename]
-- extracting... [clean up]
-- extracting... done
[ 18%] No update step for 'GTest-Release'
[ 25%] No patch step for 'GTest-Release'
[ 31%] Performing configure step for 'GTest-Release'
loading initial cache file /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/cache.cmake
loading initial cache file /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/args.cmake
-- The C compiler identification is GNU 11.4.0
-- The CXX compiler identification is GNU 11.4.0
-- Check for working C compiler: /usr/bin/cc - skipped
-- Detecting C compile features
-- Detecting C compile features - done
-- Check for working CXX compiler: /usr/bin/c++ - skipped
-- Detecting CXX compile features
-- Detecting CXX compile features - done
-- Found Python3: /usr/bin/python3.10 (found version "3.10.12") found components: Interpreter 
-- Looking for pthread.h
-- Looking for pthread.h - found
-- Performing Test CMAKE_HAVE_LIBC_PTHREAD
-- Performing Test CMAKE_HAVE_LIBC_PTHREAD - Success
-- Found Threads: TRUE  
-- Configuring done
-- Generating done
-- Build files have been written to: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Build/GTest-Release-prefix/src/GTest-Release-build
[ 37%] Performing build step for 'GTest-Release'
[ 12%] Building CXX object googletest/CMakeFiles/gtest.dir/src/gtest-all.cc.o
[ 25%] Linking CXX static library ../lib/libgtest.a
[ 25%] Built target gtest
[ 50%] Building CXX object googletest/CMakeFiles/gtest_main.dir/src/gtest_main.cc.o
[ 50%] Building CXX object googlemock/CMakeFiles/gmock.dir/src/gmock-all.cc.o
[ 62%] Linking CXX static library ../lib/libgtest_main.a
[ 62%] Built target gtest_main
[ 75%] Linking CXX static library ../lib/libgmock.a
[ 75%] Built target gmock
[ 87%] Building CXX object googlemock/CMakeFiles/gmock_main.dir/src/gmock_main.cc.o
[100%] Linking CXX static library ../lib/libgmock_main.a
[100%] Built target gmock_main
[ 43%] Performing install step for 'GTest-Release'
-- Installing: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include
-- Installing: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gmock
-- Installing: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gmock/gmock-nice-strict.h
-- Installing: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gmock/gmock-cardinalities.h
-- Installing: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gmock/gmock-actions.h
-- Installing: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gmock/gmock-function-mocker.h
-- Installing: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gmock/gmock-matchers.h
-- Installing: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gmock/gmock-more-actions.h
-- Installing: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gmock/internal
-- Installing: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gmock/internal/gmock-pp.h
-- Installing: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gmock/internal/gmock-port.h
-- Installing: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gmock/internal/gmock-internal-utils.h
-- Installing: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gmock/internal/custom
-- Installing: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gmock/internal/custom/gmock-port.h
-- Installing: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gmock/internal/custom/README.md
-- Installing: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gmock/internal/custom/gmock-matchers.h
-- Installing: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gmock/internal/custom/gmock-generated-actions.h
-- Installing: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gmock/gmock-spec-builders.h
-- Installing: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gmock/gmock-more-matchers.h
-- Installing: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gmock/gmock.h
-- Installing: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/lib/libgmock.a
-- Installing: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/lib/libgmock_main.a
-- Installing: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/lib/pkgconfig/gmock.pc
-- Installing: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/lib/pkgconfig/gmock_main.pc
-- Installing: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/lib/cmake/GTest/GTestTargets.cmake
-- Installing: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/lib/cmake/GTest/GTestTargets-release.cmake
-- Installing: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/lib/cmake/GTest/GTestConfigVersion.cmake
-- Installing: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/lib/cmake/GTest/GTestConfig.cmake
-- Up-to-date: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include
-- Installing: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gtest
-- Installing: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gtest/gtest-assertion-result.h
-- Installing: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gtest/gtest_prod.h
-- Installing: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gtest/gtest.h
-- Installing: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gtest/gtest-printers.h
-- Installing: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gtest/gtest_pred_impl.h
-- Installing: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gtest/gtest-test-part.h
-- Installing: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gtest/gtest-matchers.h
-- Installing: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gtest/gtest-death-test.h
-- Installing: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gtest/gtest-typed-test.h
-- Installing: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gtest/gtest-message.h
-- Installing: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gtest/internal
-- Installing: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gtest/internal/gtest-type-util.h
-- Installing: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gtest/internal/gtest-internal.h
-- Installing: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gtest/internal/gtest-port-arch.h
-- Installing: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gtest/internal/gtest-filepath.h
-- Installing: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gtest/internal/gtest-string.h
-- Installing: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gtest/internal/gtest-death-test-internal.h
-- Installing: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gtest/internal/gtest-port.h
-- Installing: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gtest/internal/gtest-param-util.h
-- Installing: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gtest/internal/custom
-- Installing: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gtest/internal/custom/gtest.h
-- Installing: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gtest/internal/custom/gtest-printers.h
-- Installing: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gtest/internal/custom/README.md
-- Installing: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gtest/internal/custom/gtest-port.h
-- Installing: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gtest/gtest-param-test.h
-- Installing: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gtest/gtest-spi.h
-- Installing: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/lib/libgtest.a
-- Installing: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/lib/libgtest_main.a
-- Installing: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/lib/pkgconfig/gtest.pc
-- Installing: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/lib/pkgconfig/gtest_main.pc
loading initial cache file /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/args.cmake
[ 50%] Completed 'GTest-Release'
[ 50%] Built target GTest-Release
[ 56%] Creating directories for 'GTest-Debug'
[ 62%] Performing download step (download, verify and extract) for 'GTest-Debug'
-- verifying file...
       file='/home/nastya/projects/hunter/_Base/Download/GTest/1.14.0/2b28c2a/v1.14.0.tar.gz'
-- File already exists and hash match (skip download):
  file='/home/nastya/projects/hunter/_Base/Download/GTest/1.14.0/2b28c2a/v1.14.0.tar.gz'
  SHA1='2b28c2a3a30d86b1759543ef61fac3c4d69f8c4c'
-- extracting...
     src='/home/nastya/projects/hunter/_Base/Download/GTest/1.14.0/2b28c2a/v1.14.0.tar.gz'
     dst='/home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Source'
-- extracting... [tar xfz]
-- extracting... [analysis]
-- extracting... [rename]
-- extracting... [clean up]
-- extracting... done
[ 68%] No update step for 'GTest-Debug'
[ 75%] No patch step for 'GTest-Debug'
[ 81%] Performing configure step for 'GTest-Debug'
loading initial cache file /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/cache.cmake
loading initial cache file /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/args.cmake
-- The C compiler identification is GNU 11.4.0
-- The CXX compiler identification is GNU 11.4.0
-- Check for working C compiler: /usr/bin/cc - skipped
-- Detecting C compile features
-- Detecting C compile features - done
-- Check for working CXX compiler: /usr/bin/c++ - skipped
-- Detecting CXX compile features
-- Detecting CXX compile features - done
-- Found Python3: /usr/bin/python3.10 (found version "3.10.12") found components: Interpreter 
-- Looking for pthread.h
-- Looking for pthread.h - found
-- Performing Test CMAKE_HAVE_LIBC_PTHREAD
-- Performing Test CMAKE_HAVE_LIBC_PTHREAD - Success
-- Found Threads: TRUE  
-- Configuring done
-- Generating done
-- Build files have been written to: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Build/GTest-Debug-prefix/src/GTest-Debug-build
[ 87%] Performing build step for 'GTest-Debug'
[ 12%] Building CXX object googletest/CMakeFiles/gtest.dir/src/gtest-all.cc.o
[ 25%] Linking CXX static library ../lib/libgtestd.a
[ 25%] Built target gtest
[ 37%] Building CXX object googlemock/CMakeFiles/gmock.dir/src/gmock-all.cc.o
[ 50%] Building CXX object googletest/CMakeFiles/gtest_main.dir/src/gtest_main.cc.o
[ 62%] Linking CXX static library ../lib/libgtest_maind.a
[ 62%] Built target gtest_main
[ 75%] Linking CXX static library ../lib/libgmockd.a
[ 75%] Built target gmock
[ 87%] Building CXX object googlemock/CMakeFiles/gmock_main.dir/src/gmock_main.cc.o
[100%] Linking CXX static library ../lib/libgmock_maind.a
[100%] Built target gmock_main
[ 93%] Performing install step for 'GTest-Debug'
-- Up-to-date: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include
-- Up-to-date: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gmock
-- Up-to-date: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gmock/gmock-nice-strict.h
-- Up-to-date: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gmock/gmock-cardinalities.h
-- Up-to-date: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gmock/gmock-actions.h
-- Up-to-date: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gmock/gmock-function-mocker.h
-- Up-to-date: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gmock/gmock-matchers.h
-- Up-to-date: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gmock/gmock-more-actions.h
-- Up-to-date: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gmock/internal
-- Up-to-date: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gmock/internal/gmock-pp.h
-- Up-to-date: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gmock/internal/gmock-port.h
-- Up-to-date: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gmock/internal/gmock-internal-utils.h
-- Up-to-date: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gmock/internal/custom
-- Up-to-date: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gmock/internal/custom/gmock-port.h
-- Up-to-date: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gmock/internal/custom/README.md
-- Up-to-date: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gmock/internal/custom/gmock-matchers.h
-- Up-to-date: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gmock/internal/custom/gmock-generated-actions.h
-- Up-to-date: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gmock/gmock-spec-builders.h
-- Up-to-date: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gmock/gmock-more-matchers.h
-- Up-to-date: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gmock/gmock.h
-- Installing: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/lib/libgmockd.a
-- Installing: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/lib/libgmock_maind.a
-- Installing: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/lib/pkgconfig/gmock.pc
-- Installing: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/lib/pkgconfig/gmock_main.pc
-- Installing: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/lib/cmake/GTest/GTestTargets.cmake
-- Installing: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/lib/cmake/GTest/GTestTargets-debug.cmake
-- Installing: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/lib/cmake/GTest/GTestConfigVersion.cmake
-- Installing: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/lib/cmake/GTest/GTestConfig.cmake
-- Up-to-date: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include
-- Up-to-date: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gtest
-- Up-to-date: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gtest/gtest-assertion-result.h
-- Up-to-date: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gtest/gtest_prod.h
-- Up-to-date: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gtest/gtest.h
-- Up-to-date: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gtest/gtest-printers.h
-- Up-to-date: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gtest/gtest_pred_impl.h
-- Up-to-date: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gtest/gtest-test-part.h
-- Up-to-date: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gtest/gtest-matchers.h
-- Up-to-date: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gtest/gtest-death-test.h
-- Up-to-date: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gtest/gtest-typed-test.h
-- Up-to-date: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gtest/gtest-message.h
-- Up-to-date: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gtest/internal
-- Up-to-date: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gtest/internal/gtest-type-util.h
-- Up-to-date: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gtest/internal/gtest-internal.h
-- Up-to-date: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gtest/internal/gtest-port-arch.h
-- Up-to-date: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gtest/internal/gtest-filepath.h
-- Up-to-date: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gtest/internal/gtest-string.h
-- Up-to-date: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gtest/internal/gtest-death-test-internal.h
-- Up-to-date: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gtest/internal/gtest-port.h
-- Up-to-date: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gtest/internal/gtest-param-util.h
-- Up-to-date: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gtest/internal/custom
-- Up-to-date: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gtest/internal/custom/gtest.h
-- Up-to-date: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gtest/internal/custom/gtest-printers.h
-- Up-to-date: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gtest/internal/custom/README.md
-- Up-to-date: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gtest/internal/custom/gtest-port.h
-- Up-to-date: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gtest/gtest-param-test.h
-- Up-to-date: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/include/gtest/gtest-spi.h
-- Installing: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/lib/libgtestd.a
-- Installing: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/lib/libgtest_maind.a
-- Installing: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/lib/pkgconfig/gtest.pc
-- Installing: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/Install/lib/pkgconfig/gtest_main.pc
loading initial cache file /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest/args.cmake
[100%] Completed 'GTest-Debug'
[100%] Built target GTest-Debug
-- [hunter] Build step successful (dir: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Build/GTest)
-- [hunter] Cache saved: /home/nastya/projects/hunter/_Base/Cache/raw/a1101a3bdebf9a24548d1e5890e1ae10dc1e341d.tar.bz2
-- Looking for pthread.h
-- Looking for pthread.h - found
-- Performing Test CMAKE_HAVE_LIBC_PTHREAD
-- Performing Test CMAKE_HAVE_LIBC_PTHREAD - Success
-- Found Threads: TRUE  
-- Configuring done
-- Generating done
-- Build files have been written to: /home/nastya/nastyaiva/workspace/projects/lab07/_builds
```
```
cmake --build _builds

[ 25%] Building CXX object CMakeFiles/print.dir/sources/print.cpp.o
[ 50%] Linking CXX static library libprint.a
[ 50%] Built target print
[ 75%] Building CXX object CMakeFiles/check.dir/tests/test1.cpp.o
[100%] Linking CXX executable check
[100%] Built target check
```
```
cmake --build _builds --target test

Running tests...
Test project /home/nastya/nastyaiva/workspace/projects/lab07/_builds
    Start 1: check
1/1 Test #1: check ............................   Passed    0.01 sec

100% tests passed, 0 tests failed out of 1

Total Test time (real) =   0.01 sec
```
```
cat $HUNTER_ROOT/cmake/configs/default.cmake | grep GTest

  hunter_default_version(GTest VERSION 1.7.0-hunter-6)
  hunter_default_version(GTest VERSION 1.14.0)
```
```
cat $HUNTER_ROOT/cmake/projects/GTest/hunter.cmake
# Copyright (c) 2013, Ruslan Baratov
# All rights reserved.

# !!! DO NOT PLACE HEADER GUARDS HERE !!!

include(hunter_add_version)
include(hunter_cacheable)
include(hunter_download)
include(hunter_pick_scheme)
include(hunter_cmake_args)

hunter_add_version(
    PACKAGE_NAME
    GTest
    VERSION
    "1.7.0-hunter"
    URL
    "https://github.com/hunter-packages/gtest/archive/v1.7.0-hunter.tar.gz"
    SHA1
    1ed1c26d11fb592056c1cb912bd3c784afa96eaa
)

hunter_add_version(
    PACKAGE_NAME
    GTest
    VERSION
    "1.7.0-hunter-1"
    URL
    "https://github.com/hunter-packages/gtest/archive/v1.7.0-hunter-1.tar.gz"
    SHA1
    0cb1dcf75e144ad052d3f1e4923a7773bf9b494f
)

hunter_add_version(
    PACKAGE_NAME
    GTest
    VERSION
    "1.7.0-hunter-2"
    URL
    "https://github.com/hunter-packages/gtest/archive/v1.7.0-hunter-2.tar.gz"
    SHA1
    e62b2ef70308f63c32c560f7b6e252442eed4d57
)

hunter_add_version(
    PACKAGE_NAME
    GTest
    VERSION
    "1.7.0-hunter-3"
    URL
    "https://github.com/hunter-packages/gtest/archive/v1.7.0-hunter-3.tar.gz"
    SHA1
    fea7d3020e20f059255484c69755753ccadf6362
)

hunter_add_version(
    PACKAGE_NAME
    GTest
    VERSION
    "1.7.0-hunter-4"
    URL
    "https://github.com/hunter-packages/gtest/archive/v1.7.0-hunter-4.tar.gz"
    SHA1
    9b439c0c25437a083957b197ac6905662a5d901b
)

hunter_add_version(
    PACKAGE_NAME
    GTest
    VERSION
    "1.7.0-hunter-5"
    URL
    "https://github.com/hunter-packages/gtest/archive/v1.7.0-hunter-5.tar.gz"
    SHA1
    796804df3facb074087a4d8ba6f652e5ac69ad7f
)

hunter_add_version(
    PACKAGE_NAME
    GTest
    VERSION
    "1.7.0-hunter-6"
    URL
    "https://github.com/hunter-packages/gtest/archive/v1.7.0-hunter-6.tar.gz"
    SHA1
    64b93147abe287da8fe4e18cfd54ba9297dafb82
)

hunter_add_version(
    PACKAGE_NAME
    GTest
    VERSION
    "1.7.0-hunter-7"
    URL
    "https://github.com/hunter-packages/gtest/archive/v1.7.0-hunter-7.tar.gz"
    SHA1
    19b5c98747768bcd0622714f2ed40f17aee406b2
)

hunter_add_version(
    PACKAGE_NAME
    GTest
    VERSION
    "1.7.0-hunter-8"
    URL
    "https://github.com/hunter-packages/gtest/archive/v1.7.0-hunter-8.tar.gz"
    SHA1
    ac4d2215aa1b1d745a096e5e3b2dbe0c0f229ea5
)

hunter_add_version(
    PACKAGE_NAME
    GTest
    VERSION
    "1.7.0-hunter-9"
    URL
    "https://github.com/hunter-packages/gtest/archive/v1.7.0-hunter-9.tar.gz"
    SHA1
    8a47fe9c4e550f4ed0e2c05388dd291a059223d9
)

hunter_add_version(
    PACKAGE_NAME
    GTest
    VERSION
    "1.7.0-hunter-10"
    URL
    "https://github.com/hunter-packages/gtest/archive/v1.7.0-hunter-10.tar.gz"
    SHA1
    374e6dbe8619ab467c6b1a0b470a598407b172e9
)

hunter_add_version(
    PACKAGE_NAME
    GTest
    VERSION
    "1.7.0-hunter-11"
    URL
    "https://github.com/hunter-packages/gtest/archive/v1.7.0-hunter-11.tar.gz"
    SHA1
    c6ae948ca2bea1d734af01b1069491b00933ed31
)

hunter_add_version(
    PACKAGE_NAME
    GTest
    VERSION
    1.8.0-hunter-p2
    URL
    "https://github.com/hunter-packages/googletest/archive/1.8.0-hunter-p2.tar.gz"
    SHA1
    93148cb8850abe78b76ed87158fdb6b9c48e38c4
)

hunter_add_version(
    PACKAGE_NAME
    GTest
    VERSION
    1.8.0-hunter-p5
    URL https://github.com/hunter-packages/googletest/archive/1.8.0-hunter-p5.tar.gz
    SHA1 3325aa4fc8b30e665c9f73a60f19387b7db36f85
)

hunter_add_version(
    PACKAGE_NAME
    GTest
    VERSION
    1.8.0-hunter-p6
    URL
    "https://github.com/hunter-packages/googletest/archive/1.8.0-hunter-p6.tar.gz"
    SHA1
    f57096bd01c6f8cbef043b312d4d1e82f29648b6
)

hunter_add_version(
    PACKAGE_NAME
    GTest
    VERSION
    1.8.0-hunter-p7
    URL
    "https://github.com/hunter-packages/googletest/archive/1.8.0-hunter-p7.tar.gz"
    SHA1
    4fe083a96d7597f7dce6f453dca01e1d94a1e45b
)

hunter_add_version(
    PACKAGE_NAME
    GTest
    VERSION
    1.8.0-hunter-p8
    URL
    "https://github.com/hunter-packages/googletest/archive/1.8.0-hunter-p8.tar.gz"
    SHA1
    1cdd396b20c8d29f7ea08baaa49673b1c261f545
)

hunter_add_version(
    PACKAGE_NAME
    GTest
    VERSION
    1.8.0-hunter-p9
    URL
    "https://github.com/hunter-packages/googletest/archive/1.8.0-hunter-p9.tar.gz"
    SHA1
    a345f16cb610e0b5dfa7778dc2852b784cfede5b
)

hunter_add_version(
    PACKAGE_NAME
    GTest
    VERSION
    1.8.0-hunter-p10
    URL
    "https://github.com/hunter-packages/googletest/archive/1.8.0-hunter-p10.tar.gz"
    SHA1
    1d92c9f51af756410843b13f8c4e4df09e235394
)

hunter_add_version(
    PACKAGE_NAME
    GTest
    VERSION
    "1.8.0-hunter-p11"
    URL
    "https://github.com/hunter-packages/googletest/archive/1.8.0-hunter-p11.tar.gz"
    SHA1
    76c6aec038f7d7258bf5c4f45c4817b34039d285
)

hunter_add_version(
    PACKAGE_NAME
    GTest
    VERSION
    "1.8.1"
    URL
    "https://github.com/google/googletest/archive/release-1.8.1.tar.gz"
    SHA1
    152b849610d91a9dfa1401293f43230c2e0c33f8
)

hunter_add_version(
    PACKAGE_NAME
    GTest
    VERSION
    "1.10.0"
    URL
    "https://github.com/google/googletest/archive/release-1.10.0.tar.gz"
    SHA1
    9c89be7df9c5e8cb0bc20b3c4b39bf7e82686770
)

hunter_add_version(
    PACKAGE_NAME
    GTest
    VERSION
    "1.10.0-p0"
    URL
    "https://github.com/hunter-packages/googletest/archive/v1.10.0-p0.tar.gz"
    SHA1
    f7c72be12120e018f53cda0e0daa26fab5da7dfc
)

hunter_add_version(
    PACKAGE_NAME
    GTest
    VERSION
    "1.10.0-p1"
    URL
    "https://github.com/hunter-packages/googletest/archive/v1.10.0-p1.tar.gz"
    SHA1
    06a1f667f200ff94d38b608e44c3c8061c7b8f2f
)

hunter_add_version(
    PACKAGE_NAME
    GTest
    VERSION
    "1.11.0"
    URL
    "https://github.com/google/googletest/archive/release-1.11.0.tar.gz"
    SHA1
    7b100bb68db8df1060e178c495f3cbe941c9b058
)

hunter_add_version(
    PACKAGE_NAME
    GTest
    VERSION
    "1.12.1"
    URL
    "https://github.com/google/googletest/archive/release-1.12.1.tar.gz"
    SHA1
    cdddd449d4e3aa7bd421d4519c17139ea1890fe7
)

hunter_add_version(
    PACKAGE_NAME
    GTest
    VERSION
    "1.13.0"
    URL
    "https://github.com/google/googletest/archive/v1.13.0.tar.gz"
    SHA1
    bfa4b5131b6eaac06962c251742c96aab3f7aa78
)

hunter_add_version(
    PACKAGE_NAME
    GTest
    VERSION
    "1.14.0"
    URL
    "https://github.com/google/googletest/archive/v1.14.0.tar.gz"
    SHA1
    2b28c2a3a30d86b1759543ef61fac3c4d69f8c4c
)

if(HUNTER_GTest_VERSION VERSION_LESS 1.8.0 OR HUNTER_GTest_VERSION VERSION_GREATER_EQUAL 1.11.0)
  set(_gtest_license "LICENSE")
else()
  set(_gtest_license "googletest/LICENSE")
endif()

# gtest_force_shared_crt prevents GoogleTest from modifying options
# rather than forcing it to use shared libraries
hunter_cmake_args(
    GTest
    CMAKE_ARGS
    HUNTER_INSTALL_LICENSE_FILES=${_gtest_license}
    gtest_force_shared_crt=TRUE
)

hunter_pick_scheme(DEFAULT url_sha1_cmake)
hunter_cacheable(GTest)
hunter_download(PACKAGE_NAME GTest PACKAGE_INTERNAL_DEPS_ID 1)
```
```
mkdir cmake/Hunter
```
```
cat > cmake/Hunter/config.cmake <<EOF
> hunter_config(GTest VERSION 1.7.0-hunter-9)
> EOF
```
```
mkdir demo
```
```
cat > demo/main.cpp <<EOF

> #include <print.hpp>

#include <cstdlib>

int main(int argc, char* argv[])
{
 const char* log_path = std::getenv("LOG_PATH");
 if (log_path == nullptr)
 {
 std::cerr << "undefined environment variable: LOG_PATH" << std::endl;
 return 1;
 }
 std::string text;
 while (std::cin >> text)
 {
 std::ofstream out{log_path, std::ios_base::app};
 print(text, out);
 out << std::endl;
 }
}
> EOF
```
```
gsed -i '/endif()/a\

add_executable(demo ${CMAKE_CURRENT_SOURCE_DIR}/demo/main.cpp)
target_link_libraries(demo print)
install(TARGETS demo RUNTIME DESTINATION bin)
' CMakeLists.txt

```

```
mkdir tools
```
```
git submodule add https://github.com/ruslo/polly tools/polly

Клонирование в «/home/nastya/nastyaiva/workspace/projects/lab07/tools/polly»...
remote: Enumerating objects: 6578, done.
remote: Counting objects: 100% (32/32), done.
remote: Compressing objects: 100% (15/15), done.
remote: Total 6578 (delta 21), reused 20 (delta 17), pack-reused 6546
Получение объектов: 100% (6578/6578), 1.68 МиБ | 2.04 МиБ/с, готово.
Определение изменений: 100% (4551/4551), готово.
```
```
tools/polly/bin/polly.py --test

Python version: 3.10
Build dir: /home/nastya/nastyaiva/workspace/projects/lab07/_builds/default
Execute command: [
  `which`
  `cmake`
]

[/home/nastya/nastyaiva/workspace/projects/lab07]> "which" "cmake"

/usr/bin/cmake
Execute command: [
  `cmake`
  `--version`
]

[/home/nastya/nastyaiva/workspace/projects/lab07]> "cmake" "--version"

cmake version 3.22.1

CMake suite maintained and supported by Kitware (kitware.com/cmake).
Execute command: [
  `cmake`
  `-H.`
  `-B/home/nastya/nastyaiva/workspace/projects/lab07/_builds/default`
  `-DCMAKE_TOOLCHAIN_FILE=/home/nastya/nastyaiva/workspace/projects/lab07/tools/polly/default.cmake`
]

[/home/nastya/nastyaiva/workspace/projects/lab07]> "cmake" "-H." "-B/home/nastya/nastyaiva/workspace/projects/lab07/_builds/default" "-DCMAKE_TOOLCHAIN_FILE=/home/nastya/nastyaiva/workspace/projects/lab07/tools/polly/default.cmake"

-- [polly] Used toolchain: Default
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
-- [hunter] Calculating Toolchain-SHA1
-- [hunter] Calculating Config-SHA1
-- [hunter] HUNTER_ROOT: /home/nastya/projects/hunter
-- [hunter] [ Hunter-ID: xxxxxxx | Toolchain-ID: 347e47c | Config-ID: 5a7c41e ]
-- [hunter] GTEST_ROOT: /home/nastya/projects/hunter/_Base/xxxxxxx/347e47c/5a7c41e/Install (ver.: 1.14.0)
-- Looking for pthread.h
-- Looking for pthread.h - found
-- Performing Test CMAKE_HAVE_LIBC_PTHREAD
-- Performing Test CMAKE_HAVE_LIBC_PTHREAD - Success
-- Found Threads: TRUE
-- Configuring done
-- Generating done
-- Build files have been written to: /home/nastya/nastyaiva/workspace/projects/lab07/_builds/default
Execute command: [
  `cmake`
  `--build`
  `/home/nastya/nastyaiva/workspace/projects/lab07/_builds/default`
  `--`
]

[/home/nastya/nastyaiva/workspace/projects/lab07]> "cmake" "--build" "/home/nastya/nastyaiva/workspace/projects/lab07/_builds/default" "--"

[ 25%] Building CXX object CMakeFiles/print.dir/sources/print.cpp.o
[ 50%] Linking CXX static library libprint.a
[ 50%] Built target print
[ 75%] Building CXX object CMakeFiles/demo.dir/demo/main.cpp.o
[100%] Linking CXX executable demo
[100%] Built target demo
Run tests
Execute command: [
  `ctest`
]

[/home/nastya/nastyaiva/workspace/projects/lab07/_builds/default]> "ctest"

*********************************
No test configuration file found!
*********************************
Usage

  ctest [options]

-
Log saved: /home/nastya/nastyaiva/workspace/projects/lab07/_logs/polly/default/log.txt
-
Generate: 0:00:03.879126s
Build: 0:00:02.481164s
Test: 0:00:00.035462s
-
Total: 0:00:06.396144s
-
SUCCESS
```
```
tools/polly/bin/polly.py --install

Python version: 3.10
Build dir: /home/nastya/nastyaiva/workspace/projects/lab07/_builds/default
Execute command: [
  `which`
  `cmake`
]

[/home/nastya/nastyaiva/workspace/projects/lab07]> "which" "cmake"

/usr/bin/cmake
Execute command: [
  `cmake`
  `--version`
]

[/home/nastya/nastyaiva/workspace/projects/lab07]> "cmake" "--version"

cmake version 3.22.1

CMake suite maintained and supported by Kitware (kitware.com/cmake).

== WARNING ==

Looks like cmake arguments changed. You have two options to fix it:
  * Remove build directory completely by adding '--clear' (works 100%)
  * Run configure again by adding '--reconfig' (you must understand how CMake cache variables works/updated)

- "cmake" "-H." "-B/home/nastya/nastyaiva/workspace/projects/lab07/_builds/default" "-DCMAKE_TOOLCHAIN_FILE=/home/nastya/nastyaiva/workspace/projects/lab07/tools/polly/default.cmake"
+ "cmake" "-H." "-B/home/nastya/nastyaiva/workspace/projects/lab07/_builds/default" "-DCMAKE_TOOLCHAIN_FILE=/home/nastya/nastyaiva/workspace/projects/lab07/tools/polly/default.cmake" "-DCMAKE_INSTALL_PREFIX=/home/nastya/nastyaiva/workspace/projects/lab07/_install/default"
?                                                                                                                                                                                     ++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
```
```
sudo tools/polly/bin/polly.py --toolchain clang-cxx14

Python version: 3.10
Build dir: /home/nastya/nastyaiva/workspace/projects/lab07/_builds/clang-cxx14
Execute command: [
  `which`
  `cmake`
]

[/home/nastya/nastyaiva/workspace/projects/lab07]> "which" "cmake"

/usr/bin/cmake
Execute command: [
  `cmake`
  `--version`
]

[/home/nastya/nastyaiva/workspace/projects/lab07]> "cmake" "--version"

cmake version 3.22.1

CMake suite maintained and supported by Kitware (kitware.com/cmake).
Execute command: [
  `cmake`
  `-H.`
  `-B/home/nastya/nastyaiva/workspace/projects/lab07/_builds/clang-cxx14`
  `-GUnix Makefiles`
  `-DCMAKE_TOOLCHAIN_FILE=/home/nastya/nastyaiva/workspace/projects/lab07/tools/polly/clang-cxx14.cmake`
]

[/home/nastya/nastyaiva/workspace/projects/lab07]> "cmake" "-H." "-B/home/nastya/nastyaiva/workspace/projects/lab07/_builds/clang-cxx14" "-GUnix Makefiles" "-DCMAKE_TOOLCHAIN_FILE=/home/nastya/nastyaiva/workspace/projects/lab07/tools/polly/clang-cxx14.cmake"

-- [polly] Used toolchain: clang / c++14 support
-- The C compiler identification is Clang 14.0.0
-- The CXX compiler identification is Clang 14.0.0
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Check for working C compiler: /usr/bin/clang - skipped
-- Detecting C compile features
-- Detecting C compile features - done
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- Check for working CXX compiler: /usr/bin/clang++ - skipped
-- Detecting CXX compile features
-- Detecting CXX compile features - done
-- [hunter] Calculating Toolchain-SHA1
-- [hunter] Calculating Config-SHA1
-- [hunter] HUNTER_ROOT: /root/.hunter
-- [hunter] [ Hunter-ID: a20151e | Toolchain-ID: 45ed920 | Config-ID: 4abab25 ]
-- [hunter] GTEST_ROOT: /root/.hunter/_Base/a20151e/45ed920/4abab25/Install (ver.: 1.14.0)
-- [hunter] Building GTest
loading initial cache file /root/.hunter/_Base/a20151e/45ed920/4abab25/cache.cmake
loading initial cache file /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/args.cmake
-- [polly] Used toolchain: clang / c++14 support
-- The C compiler identification is Clang 14.0.0
-- The CXX compiler identification is Clang 14.0.0
-- Check for working C compiler: /usr/bin/clang - skipped
-- Detecting C compile features
-- Detecting C compile features - done
-- Check for working CXX compiler: /usr/bin/clang++ - skipped
-- Detecting CXX compile features
-- Detecting CXX compile features - done
-- Configuring done
-- Generating done
-- Build files have been written to: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Build
[  6%] Creating directories for 'GTest-Release'
[ 12%] Performing download step (download, verify and extract) for 'GTest-Release'
-- Downloading...
   dst='/root/.hunter/_Base/Download/GTest/1.14.0/2b28c2a/v1.14.0.tar.gz'
   timeout='none'
   inactivity timeout='none'
-- Using src='https://github.com/google/googletest/archive/v1.14.0.tar.gz'
-- [download 1% complete]
-- [download 3% complete]
-- [download 4% complete]
-- [download 9% complete]
-- [download 10% complete]
-- [download 16% complete]
-- [download 20% complete]
-- [download 27% complete]
-- [download 28% complete]
-- [download 31% complete]
-- [download 35% complete]
-- [download 38% complete]
-- [download 39% complete]
-- [download 40% complete]
-- [download 44% complete]
-- [download 48% complete]
-- [download 52% complete]
-- [download 56% complete]
-- [download 60% complete]
-- [download 64% complete]
-- [download 68% complete]
-- [download 74% complete]
-- [download 77% complete]
-- [download 83% complete]
-- [download 84% complete]
-- [download 88% complete]
-- [download 90% complete]
-- [download 94% complete]
-- [download 95% complete]
-- [download 96% complete]
-- [download 97% complete]
-- [download 98% complete]
-- [download 100% complete]
-- verifying file...
       file='/root/.hunter/_Base/Download/GTest/1.14.0/2b28c2a/v1.14.0.tar.gz'
-- Downloading... done
-- extracting...
     src='/root/.hunter/_Base/Download/GTest/1.14.0/2b28c2a/v1.14.0.tar.gz'
     dst='/root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Source'
-- extracting... [tar xfz]
-- extracting... [analysis]
-- extracting... [rename]
-- extracting... [clean up]
-- extracting... done
[ 18%] No update step for 'GTest-Release'
[ 25%] No patch step for 'GTest-Release'
[ 31%] Performing configure step for 'GTest-Release'
loading initial cache file /root/.hunter/_Base/a20151e/45ed920/4abab25/cache.cmake
loading initial cache file /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/args.cmake
-- [polly] Used toolchain: clang / c++14 support
-- The C compiler identification is Clang 14.0.0
-- The CXX compiler identification is Clang 14.0.0
-- Check for working C compiler: /usr/bin/clang - skipped
-- Detecting C compile features
-- Detecting C compile features - done
-- Check for working CXX compiler: /usr/bin/clang++ - skipped
-- Detecting CXX compile features
-- Detecting CXX compile features - done
-- Found Python3: /usr/bin/python3.10 (found version "3.10.12") found components: Interpreter
-- Looking for pthread.h
-- Looking for pthread.h - found
-- Performing Test CMAKE_HAVE_LIBC_PTHREAD
-- Performing Test CMAKE_HAVE_LIBC_PTHREAD - Success
-- Found Threads: TRUE
-- Configuring done
-- Generating done
-- Build files have been written to: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Build/GTest-Release-prefix/src/GTest-Release-build
[ 37%] Performing build step for 'GTest-Release'
[ 12%] Building CXX object googletest/CMakeFiles/gtest.dir/src/gtest-all.cc.o
[ 25%] Linking CXX static library ../lib/libgtest.a
[ 25%] Built target gtest
[ 37%] Building CXX object googletest/CMakeFiles/gtest_main.dir/src/gtest_main.cc.o
[ 50%] Building CXX object googlemock/CMakeFiles/gmock.dir/src/gmock-all.cc.o
[ 62%] Linking CXX static library ../lib/libgtest_main.a
[ 62%] Built target gtest_main
[ 75%] Linking CXX static library ../lib/libgmock.a
[ 75%] Built target gmock
[ 87%] Building CXX object googlemock/CMakeFiles/gmock_main.dir/src/gmock_main.cc.o
[100%] Linking CXX static library ../lib/libgmock_main.a
[100%] Built target gmock_main
[ 43%] Performing install step for 'GTest-Release'
-- Installing: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include
-- Installing: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gmock
-- Installing: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gmock/gmock-nice-strict.h
-- Installing: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gmock/gmock-cardinalities.h
-- Installing: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gmock/gmock-actions.h
-- Installing: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gmock/gmock-function-mocker.h
-- Installing: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gmock/gmock-matchers.h
-- Installing: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gmock/gmock-more-actions.h
-- Installing: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gmock/internal
-- Installing: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gmock/internal/gmock-pp.h
-- Installing: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gmock/internal/gmock-port.h
-- Installing: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gmock/internal/gmock-internal-utils.h
-- Installing: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gmock/internal/custom
-- Installing: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gmock/internal/custom/gmock-port.h
-- Installing: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gmock/internal/custom/README.md
-- Installing: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gmock/internal/custom/gmock-matchers.h
-- Installing: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gmock/internal/custom/gmock-generated-actions.h
-- Installing: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gmock/gmock-spec-builders.h
-- Installing: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gmock/gmock-more-matchers.h
-- Installing: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gmock/gmock.h
-- Installing: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/lib/libgmock.a
-- Installing: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/lib/libgmock_main.a
-- Installing: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/lib/pkgconfig/gmock.pc
-- Installing: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/lib/pkgconfig/gmock_main.pc
-- Installing: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/lib/cmake/GTest/GTestTargets.cmake
-- Installing: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/lib/cmake/GTest/GTestTargets-release.cmake
-- Installing: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/lib/cmake/GTest/GTestConfigVersion.cmake
-- Installing: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/lib/cmake/GTest/GTestConfig.cmake
-- Up-to-date: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include
-- Installing: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gtest
-- Installing: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gtest/gtest-assertion-result.h
-- Installing: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gtest/gtest_prod.h
-- Installing: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gtest/gtest.h
-- Installing: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gtest/gtest-printers.h
-- Installing: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gtest/gtest_pred_impl.h
-- Installing: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gtest/gtest-test-part.h
-- Installing: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gtest/gtest-matchers.h
-- Installing: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gtest/gtest-death-test.h
-- Installing: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gtest/gtest-typed-test.h
-- Installing: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gtest/gtest-message.h
-- Installing: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gtest/internal
-- Installing: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gtest/internal/gtest-type-util.h
-- Installing: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gtest/internal/gtest-internal.h
-- Installing: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gtest/internal/gtest-port-arch.h
-- Installing: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gtest/internal/gtest-filepath.h
-- Installing: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gtest/internal/gtest-string.h
-- Installing: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gtest/internal/gtest-death-test-internal.h
-- Installing: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gtest/internal/gtest-port.h
-- Installing: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gtest/internal/gtest-param-util.h
-- Installing: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gtest/internal/custom
-- Installing: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gtest/internal/custom/gtest.h
-- Installing: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gtest/internal/custom/gtest-printers.h
-- Installing: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gtest/internal/custom/README.md
-- Installing: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gtest/internal/custom/gtest-port.h
-- Installing: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gtest/gtest-param-test.h
-- Installing: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gtest/gtest-spi.h
-- Installing: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/lib/libgtest.a
-- Installing: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/lib/libgtest_main.a
-- Installing: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/lib/pkgconfig/gtest.pc
-- Installing: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/lib/pkgconfig/gtest_main.pc
loading initial cache file /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/args.cmake
[ 50%] Completed 'GTest-Release'
[ 50%] Built target GTest-Release
[ 56%] Creating directories for 'GTest-Debug'
[ 62%] Performing download step (download, verify and extract) for 'GTest-Debug'
-- verifying file...
       file='/root/.hunter/_Base/Download/GTest/1.14.0/2b28c2a/v1.14.0.tar.gz'
-- File already exists and hash match (skip download):
  file='/root/.hunter/_Base/Download/GTest/1.14.0/2b28c2a/v1.14.0.tar.gz'
  SHA1='2b28c2a3a30d86b1759543ef61fac3c4d69f8c4c'
-- extracting...
     src='/root/.hunter/_Base/Download/GTest/1.14.0/2b28c2a/v1.14.0.tar.gz'
     dst='/root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Source'
-- extracting... [tar xfz]
-- extracting... [analysis]
-- extracting... [rename]
-- extracting... [clean up]
-- extracting... done
[ 68%] No update step for 'GTest-Debug'
[ 75%] No patch step for 'GTest-Debug'
[ 81%] Performing configure step for 'GTest-Debug'
loading initial cache file /root/.hunter/_Base/a20151e/45ed920/4abab25/cache.cmake
loading initial cache file /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/args.cmake
-- [polly] Used toolchain: clang / c++14 support
-- The C compiler identification is Clang 14.0.0
-- The CXX compiler identification is Clang 14.0.0
-- Check for working C compiler: /usr/bin/clang - skipped
-- Detecting C compile features
-- Detecting C compile features - done
-- Check for working CXX compiler: /usr/bin/clang++ - skipped
-- Detecting CXX compile features
-- Detecting CXX compile features - done
-- Found Python3: /usr/bin/python3.10 (found version "3.10.12") found components: Interpreter
-- Looking for pthread.h
-- Looking for pthread.h - found
-- Performing Test CMAKE_HAVE_LIBC_PTHREAD
-- Performing Test CMAKE_HAVE_LIBC_PTHREAD - Success
-- Found Threads: TRUE
-- Configuring done
-- Generating done
-- Build files have been written to: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Build/GTest-Debug-prefix/src/GTest-Debug-build
[ 87%] Performing build step for 'GTest-Debug'
[ 12%] Building CXX object googletest/CMakeFiles/gtest.dir/src/gtest-all.cc.o
[ 25%] Linking CXX static library ../lib/libgtestd.a
[ 25%] Built target gtest
[ 37%] Building CXX object googletest/CMakeFiles/gtest_main.dir/src/gtest_main.cc.o
[ 50%] Building CXX object googlemock/CMakeFiles/gmock.dir/src/gmock-all.cc.o
[ 62%] Linking CXX static library ../lib/libgtest_maind.a
[ 62%] Built target gtest_main
[ 75%] Linking CXX static library ../lib/libgmockd.a
[ 75%] Built target gmock
[ 87%] Building CXX object googlemock/CMakeFiles/gmock_main.dir/src/gmock_main.cc.o
[100%] Linking CXX static library ../lib/libgmock_maind.a
[100%] Built target gmock_main
[ 93%] Performing install step for 'GTest-Debug'
-- Up-to-date: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include
-- Up-to-date: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gmock
-- Up-to-date: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gmock/gmock-nice-strict.h
-- Up-to-date: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gmock/gmock-cardinalities.h
-- Up-to-date: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gmock/gmock-actions.h
-- Up-to-date: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gmock/gmock-function-mocker.h
-- Up-to-date: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gmock/gmock-matchers.h
-- Up-to-date: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gmock/gmock-more-actions.h
-- Up-to-date: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gmock/internal
-- Up-to-date: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gmock/internal/gmock-pp.h
-- Up-to-date: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gmock/internal/gmock-port.h
-- Up-to-date: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gmock/internal/gmock-internal-utils.h
-- Up-to-date: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gmock/internal/custom
-- Up-to-date: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gmock/internal/custom/gmock-port.h
-- Up-to-date: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gmock/internal/custom/README.md
-- Up-to-date: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gmock/internal/custom/gmock-matchers.h
-- Up-to-date: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gmock/internal/custom/gmock-generated-actions.h
-- Up-to-date: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gmock/gmock-spec-builders.h
-- Up-to-date: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gmock/gmock-more-matchers.h
-- Up-to-date: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gmock/gmock.h
-- Installing: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/lib/libgmockd.a
-- Installing: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/lib/libgmock_maind.a
-- Installing: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/lib/pkgconfig/gmock.pc
-- Installing: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/lib/pkgconfig/gmock_main.pc
-- Installing: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/lib/cmake/GTest/GTestTargets.cmake
-- Installing: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/lib/cmake/GTest/GTestTargets-debug.cmake
-- Installing: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/lib/cmake/GTest/GTestConfigVersion.cmake
-- Installing: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/lib/cmake/GTest/GTestConfig.cmake
-- Up-to-date: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include
-- Up-to-date: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gtest
-- Up-to-date: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gtest/gtest-assertion-result.h
-- Up-to-date: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gtest/gtest_prod.h
-- Up-to-date: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gtest/gtest.h
-- Up-to-date: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gtest/gtest-printers.h
-- Up-to-date: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gtest/gtest_pred_impl.h
-- Up-to-date: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gtest/gtest-test-part.h
-- Up-to-date: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gtest/gtest-matchers.h
-- Up-to-date: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gtest/gtest-death-test.h
-- Up-to-date: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gtest/gtest-typed-test.h
-- Up-to-date: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gtest/gtest-message.h
-- Up-to-date: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gtest/internal
-- Up-to-date: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gtest/internal/gtest-type-util.h
-- Up-to-date: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gtest/internal/gtest-internal.h
-- Up-to-date: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gtest/internal/gtest-port-arch.h
-- Up-to-date: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gtest/internal/gtest-filepath.h
-- Up-to-date: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gtest/internal/gtest-string.h
-- Up-to-date: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gtest/internal/gtest-death-test-internal.h
-- Up-to-date: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gtest/internal/gtest-port.h
-- Up-to-date: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gtest/internal/gtest-param-util.h
-- Up-to-date: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gtest/internal/custom
-- Up-to-date: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gtest/internal/custom/gtest.h
-- Up-to-date: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gtest/internal/custom/gtest-printers.h
-- Up-to-date: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gtest/internal/custom/README.md
-- Up-to-date: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gtest/internal/custom/gtest-port.h
-- Up-to-date: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gtest/gtest-param-test.h
-- Up-to-date: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/include/gtest/gtest-spi.h
-- Installing: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/lib/libgtestd.a
-- Installing: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/lib/libgtest_maind.a
-- Installing: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/lib/pkgconfig/gtest.pc
-- Installing: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/Install/lib/pkgconfig/gtest_main.pc
loading initial cache file /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest/args.cmake
[100%] Completed 'GTest-Debug'
[100%] Built target GTest-Debug
-- [hunter] Build step successful (dir: /root/.hunter/_Base/a20151e/45ed920/4abab25/Build/GTest)
-- [hunter] Cache saved: /root/.hunter/_Base/Cache/raw/960f690a9b3077c56347ed44abab2bc8e4189a0b.tar.bz2
-- Looking for pthread.h
-- Looking for pthread.h - found
-- Performing Test CMAKE_HAVE_LIBC_PTHREAD
-- Performing Test CMAKE_HAVE_LIBC_PTHREAD - Success
-- Found Threads: TRUE
-- Configuring done
-- Generating done
-- Build files have been written to: /home/nastya/nastyaiva/workspace/projects/lab07/_builds/clang-cxx14
Execute command: [
  `cmake`
  `--build`
  `/home/nastya/nastyaiva/workspace/projects/lab07/_builds/clang-cxx14`
  `--`
]

[/home/nastya/nastyaiva/workspace/projects/lab07]> "cmake" "--build" "/home/nastya/nastyaiva/workspace/projects/lab07/_builds/clang-cxx14" "--"

[ 25%] Building CXX object CMakeFiles/print.dir/sources/print.cpp.o
[ 50%] Linking CXX static library libprint.a
[ 50%] Built target print
[ 75%] Building CXX object CMakeFiles/demo.dir/demo/main.cpp.o
[100%] Linking CXX executable demo
[100%] Built target demo
-
Log saved: /home/nastya/nastyaiva/workspace/projects/lab07/_logs/polly/clang-cxx14/log.txt
-
Generate: 0:01:00.684381s
Build: 0:00:02.829357s
-
Total: 0:01:03.514457s
-
SUCCESS
```








