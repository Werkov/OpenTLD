add_library(cvblobs SHARED
    blob.cpp
    BlobContour.cpp
    BlobOperators.cpp
    BlobProperties.cpp
    BlobResult.cpp
    ComponentLabeling.cpp
    blob.h
    BlobContour.h
    BlobLibraryConfiguration.h
    BlobOperators.h
    BlobProperties.h
    BlobResult.h
    ComponentLabeling.h)

target_link_libraries(cvblobs ${OpenCV_LIBS})

install(TARGETS cvblobs
	LIBRARY DESTINATION lib64
	ARCHIVE DESTINATION lib64
)
