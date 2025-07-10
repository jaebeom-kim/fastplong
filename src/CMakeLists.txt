# include_directories(fastplong)
# include_directories(../lib/libdeflate)
# include_directories(../lib/libisal)
# include_directories(../lib/libhwy)

# 

# add_executable(fastplong
#         ${fastplong_source_files}
# )

# target_include_directories(fastplong
#     PRIVATE ${PROJECT_SOURCE_DIR}/src
#     PRIVATE ${PROJECT_SOURCE_DIR}/src/fastplong
#     PRIVATE ${PROJECT_SOURCE_DIR}/lib/libdeflate
#     PRIVATE ${PROJECT_SOURCE_DIR}/lib/libisal
#     PRIVATE ${PROJECT_SOURCE_DIR}/lib/libhwy
# )

add_subdirectory(fastplong)

add_executable(fastplong
    ${fastplong_source_files}
)

target_link_libraries(fastplong 
    PRIVATE isal
    PRIVATE libdeflate_static
    PRIVATE hwy
    PRIVATE nedmalloc
)

target_include_directories(fastplong
  PRIVATE 
    $<BUILD_INTERFACE:${PROJECT_SOURCE_DIR}/src>
    $<BUILD_INTERFACE:${PROJECT_SOURCE_DIR}/src/fastplong>
)


set_target_properties(fastplong PROPERTIES
  RUNTIME_OUTPUT_DIRECTORY "${CMAKE_BINARY_DIR}/bin"
)