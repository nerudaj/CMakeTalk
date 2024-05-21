cmake_minimum_required ( VERSION 3.26 )

set ( CMAKE_CXX_STANDARD 23 )
set ( CMAKE_GENERATOR_PLATFORM x64 )

project ( CMakeTalk )

add_library ( ${PROJECT_NAME}
	"${CMAKE_CURRENT_SOURCE_DIR}/include/Lib.hpp"
	"${CMAKE_CURRENT_SOURCE_DIR}/src/Lib.cpp"
)

target_include_directories ( ${PROJECT_NAME}
	PUBLIC "${CMAKE_CURRENT_SOURCE_DIR}/include"
)
