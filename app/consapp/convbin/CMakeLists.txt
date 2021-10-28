set(SRC ${CMAKE_SOURCE_DIR}/src)
set(SOURCES 
    convbin.c
	${SRC}/rtkcmn.c
	${SRC}/rinex.c
	${SRC}/sbas.c
	${SRC}/preceph.c
	${SRC}/rcvraw.c
	${SRC}/convrnx.c
	${SRC}/rtcm.c
	${SRC}/rtcm2.c
	${SRC}/rtcm3.c
	${SRC}/rtcm3e.c
	${SRC}/pntpos.c
	${SRC}/ionex.c
	${SRC}/ephemeris.c
	${SRC}/rcv/novatel.c
	${SRC}/rcv/ss2.c
	${SRC}/rcv/ublox.c
	${SRC}/rcv/crescent.c
	${SRC}/rcv/skytraq.c
	${SRC}/rcv/javad.c
	${SRC}/rcv/nvs.c
	${SRC}/rcv/binex.c
	${SRC}/rcv/rt17.c
	${SRC}/rcv/septentrio.c
    )
add_executable(convbin ${SOURCES})
target_include_directories(convbin PUBLIC ${CMAKE_SOURCE_DIR}/src)
target_compile_definitions(convbin PRIVATE ${RTKLIB_DEFINES})

install(TARGETS convbin
    EXPORT rtklibTargets
    RUNTIME DESTINATION bin)
