include_directories(${CMAKE_CURRENT_SOURCE_DIR})
include_directories(../common)
add_definitions(-DAPPNAME=mfsmetalogger)

collect_sources(METALOGGER)

add_library(metalogger ${METALOGGER_SOURCES})
target_link_libraries(metalogger mfscommon ${ZLIB_LIBRARIES})
add_tests(metalogger ${METALOGGER_TESTS})

add_executable(mfsmetalogger ${MAIN_SRC})
target_link_libraries(mfsmetalogger metalogger)
install(TARGETS mfsmetalogger RUNTIME DESTINATION ${SBIN_SUBDIR})
