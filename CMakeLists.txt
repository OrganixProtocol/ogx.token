add_contract(ogx.token ogx.token ${CMAKE_CURRENT_SOURCE_DIR}/src/ogx.token.cpp)

target_include_directories(ogx.token
   PUBLIC
   ${CMAKE_CURRENT_SOURCE_DIR}/include)

set_target_properties(ogx.token
   PROPERTIES
   RUNTIME_OUTPUT_DIRECTORY "${CMAKE_CURRENT_BINARY_DIR}")

configure_file( ${CMAKE_CURRENT_SOURCE_DIR}/ricardian/ogx.token.contracts.md.in ${CMAKE_CURRENT_BINARY_DIR}/ricardian/ogx.token.contracts.md @ONLY )

target_compile_options( ogx.token PUBLIC -R${CMAKE_CURRENT_SOURCE_DIR}/ricardian -R${CMAKE_CURRENT_BINARY_DIR}/ricardian )
