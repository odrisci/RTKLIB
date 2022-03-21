set(SRC ${PROJECT_SOURCE_DIR}/src)
SET(SOURCES
    rtkrcv.c
    vt.c
	${SRC}/rtkcmn.c
	${SRC}/rtksvr.c
	${SRC}/rtkpos.c
	${SRC}/geoid.c
	${SRC}/solution.c
	${SRC}/lambda.c
	${SRC}/sbas.c
	${SRC}/stream.c
	${SRC}/rcvraw.c
	${SRC}/rtcm.c
	${SRC}/rtcm2.c
	${SRC}/rtcm3.c
	${SRC}/rtcm3e.c
	${SRC}/preceph.c
	${SRC}/options.c
	${SRC}/pntpos.c
	${SRC}/ppp.c
	${SRC}/ppp_ar.c
	${SRC}/rcv/novatel.c
	${SRC}/rcv/ublox.c
	${SRC}/rcv/ss2.c
	${SRC}/rcv/crescent.c
	${SRC}/rcv/skytraq.c
	${SRC}/rcv/javad.c
	${SRC}/rcv/nvs.c
	${SRC}/rcv/binex.c
	${SRC}/rcv/rt17.c
	${SRC}/ephemeris.c
	${SRC}/rinex.c
	${SRC}/ionex.c
	${SRC}/tides.c
	${SRC}/rcv/septentrio.c
    )
add_executable(rtkrcv ${SOURCES})
target_include_directories(rtkrcv PUBLIC ${PROJECT_SOURCE_DIR}/src)
target_compile_definitions(rtkrcv PRIVATE ${RTKLIB_DEFINES})
target_link_libraries(rtkrcv PRIVATE Threads::Threads)
if(MSVC)
    target_link_libraries(rtkrcv PRIVATE winmm.lib)
else()
    target_link_libraries(rtkrcv PRIVATE m)
endif()

install(TARGETS rtkrcv
    EXPORT rtklibTargets
    RUNTIME DESTINATION ${RTKLIB_BINDIR})
