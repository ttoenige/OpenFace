add_executable(FaceLandmarkVid FaceLandmarkVid.cpp)

# Local libraries
include_directories(${LandmarkDetector_SOURCE_DIR}/include)

include_directories(../../lib/local/LandmarkDetector/include)
include_directories(../../lib/local/FaceAnalyser/include)		

target_link_libraries(FaceLandmarkVid LandmarkDetector)
target_link_libraries(FaceLandmarkVid FaceAnalyser)
target_link_libraries(FaceLandmarkVid ${dlib_LIBRARIES})
target_link_libraries(FaceLandmarkVid ${OpenCV_LIBS} ${Boost_LIBRARIES} ${TBB_LIBRARIES})

CONFIGURE_FILE("start_FaceLandmarkVid.sh.in" start_FaceLandmarkVid.sh @ONLY)
INSTALL(PROGRAMS ${CMAKE_CURRENT_BINARY_DIR}/start_FaceLandmarkVid.sh DESTINATION bin)



install (TARGETS FaceLandmarkVid DESTINATION ${CMAKE_INSTALL_PREFIX}/bin)
