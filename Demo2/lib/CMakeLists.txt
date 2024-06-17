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
	FILES
		"${CMAKE_CURRENT_BINARY_DIR}/Debug/${TARGET_NAME}${CMAKE_DEBUG_POSTFIX}.lib"
	DESTINATION
		"lib"
)

install (
	FILES
		"${CMAKE_CURRENT_BINARY_DIR}/Release/${TARGET_NAME}.lib"
	DESTINATION
		"lib"
)

install (
	DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/include"
	DESTINATION "."
)

# Proper way to achieve the same thing, but requires two build dirs and multibuild config
# https://cmake.org/cmake/help/v3.26/guide/tutorial/Packaging%20Debug%20and%20Release.html
# also requires you to annotate all header files with correct properties
# https://stackoverflow.com/questions/54271925/how-to-configure-cmakelists-txt-to-install-public-headers-of-a-shared-library
# install( TARGETS ${TARGET_NAME}
# 		CONFIGURATIONS Debug Release
#        ARCHIVE
# 			DESTINATION lib
#        LIBRARY
#			DESTINATION lib
#		PUBLIC_HEADER DESTINATION "include" # or FILE_SET
# )