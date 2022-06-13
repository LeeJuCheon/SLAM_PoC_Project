# Test sources
set(IMAGEPROJECTOR_TEST_SRCS
        ImageProjector
        )

# Include
include_directories(
        ${IMAGEPROJECTOR_INCLUDE_PATH}
)

# Targets
add_executable(ImageProjector_test
        main.cpp
        ${IMAGEPROJECTOR_TEST_SRCS}.cpp
        )

target_link_libraries(ImageProjector_test
        ${GTEST_LIBS}
        ImageProjector
        stdc++fs
        )

add_test(NAME ImageProjectorTest COMMAND
        ${CMAKE_CURRENT_BINARY_DIR}/ImageProjector_test)

set(matchString "/")
set(replaceWith "_")

# foreach(test ${IMAGEPROJECTOR_TEST_SRCS})
#     string(REPLACE ${matchString} ${replaceWith} test_name ${test})
#     set(test_name ${test_name})

#     add_executable(${test_name}
#             main.cpp
#             ${test}.cpp)
#     target_link_libraries(${test_name}
#             ${GTEST_LIBS}
#             IMAGEPROJECTOR
#             stdc++fs
#             )
#     add_test(${test_name}
#             ${test_name}
#             --gtest_color=yes
#             )
# endforeach()