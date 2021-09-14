#多个
cmake_minimum_required(VERSION 3.0.0)
project(ch01 VERSION 0.1.0)

include_directories("${PROJECT_BINARY_DIR}")

# Find all main*.cpp files and store in list mains
file(GLOB_RECURSE mains RELATIVE  #递归的查找cc文件,不需要写明白路径
"${CMAKE_CURRENT_SOURCE_DIR}"
# "${CMAKE_CURRENT_SOURCE_DIR}/for_ex.cc"
# "${CMAKE_CURRENT_SOURCE_DIR}/add.cc"
"${CMAKE_CURRENT_SOURCE_DIR}/add_item.cc"
"${CMAKE_CURRENT_SOURCE_DIR}/add_item2.cc"
"${CMAKE_CURRENT_SOURCE_DIR}/avg_price.cc"
"${CMAKE_CURRENT_SOURCE_DIR}/item_io.cc"


)

foreach(mainfile IN LISTS mains)# for item in ["xx/xx.cc","xx/xxx.cc"]
    # Get file name without directory
    set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${PROJECT_SOURCE_DIR}/bin)
    get_filename_component(mainname ${mainfile} NAME_WE)#
    add_executable(${mainname} ${mainfile})
    message("-> compiling "${mainfile})
endforeach()

include_directories(ch01
    PRIVATE 
        ${PROJECT_SOURCE_DIR}/include
)