cmake_minimum_required ( VERSION 3.26 )

set ( TARGET_NAME demo-lib )
set ( CMAKE_DEBUG_POSTFIX "-d" )

add_library ( ${TARGET_NAME}
	"${CMAKE_CURRENT_SOURCE_DIR}/include/Lib.hpp"
	"${CMAKE_CURRENT_SOURCE_DIR}/src/Lib.cpp"
)

target_include_directories ( ${TARGET_NAME}
	PUBLIC "${CMAKE_CURRENT_SOURCE_DIR}/include"
)

install (
	DIRECTORY	"${CMAKE_CURRENT_SOURCE_DIR}/include"
	DESTINATION "."
)

# TODO: install libfiles