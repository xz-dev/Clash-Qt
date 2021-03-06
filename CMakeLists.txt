cmake_minimum_required(VERSION 3.9)
project(clash_qt)

set(CMAKE_CXX_STANDARD 11)

IF (CMAKE_BUILD_TYPE STREQUAL Debug)
    ADD_DEFINITIONS(-DDEBUG)
ENDIF()
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)
set(CMAKE_AUTOUIC ON)

find_package(Qt5 5.12.0 REQUIRED COMPONENTS Core Gui WebEngineWidgets Widgets)

set(src_files
        src/main.cpp
        src/webui.h src/webui.cpp
        src/systemtray.h src/systemtray.cpp
        src/clash.cpp src/clash.h
        src/clashconfig.cpp src/clashconfig.h
        src/subscribemanager.h src/subscribemanager.cpp
        src/editdialog.h src/editdialog.cpp
        )

set(res_files res/res.qrc)
add_executable(clash-qt ${src_files} ${res_files})

target_link_libraries(clash-qt Qt5::Core Qt5::Gui Qt5::WebEngineCore Qt5::WebEngineWidgets Qt5::Widgets yaml-cpp)