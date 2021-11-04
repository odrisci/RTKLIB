set(SRC ${PROJECT_SOURCE_DIR}/src)
SET(SOURCES 
    rnx2rtkp.c
	${SRC}/rtkcmn.c
	${SRC}/rinex.c
	${SRC}/rtkpos.c
	${SRC}/postpos.c
	${SRC}/solution.c
	${SRC}/lambda.c
	${SRC}/geoid.c
	${SRC}/sbas.c
	${SRC}/preceph.c
	${SRC}/pntpos.c
	${SRC}/ephemeris.c
	${SRC}/options.c
	${SRC}/ppp.c
	${SRC}/ppp_ar.c
	${SRC}/rtcm.c
	${SRC}/rtcm2.c
	${SRC}/rtcm3.c
	${SRC}/rtcm3e.c
	${SRC}/ionex.c
	${SRC}/tides.c
    )
add_executable(rnx2rtkp ${SOURCES})
target_include_directories(rnx2rtkp PUBLIC ${PROJECT_SOURCE_DIR}/src)
target_compile_definitions(rnx2rtkp PRIVATE ${RTKLIB_DEFINES})
if(MSVC)
	target_link_libraries(rnx2rtkp winmm.lib)
endif()

install(TARGETS rnx2rtkp
    EXPORT rtklibTargets
    RUNTIME DESTINATION ${RTKLIB_BINDIR})
