# The following lines of boilerplate have to be in your project's CMakeLists
# in this exact order for cmake to work correctly
cmake_minimum_required(VERSION 3.5)

# (Not part of the boilerplate)
# This example uses an extra component for common functions such as Wi-Fi and Ethernet connection.
# set(EXTRA_COMPONENT_DIRS $ENV{IDF_PATH}/examples/common_components/protocol_examples_common)

include($ENV{IDF_PATH}/tools/cmake/project.cmake)
# Fix für den LVGL-Fehler
set(COMPONENTS_NO_BUILD_TESTS 1)
add_compile_definitions(LV_CONF_SKIP)
add_compile_definitions(LV_CONF_INCLUDE_SIMPLE)


project(esp-miner)

