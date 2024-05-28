cmake_minimum_required ( VERSION 3.26 )

project ( Demo2
	VERSION     0.42.0
	DESCRIPTION "CMake demo for C++ Meetup"
	LANGUAGES   CXX
)

include ( "${CMAKE_SOURCE_DIR}/cmake/CPM.cmake" )

set ( CMAKE_CXX_STANDARD 26 ) # /std:c++latest in MSVC

option ( ENABLE_TESTS "Enable building unit test target" ON )

add_subdirectory ( "${CMAKE_SOURCE_DIR}/bin" )
add_subdirectory ( "${CMAKE_SOURCE_DIR}/lib" )

if ( ${ENABLE_TESTS} )
	enable_testing()
	add_subdirectory ( "${CMAKE_SOURCE_DIR}/tests" )
endif()

include ( CPack )

set ( CPACK_GENERATOR "NSIS" )
