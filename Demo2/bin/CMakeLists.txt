cmake_minimum_required ( VERSION 3.26 )

set ( TARGET_NAME demo-bin )

add_executable ( ${TARGET_NAME}
	"${CMAKE_CURRENT_SOURCE_DIR}/src/Main.cpp"
)

target_link_libraries ( ${TARGET_NAME}
	LINK_PRIVATE demo-lib
)

install (
	TARGETS ${TARGET_NAME}
	CONFIGURATIONS Release
	RUNTIME DESTINATION bin
)
