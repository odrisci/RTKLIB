SET(SOURCES pos2kml.c)
add_executable(pos2kml ${SOURCES})
target_include_directories(pos2kml PUBLIC ${CMAKE_SOURCE_DIR}/src)
target_compile_definitions(pos2kml PRIVATE ${RTKLIB_DEFINES})
target_link_libraries(pos2kml PRIVATE rtklib)

install(TARGETS pos2kml
    EXPORT rtklibTargets
    RUNTIME DESTINATION bin)
