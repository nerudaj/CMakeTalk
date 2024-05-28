cmake_minimum_required ( VERSION 3.26 )

CPMAddPackage( "gh:catchorg/Catch2@3.3.2" )

set ( ${TARGET_NAME} demo-tests )

add_executable( ${TARGET_NAME}
    "${CMAKE_CURRENT_SOURCE_DIR}/src/LibTests.cpp"
)

target_link_libraries( ${TARGET_NAME}
    LINK_PRIVATE demo-lib
    LINK_PRIVATE Catch2::Catch2WithMain
)

add_test (
    NAME "basic test"
    COMMAND ${TARGET_NAME}
)