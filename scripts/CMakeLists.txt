if(enable-dep-dll)
	if(enable-qt5)
		find_package(Qt5Gui QUIET)
		if(Qt5Gui_FOUND)
			get_target_property(mgl_qt_loc Qt5::QWindowsIntegrationPlugin LOCATION)
		endif(Qt5Gui_FOUND)
	endif(enable-qt5)

	install(CODE "SET(mgl_qt_loc \"${mgl_qt_loc}\")")
	install(CODE "SET(CMAKE_INSTALL_PREFIX \"${CMAKE_INSTALL_PREFIX}\")")
	install(SCRIPT install-deps.cmake)
endif(enable-dep-dll)

if(WIN32)
	install(FILES ${CMAKE_SOURCE_DIR}/scripts/FindMathGL2.cmake DESTINATION ${CMAKE_INSTALL_PREFIX} RENAME mathgl2-config.cmake)
else(WIN32)
	install(FILES ${CMAKE_SOURCE_DIR}/scripts/FindMathGL2.cmake DESTINATION ${MathGL_INSTALL_LIB_DIR}/cmake/mathgl2/ RENAME mathgl2-config.cmake)
endif(WIN32)

#export(TARGETS MathGLTargets FILE "${PROJECT_BINARY_DIR}/MathGLTargets.cmake")
#export(PACKAGE MathGL2)

#configure_file(MathGLConfig.cmake.in "${MathGL2_BINARY_DIR}/MathGLConfig.cmake" @ONLY)
#configure_file(MathGLConfigVersion.cmake.in "${MathGL2_BINARY_DIR}/MathGLConfigVersion.cmake" @ONLY)

#install(FILES
#	"${MathGL2_BINARY_DIR}/MathGLConfig.cmake"
#	"${MathGL2_BINARY_DIR}/MathGLConfigVersion.cmake"
#	DESTINATION "${MathGL_INSTALL_CMAKE_DIR}" COMPONENT dev)

#install(EXPORT MathGLTargets DESTINATION "${MathGL_INSTALL_CMAKE_DIR}" COMPONENT dev)
