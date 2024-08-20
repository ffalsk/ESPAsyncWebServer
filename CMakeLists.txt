
get_filename_component(dir ${CMAKE_CURRENT_LIST_FILE} PATH)
FILE(GLOB_RECURSE app_sources
    ${dir}/src/*.cpp
)

idf_component_register(SRCS ${app_sources}
    REQUIRES "ESPAsyncWebServer"
    INCLUDE_DIRS "src"
    REQUIRES arduino-esp32 AsyncTCP)

target_compile_definitions(${COMPONENT_TARGET} PUBLIC -DESP32)
target_compile_options(${COMPONENT_TARGET} PRIVATE -fno-rtti)
