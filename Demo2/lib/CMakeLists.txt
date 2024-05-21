cmake_minimum_required ( VERSION 3.26 )

project ( demo-lib )

add_library ( ${PROJECT_NAME}
	"${CMAKE_CURRENT_SOURCE_DIR}/include/Lib.hpp"
	"${CMAKE_CURRENT_SOURCE_DIR}/src/Lib.cpp"
)

target_include_directories ( ${PROJECT_NAME}
	PUBLIC "${CMAKE_CURRENT_SOURCE_DIR}/include"
)

install (
	DIRECTORY	"${CMAKE_CURRENT_SOURCE_DIR}/include"
	DESTINATION "."
)

# TODO: install libfiles