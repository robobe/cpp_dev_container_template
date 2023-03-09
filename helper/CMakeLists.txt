set (SOURCES
    src/helper.cpp
)

add_library(helper ${SOURCES})
target_include_directories(helper PUBLIC include)