add_executable(${MAIN_TARGET_NAME}Test)

target_link_libraries(${MAIN_TARGET_NAME}Test ${MAIN_TARGET_NAME})

target_sources(${MAIN_TARGET_NAME}Test
  PRIVATE
    ${CMAKE_CURRENT_LIST_DIR}/main.cpp
)

install(TARGETS ${MAIN_TARGET_NAME}Test)