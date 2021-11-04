set(SOURCES
    "convgpx.c"
    "convkml.c"
    "convrnx.c"
    "datum.c"
    "download.c"
    "ephemeris.c"
    "geoid.c"
    "gis.c"
    "ionex.c"
    "lambda.c"
    "options.c"
    "pntpos.c"
    "postpos.c"
    "ppp.c"
    "ppp_ar.c"
    "preceph.c"
    "rcvraw.c"
    "rinex.c"
    "rtcm.c"
    "rtcm2.c"
    "rtcm3.c"
    "rtcm3e.c"
    "rtkcmn.c"
    "rtkpos.c"
    "rtksvr.c"
    "sbas.c"
    "solution.c"
    "stream.c"
    "streamsvr.c"
    "tides.c"
    "tle.c"
    "rcv/binex.c"
    "rcv/crescent.c"
    "rcv/javad.c"
    "rcv/novatel.c"
    "rcv/nvs.c"
    "rcv/rt17.c"
    "rcv/septentrio.c"
    "rcv/skytraq.c"
    "rcv/ss2.c"
    "rcv/ublox.c"
    )
#* options : -DENAGLO   enable GLONASS
#*           -DENAGAL   enable Galileo
#*           -DENAQZS   enable QZSS
#*           -DENACMP   enable BeiDou
#*           -DENAIRN   enable IRNSS
#*           -DNFREQ=n  set number of obs codes/frequencies
#*           -DNEXOBS=n set number of extended obs codes
#*           -DMAXOBS=n set max number of obs data in an epoch
#*           -DWIN32    use WIN32 API
#*           -DWIN_DLL  generate library as Windows DLL

add_library(rtklib SHARED ${SOURCES} )
target_include_directories(rtklib PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})
target_compile_definitions(rtklib PRIVATE
    SHARED_LIB
    ${RTKLIB_DEFINES})

if(MSVC)
	target_link_libraries(rtklib PRIVATE winmm.lib wsock32 ws2_32)
endif()

install(TARGETS rtklib
    EXPORT rtklibTargets
    LIBRARY DESTINATION lib
    ARCHIVE DESTINATION lib
    RUNTIME DESTINATION bin
    INCLUDES DESTINATION include)

