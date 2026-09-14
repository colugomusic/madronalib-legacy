cmake_minimum_required(VERSION 3.30)
project(madronalib)
add_library(madronalib INTERFACE)
add_library(madronalib::madronalib ALIAS madronalib)
target_sources(madronalib PUBLIC
	FILE_SET HEADERS
	BASE_DIRS
		${CMAKE_CURRENT_SOURCE_DIR}
	FILES
		${CMAKE_CURRENT_SOURCE_DIR}/external/sse2neon.h
		${CMAKE_CURRENT_SOURCE_DIR}/app/MLPlatform.h
		${CMAKE_CURRENT_SOURCE_DIR}/DSP/MLDSPBuffer.h
		${CMAKE_CURRENT_SOURCE_DIR}/DSP/MLDSPFilters.h
		${CMAKE_CURRENT_SOURCE_DIR}/DSP/MLDSPFunctional.h
		${CMAKE_CURRENT_SOURCE_DIR}/DSP/MLDSPGens.h
		${CMAKE_CURRENT_SOURCE_DIR}/DSP/MLDSPMath.h
		${CMAKE_CURRENT_SOURCE_DIR}/DSP/MLDSPMathNEON.h
		${CMAKE_CURRENT_SOURCE_DIR}/DSP/MLDSPMathSSE.h
		${CMAKE_CURRENT_SOURCE_DIR}/DSP/MLDSPOps.h
		${CMAKE_CURRENT_SOURCE_DIR}/DSP/MLDSPProjections.h
		${CMAKE_CURRENT_SOURCE_DIR}/DSP/MLDSPRatio.h
		${CMAKE_CURRENT_SOURCE_DIR}/DSP/MLDSPRouting.h
		${CMAKE_CURRENT_SOURCE_DIR}/DSP/MLDSPSample.h
		${CMAKE_CURRENT_SOURCE_DIR}/DSP/MLDSPScalarMath.h
		${CMAKE_CURRENT_SOURCE_DIR}/DSP/MLDSPScale.h
		${CMAKE_CURRENT_SOURCE_DIR}/DSP/MLDSPUtils.h
)
target_include_directories(madronalib INTERFACE
	$<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}>
	$<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/external>
    $<INSTALL_INTERFACE:include/madronalib>
	$<INSTALL_INTERFACE:include/madronalib/app>
	$<INSTALL_INTERFACE:include/madronalib/DSP>
	$<INSTALL_INTERFACE:include/madronalib/external>
)
install(
	TARGETS madronalib
	EXPORT madronalib
	FILE_SET HEADERS
	DESTINATION include/madronalib
)
install(EXPORT madronalib
    FILE madronalibConfig.cmake
    NAMESPACE madronalib::
    DESTINATION lib/cmake/madronalib
)
