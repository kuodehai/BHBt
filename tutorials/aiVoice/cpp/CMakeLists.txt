message(STATUS "tutorials: ${CMAKE_CURRENT_SOURCE_DIR}")

file(GLOB_RECURSE BTUNITTEST_SRC  "${CMAKE_CURRENT_SOURCE_DIR}/*.cpp")
file(GLOB_RECURSE BTUNITTEST_INC  "${CMAKE_CURRENT_SOURCE_DIR}/*.h")

# add the binary tree to the search path for include files
# so that we will find TutorialConfig.h
include_directories("${PROJECT_SOURCE_DIR}/inc")
include_directories(${CMAKE_CURRENT_SOURCE_DIR})

# set(BTUNITTEST_SRC_INC ${BTUNITTEST_SRC} ${BTUNITTEST_INC})

# add the executable
add_executable(aiVoice ${BTUNITTEST_INC} ${BTUNITTEST_SRC})

target_link_libraries (aiVoice libbehaviac ${CMAKE_THREAD_LIBS_INIT})

set_target_properties(aiVoice PROPERTIES PREFIX "")
# set_target_properties(aiVoice PROPERTIES OUTPUT_NAME_DEBUG libbehaviac${${CMAKE_DEBUG_POSTFIX}}
# set_target_properties(aiVoice PROPERTIES OUTPUT_NAME_RELEASE libbehaviac${${CMAKE_RELEASE_POSTFIX}}
set_target_properties(aiVoice PROPERTIES DEBUG_POSTFIX ${CMAKE_DEBUG_POSTFIX})
set_target_properties(aiVoice PROPERTIES RELEASE_POSTFIX ${CMAKE_RELEASE_POSTFIX})
