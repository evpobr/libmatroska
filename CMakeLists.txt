cmake_minimum_required(VERSION 3.1.2)

project(matroska CXX C)

set(libmatroska_SOURCES
        src/FileKax.cpp
        src/KaxAttached.cpp
        src/KaxAttachments.cpp
        src/KaxBlock.cpp
        src/KaxBlockData.cpp
        src/KaxCluster.cpp
        src/KaxContexts.cpp
        src/KaxCues.cpp
        src/KaxCuesData.cpp
        src/KaxInfoData.cpp
        src/KaxSeekHead.cpp
        src/KaxSegment.cpp
        src/KaxSemantic.cpp
        src/KaxTracks.cpp
        src/KaxVersion.cpp)

set(libmatroska_PUBLIC_HEADERS
        matroska/FileKax.h
        matroska/KaxAttached.h
        matroska/KaxAttachments.h
        matroska/KaxBlockData.h
        matroska/KaxBlock.h
        matroska/KaxChapters.h
        matroska/KaxClusterData.h
        matroska/KaxCluster.h
        matroska/KaxConfig.h
        matroska/KaxContentEncoding.h
        matroska/KaxContexts.h
        matroska/KaxCuesData.h
        matroska/KaxCues.h
        matroska/KaxDefines.h
        matroska/KaxInfoData.h
        matroska/KaxInfo.h
        matroska/KaxSeekHead.h
        matroska/KaxSegment.h
        matroska/KaxSemantic.h
        matroska/KaxTag.h
        matroska/KaxTags.h
        matroska/KaxTrackAudio.h
        matroska/KaxTrackEntryData.h
        matroska/KaxTracks.h
        matroska/KaxTrackVideo.h
        matroska/KaxTypes.h
        matroska/KaxVersion.h)

set(libmatroska_C_PUBLIC_HEADERS
        matroska/c/libmatroska.h
        matroska/c/libmatroska_t.h)

add_library(matroska SHARED ${libmatroska_SOURCES} ${limatroska_PUBLIC_HEADERS} ${libmatroska_C_PUBLIC_HEADERS})

target_link_libraries(matroska PUBLIC ebml)

set_target_properties(matroska PROPERTIES
        VERSION 6.0.0
        SOVERSION 6)

target_include_directories(matroska PUBLIC
        $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}>
        $<INSTALL_INTERFACE:${CMAKE_INSTALL_INCLUDEDIR}>
        )

if (MSVC)
    target_compile_definitions(matroska PRIVATE _CRT_SECURE_NO_WARNINGS)
endif ()