SET(SOURCES str2str.c)
add_executable(str2str ${SOURCES})
target_include_directories(str2str PUBLIC ${CMAKE_SOURCE_DIR}/src)
target_compile_definitions(str2str PRIVATE ${RTKLIB_DEFINES})
target_link_libraries(str2str PRIVATE rtklib Threads::Threads)

install(TARGETS str2str
    EXPORT rtklibTargets
    RUNTIME DESTINATION bin)
