#target.symbol SimDataFormatsCrossingFrame
include_directories(${CMAKE_SOURCE_DIR}
${Boost_INCLUDE_DIR}
${Boost_INCLUDE_DIR}/python
${EIGEN_INCLUDE_DIR}/eigen3
${FMT_INCLUDE_DIR}
${GSL_INCLUDE_DIR}
${CMSMD5_INCLUDE_DIR}
${Python_INCLUDE_DIR}
${ROOT_INCLUDE_DIR}
${TBB_INCLUDE_DIRS}
${TINYXML2_INCLUDE_DIR}
${UUID_INCLUDE_DIR}
/usr/include
)

cms_rootdict(SimDataFormatsCrossingFrame src/classes.h src/classes_def.xml)

add_rootdict_rules(SimDataFormatsCrossingFrame)

add_library(SimDataFormatsCrossingFrame SHARED ${SimDataFormatsCrossingFrame_EXTRA_SOURCES}
  src/CrossingFramePlaybackInfoNew.cc
  )

set_target_properties(SimDataFormatsCrossingFrame PROPERTIES LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

 add_dependencies( ALL_LIBS SimDataFormatsCrossingFrame)

install( TARGETS SimDataFormatsCrossingFrame DESTINATION ${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_LIBDIR} EXPORT stitched::)

target_link_libraries(SimDataFormatsCrossingFrame PUBLIC
DataFormatsCommon
SimDataFormatsEncodedEventId
)

