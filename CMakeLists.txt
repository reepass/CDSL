############################################
#
# libcdsl uses cmake because it's simple
#   Build instructions can be found in the README
#
############################################

# Set some flags
cmake_minimum_required(VERSION 2.8.11)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c11")
set(CMAKE_BUILD_TYPE Debug)

# Create our project for further reference
project(libcdsl)

set(CDSL_SRC 
        lib/adeque.c
        lib/alist.c
        lib/aqueue.c
        lib/array2d.c
        lib/astack.c
        lib/binarytree.c
        lib/examples.c
        lib/hashtable.c
        lib/line.c
        lib/list.c
        lib/maxheap.c
        lib/minheap.c
        lib/queue.c
        lib/stack.c
        lib/transform.c
        lib/util.c
        lib/vector.c
)

# Define our library in cmake
add_library(libcdsl STATIC ${CDSL_SRC})

# Include the subdirectories to search for headers
target_include_directories(libcdsl PUBLIC "headers")
target_include_directories(libcdsl PRIVATE "lib")

# since the name starts with 'lib' dont add it again
set_target_properties(libcdsl PROPERTIES PREFIX "")
