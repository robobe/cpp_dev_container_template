set(TEST_BINARY ${PROJECT_NAME}_test)
add_executable(${TEST_BINARY} test_app.cpp)
target_link_libraries(${TEST_BINARY}
    helper
    gtest
    gtest_main
)