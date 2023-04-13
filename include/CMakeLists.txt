target_include_directories(${MAIN_TARGET_NAME} INTERFACE ${CMAKE_CURRENT_LIST_DIR})

target_sources(${MAIN_TARGET_NAME}
  PUBLIC FILE_SET HEADERS
    BASE_DIRS 
      ${CMAKE_CURRENT_LIST_DIR}
    FILES
      ${CMAKE_CURRENT_LIST_DIR}/constexpr_hash_map.hpp
)