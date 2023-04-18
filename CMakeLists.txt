cmake_minimum_required(VERSION 3.16)

project(Direction-Sense-using-Neural-Network VERSION 0.1 LANGUAGES CXX)

set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_AUTORCC ON)

find_package(Qt6 6.4 REQUIRED COMPONENTS Quick)

qt_standard_project_setup()

set( project_sources
    src/src/qt/myappsettingsclass.h
    src/src/qt/myappsettingsclass.cpp
)

qt_add_executable(appDirection-Sense-using-Neural-Network
    resources.qrc
    src/main.cpp
    ${project_sources}
)


qt_add_qml_module(appDirection-Sense-using-Neural-Network
    URI Direction-Sense-using-Neural-Network
    VERSION 1.0
    QML_FILES
    "src/ui/Main.qml"
    "src/ui/pages/home.qml"
    "src/ui/pages/app-settings.qml"
    "src/ui/others/home-tabs/Output.qml"
    "src/ui/others/home-tabs/Processing.qml"
    "src/ui/others/home-tabs/Input.qml"
)
set_target_properties(appDirection-Sense-using-Neural-Network PROPERTIES
    MACOSX_BUNDLE_GUI_IDENTIFIER my.example.com
    MACOSX_BUNDLE_BUNDLE_VERSION ${PROJECT_VERSION}
    MACOSX_BUNDLE_SHORT_VERSION_STRING ${PROJECT_VERSION_MAJOR}.${PROJECT_VERSION_MINOR}
    MACOSX_BUNDLE TRUE
    WIN32_EXECUTABLE TRUE
)

target_link_libraries(appDirection-Sense-using-Neural-Network
    PRIVATE Qt6::Quick
)

install(TARGETS appDirection-Sense-using-Neural-Network
    BUNDLE DESTINATION .
    LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR})
