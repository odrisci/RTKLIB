set(SRC ${PROJECT_SOURCE_DIR}/src)
SET(SOURCES
    str2str.c
	${SRC}/stream.c
	${SRC}/streamsvr.c
	${SRC}/rtkcmn.c
	${SRC}/solution.c
	${SRC}/sbas.c
	${SRC}/geoid.c
	${SRC}/rcvraw.c
	${SRC}/rcv/novatel.c
	${SRC}/rcv/ublox.c
	${SRC}/rcv/ss2.c
	${SRC}/rcv/crescent.c
	${SRC}/rcv/skytraq.c
	${SRC}/rcv/javad.c
	${SRC}/rcv/nvs.c
	${SRC}/rcv/binex.c
	${SRC}/rcv/rt17.c
	${SRC}/rtcm.c
	${SRC}/rtcm2.c
	${SRC}/rtcm3.c
	${SRC}/rtcm3e.c
	${SRC}/preceph.c
	${SRC}/rcv/septentrio.c
    )
add_executable(str2str ${SOURCES})
target_include_directories(str2str PUBLIC ${PROJECT_SOURCE_DIR}/src)
target_compile_definitions(str2str PRIVATE ${RTKLIB_DEFINES})
target_link_libraries(str2str PRIVATE Threads::Threads)

install(TARGETS str2str
    EXPORT rtklibTargets
    RUNTIME DESTINATION ${RTKLIB_BINDIR})
