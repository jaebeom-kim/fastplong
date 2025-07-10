add_library(nedmalloc nedmalloc.c)
# set_target_properties(nedmalloc
#         PROPERTIES
#                 COMPILE_FLAGS "-DREPLACE_SYSTEM_ALLOCATOR -DWIN32 -DNO_MALLINFO=1"
#                 LINK_FLAGS "-DREPLACE_SYSTEM_ALLOCATOR -DWIN32 -DNO_MALLINFO=1")
if (WIN32)
  set(win_def -DWIN32)
else()
  set(win_def "")
endif()

set(common_defs "-DREPLACE_SYSTEM_ALLOCATOR ${win_def} -DNO_MALLINFO=1 ${MMSEQS_CXX_FLAGS} -w")
set_target_properties(nedmalloc PROPERTIES
  COMPILE_FLAGS "${common_defs}"
  LINK_FLAGS    "${common_defs}"
)
                