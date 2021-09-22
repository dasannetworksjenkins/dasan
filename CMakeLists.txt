cmake_minimum_required(VERSION 3.14)

project(gtest_Test VERSION 1.0)


if (NOT googletest)
        include(FetchContent)
        FetchContent_Declare(
                googletest
                        # Specify the commit you depend on and update it regularly.
                        URL https://github.com/google/googletest/archive/609281088cfefc76f9d0ce82e1ff6c30cc3591e5.zip
                        # Change to actual retpsitory if you want
                        #URL https://github.com/google/googletest/archive/refs/heads/master.zip
        )
        # For Windows: Prevent overriding the parent project's compiler/linker settings
        set(gtest_force_shared_crt ON CACHE BOOL "" FORCE)
        FetchContent_MakeAvailable(googletest)
endif()


# Now simply link against gtest or gtest_main as needed. Eg
add_executable(${PROJECT_NAME} test.cpp)
target_link_libraries(${PROJECT_NAME} gtest_main)
add_test(NAME example_test COMMAND ${PROJECT_NAME})

