set(SOURCES convbin.c)
add_executable(convbin ${SOURCES})
target_include_directories(convbin PUBLIC ${CMAKE_SOURCE_DIR}/src)
target_compile_definitions(convbin PRIVATE ${RTKLIB_DEFINES})
target_link_libraries(convbin PRIVATE rtklib)

install(TARGETS convbin
    EXPORT rtklibTargets
    RUNTIME DESTINATION bin)
