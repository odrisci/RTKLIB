set(SRC ${PROJECT_SOURCE_DIR}/src)
SET(SOURCES 
    pos2kml.c
	${SRC}/convkml.c
	${SRC}/convgpx.c
	${SRC}/solution.c
	${SRC}/geoid.c
	${SRC}/rtkcmn.c
	${SRC}/preceph.c
    )
add_executable(pos2kml ${SOURCES})
target_include_directories(pos2kml PUBLIC ${PROJECT_SOURCE_DIR}/src)
target_compile_definitions(pos2kml PRIVATE ${RTKLIB_DEFINES})
if(MSVC)
	target_link_libraries(pos2kml winmm.lib)
endif()

install(TARGETS pos2kml
    EXPORT rtklibTargets
    RUNTIME DESTINATION bin)
