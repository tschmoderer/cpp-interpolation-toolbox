add_executable(test_interp1d test_interp1d.cpp)
target_link_libraries(test_interp1d LINK_PUBLIC linalg)
target_link_libraries(test_interp1d LINK_PUBLIC interpol)

add_test(test_interp1d test_interp1d)

if (NOT TARGET memcheck)
add_custom_target(memcheck
    COMMAND ${CMAKE_CTEST_COMMAND} 
        --force-new-ctest-process --test-action memcheck
    COMMAND cat "${CMAKE_BINARY_DIR}/Testing/Temporary/MemoryChecker.*.log"
    WORKING_DIRECTORY "${CMAKE_BINARY_DIR}")
endif()
