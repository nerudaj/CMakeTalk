cmake_minimum_required ( VERSION 3.26 )

include ( "${CMAKE_SOURCE_DIR}/cmake/CPM.cmake" )

set ( CMAKE_CXX_STANDARD 26 ) # /std:c++latest in MSVC

option ( ENABLE_TESTS "Enable building unit test target" ON )

project ( CMakeTalk
	VERSION 0.42.0
	DESCRIPTION "CMake demonstration for C++ talk"
)

add_subdirectory ( "${CMAKE_SOURCE_DIR}/bin" )
add_subdirectory ( "${CMAKE_SOURCE_DIR}/lib" )

if ( ${ENABLE_TESTS} )
	enable_testing()
	add_subdirectory ( "${CMAKE_SOURCE_DIR}/tests" )
endif()

include ( CPack )

set ( CPACK_GENERATOR "NSIS" )
