
include_directories(imacq
    mftracker
    tld
    .
    ../3rdparty/cvblobs
    ${OpenCV_INCLUDE_DIRS})
link_directories(${OpenCV_LIB_DIR})

set(SOURCES 
    imacq/ImAcq.cpp
    mftracker/BB.cpp
    mftracker/BBPredict.cpp
    mftracker/FBTrack.cpp
    mftracker/Lk.cpp
    mftracker/Median.cpp
    tld/Clustering.cpp
    tld/DetectionResult.cpp
    tld/DetectorCascade.cpp
    tld/EnsembleClassifier.cpp
    tld/ForegroundDetector.cpp
    tld/MedianFlowTracker.cpp
    tld/NNClassifier.cpp
    tld/TLD.cpp
    tld/TLDUtil.cpp
    tld/VarianceFilter.cpp)

set(PUBLIC_HEADERS
    tld/DetectorCascade.h
    tld/TLD.h)

set(HEADERS 
    ${PUBLIC_HEADERS}
    imacq/ImAcq.h
    mftracker/BB.h
    mftracker/BBPredict.h
    mftracker/FBTrack.h
    mftracker/Lk.h
    mftracker/Median.h
    tld/Clustering.h
    tld/DetectionResult.h
    tld/EnsembleClassifier.h
    tld/ForegroundDetector.h
    tld/IntegralImage.h
    tld/MedianFlowTracker.h
    tld/NNClassifier.h
    tld/NormalizedPatch.h
    tld/TLDUtil.h
    tld/VarianceFilter.h)

add_library(libopentld SHARED ${SOURCES} ${HEADERS})

target_link_libraries(libopentld ${OpenCV_LIBS} cvblobs)
set_target_properties(libopentld PROPERTIES OUTPUT_NAME opentld)

install(TARGETS libopentld
	LIBRARY DESTINATION lib64
	ARCHIVE DESTINATION lib64
)

install(FILES ${PUBLIC_HEADERS} DESTINATION include/tld)
