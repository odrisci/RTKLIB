SET(SOURCES rtkrcv.c vt.c)
add_executable(rtkrcv ${SOURCES})
target_include_directories(rtkrcv PUBLIC ${CMAKE_SOURCE_DIR}/src)
target_compile_definitions(rtkrcv PRIVATE ${RTKLIB_DEFINES})
target_link_libraries(rtkrcv PRIVATE rtklib Threads::Threads)

install(TARGETS rtkrcv
    EXPORT rtklibTargets
    RUNTIME DESTINATION bin)
