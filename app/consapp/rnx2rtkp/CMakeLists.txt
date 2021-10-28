SET(SOURCES rnx2rtkp.c)
add_executable(rnx2rtkp ${SOURCES})
target_include_directories(rnx2rtkp PUBLIC ${CMAKE_SOURCE_DIR}/src)
target_compile_definitions(rnx2rtkp PRIVATE ${RTKLIB_DEFINES})
target_link_libraries(rnx2rtkp PRIVATE rtklib)


install(TARGETS rnx2rtkp
    EXPORT rtklibTargets
    RUNTIME DESTINATION bin)
