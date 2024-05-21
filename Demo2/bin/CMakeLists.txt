cmake_minimum_required ( VERSION 3.26 )

project ( demo-bin )

add_executable ( ${PROJECT_NAME}
	"${CMAKE_CURRENT_SOURCE_DIR}/src/Main.cpp"
)

target_link_libraries ( ${PROJECT_NAME}
	LINK_PRIVATE demo-lib
)

install (
	FILES "${CMAKE_CURRENT_BINARY_DIR}/Release/${PROJECT_NAME}.exe"
	DESTINATION "bin"
)
