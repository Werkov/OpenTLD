
include_directories(imacq
    mftracker
    tld
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

set(HEADERS 
    imacq/ImAcq.h
    mftracker/BB.h
    mftracker/BBPredict.h
    mftracker/FBTrack.h
    mftracker/Lk.h
    mftracker/Median.h
    tld/Clustering.h
    tld/DetectionResult.h
    tld/DetectorCascade.h
    tld/EnsembleClassifier.h
    tld/ForegroundDetector.h
    tld/IntegralImage.h
    tld/MedianFlowTracker.h
    tld/NNClassifier.h
    tld/NormalizedPatch.h
    tld/TLD.h
    tld/TLDUtil.h
    tld/VarianceFilter.h)

add_library(libopentld SHARED ${SOURCES} ${HEADERS})
add_library(libopentld-static STATIC ${SOURCES} ${HEADERS})

target_link_libraries(libopentld ${OpenCV_LIBS})

set_target_properties(libopentld PROPERTIES OUTPUT_NAME opentld)

install(TARGETS libopentld
	LIBRARY DESTINATION lib
	ARCHIVE DESTINATION lib
)
