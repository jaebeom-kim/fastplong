add_library(nedmalloc nedmalloc.c)
set_target_properties(nedmalloc
        PROPERTIES
                COMPILE_FLAGS "-DREPLACE_SYSTEM_ALLOCATOR -DWIN32 -DNO_MALLINFO=1"
                LINK_FLAGS "-DREPLACE_SYSTEM_ALLOCATOR -DWIN32 -DNO_MALLINFO=1")