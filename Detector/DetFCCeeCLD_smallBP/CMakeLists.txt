###############################################################################
# Package: DetFCCeeCLD_smallBP
################################################################################

install(DIRECTORY ${CMAKE_CURRENT_LIST_DIR}/compact DESTINATION ${CMAKE_INSTALL_DATADIR}/${CMAKE_PROJECT_NAME}/Detector/DetFCCeeCLD_smallBP)


file(GLOB sources src/*.cpp)
add_dd4hep_plugin(DetFCCeeCLD_smallBP SHARED ${sources})
target_link_libraries(DetFCCeeCLD_smallBP DD4hep::DDCore)

set(LIBRARY_OUTPUT_PATH ${CMAKE_LIBRARY_OUTPUT_DIRECTORY})

add_test(NAME ConstructDetFCCeeCLD_smallBP
         COMMAND root -q -b ".github/scripts/load_detector.C(\"Detector/DetFCCeeCLD_smallBP/compact/FCCee_DectMaster.xml\")"
         WORKING_DIRECTORY ${PROJECT_SOURCE_DIR}
         )
k4_set_test_env(ConstructDetFCCeeCLD_smallBP)
