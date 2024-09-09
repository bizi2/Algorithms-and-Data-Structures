# CMakeList.txt: файл проекта CMake верхнего уровня; проведите глобальную конфигурацию
# и включите сюда подпроекты.
#
cmake_minimum_required (VERSION 3.8)

# Включение горячей перезагрузки для компиляторов MSVC, если поддерживается.
if (POLICY CMP0141)
  cmake_policy(SET CMP0141 NEW)
  set(CMAKE_MSVC_DEBUG_INFORMATION_FORMAT "$<IF:$<AND:$<C_COMPILER_ID:MSVC>,$<CXX_COMPILER_ID:MSVC>>,$<$<CONFIG:Debug,RelWithDebInfo>:EditAndContinue>,$<$<CONFIG:Debug,RelWithDebInfo>:ProgramDatabase>>")
endif()

project ("libpair")

# Включите подпроекты.
add_subdirectory ("CMakeProject1")

add_subdirectory(lib_easy_example)    # подключаем дополнительный CMakeLists.txt из подкаталога с именем lib_easy_example

add_subdirectory(lib_pair)	      # подключаем дополнительный CMakeLists.txt из подкаталога с именем lib_pair

add_subdirectory(main)                # подключаем дополнительный CMakeLists.txt из подкаталога с именем main

option(BTEST "build test?" ON) 
