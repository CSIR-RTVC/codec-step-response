# CMakeLists.txt in x264Codec dir

IF(WIN32)
# SET(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -D_BUILD_FOR_SHORT")
SET(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -D_CRT_SECURE_NO_WARNINGS")
# get rid of some compiler warnings
SET(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -D_CRT_SECURE_NO_WARNINGS")
ELSE(WIN32)
add_definitions("-Wwrite-strings")
#SET(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wwrite-strings")
ENDIF(WIN32)

INCLUDE_DIRECTORIES(
${CodecStepResponseIncludes}
$ENV{X264_DIR}
)

# Lib directories
LINK_DIRECTORIES(
${CodecStepResponseLink}
)

SET(H264v2_LIB_HDRS
stdafx.h
X264Codec.h
)	

SET(H264v2_LIB_SRCS 
stdafx.cpp
X264Codec.cpp
)

ADD_LIBRARY( X264Codec SHARED ${H264v2_LIB_SRCS} ${H264v2_LIB_HDRS})

TARGET_LINK_LIBRARIES(
X264Codec
x264
dl
) 

