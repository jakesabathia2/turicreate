project(annotation_test)


make_library(annotation_test_utils
  SOURCES
    utils.cpp
  REQUIRES
    unity_shared_for_testing
)

if(${TC_BUILD_REMOTEFS})

make_boost_test(image_classifier_tests.cxx
  REQUIRES
    annotation_test_utils
  COMPILE_FLAGS_EXTRA_GCC
    -Wno-unknown-pragmas  # NOTE: used for auto-generated protobuf source files
    -Wno-unused-function  # NOTE: used for auto-generated protobuf source files
)

if (APPLE)
  make_boost_test(utils_tests.cxx
    REQUIRES
      annotation_test_utils
    COMPILE_FLAGS_EXTRA_GCC
      -Wno-unknown-pragmas  # NOTE: used for auto-generated protobuf source files
      -Wno-unused-function  # NOTE: used for auto-generated protobuf source files
  )
endif()

endif()


make_boost_test(object_detector_tests.cxx
  REQUIRES
    annotation_test_utils
  COMPILE_FLAGS_EXTRA_GCC
    -Wno-unknown-pragmas  # NOTE: used for auto-generated protobuf source files
    -Wno-unused-function  # NOTE: used for auto-generated protobuf source files
)

