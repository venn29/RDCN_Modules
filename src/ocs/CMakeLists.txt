check_include_file_cxx(stdint.h HAVE_STDINT_H)
if(HAVE_STDINT_H)
    add_definitions(-DHAVE_STDINT_H)
endif()

set(examples_as_tests_sources)
if(${ENABLE_EXAMPLES})
    set(examples_as_tests_sources
        #test/ocs-examples-test-suite.cc
        )
endif()

build_lib(
    LIBNAME ocs
    SOURCE_FILES model/ipv4-ocs-routing.cc
                 model/route-schedule.cc
                 model/Ipv4EpsRouting.cc
                 model/MultiChannelPointToPoint.cc
                 model/OcsUtils.cc
                 model/new-bulk-send-application.cc
                 model/PFifoFlowSizeQueueDisc.cc
                 model/Ipv4SingleEPSRouting.cc
                 model/SingleRouteSchedule.cc
                 model/FlowSizeDistribution.cc
                 model/AppPlanner.cc
                 model/Prio2Device.cc
#                 model/BufferRecorder.cc
                 helper/ocs-helper.cc
                 helper/MultideviceHelper.cc
                 helper/new-bulk-send-helper.cc
                 helper/FatTreeHelper.cc
                 helper/Prio2DeviceHelper.cc
    HEADER_FILES model/ipv4-ocs-routing.h
                 model/route-schedule.h
                 model/Ipv4EpsRouting.h
                 model/MultiChannelPointToPoint.h
                 model/OcsUtils.h
                 model/new-bulk-send-application.h
                 model/PFifoFlowSizeQueueDisc.h
                 model/Ipv4SingleEPSRouting.h
                 model/SingleRouteSchedule.h
                 model/FlowSizeDistribution.h
                 model/AppPlanner.h
                 model/Prio2Device.h
#                 model/BufferRecorder.h
                 helper/ocs-helper.h
                 helper/MultideviceHelper.h
                 helper/new-bulk-send-helper.h
                 helper/FatTreeHelper.h
                 helper/Prio2DeviceHelper.h
    LIBRARIES_TO_LINK 
                 ${libcore}
                 ${libinternet}
                 ${libnetwork}
                 ${libapplications}
    TEST_SOURCES test/ocs-test-suite.cc
                 ${examples_as_tests_sources}
)

