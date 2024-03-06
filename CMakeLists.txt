set(LIB segger-rtt)

file(GLOB_RECURSE LIB_SRCS CONFIGURE_DEPENDS ${CMAKE_CURRENT_LIST_DIR}/RTT/*.c)
set(LIB_SRCS ${LIB_SRCS} ${CMAKE_CURRENT_LIST_DIR}/Syscalls/SEGGER_RTT_Syscalls_GCC.c ${CMAKE_CURRENT_LIST_DIR}/RTT/SEGGER_RTT_ASM_ARMv7M.S)

add_library(${LIB} STATIC ${LIB_SRCS})
set_target_properties(${LIB} PROPERTIES COMPILE_FLAGS -w)

target_compile_definitions(${LIB} PRIVATE RTT_USE_ASM=1)
target_include_directories(${LIB}
                           SYSTEM PUBLIC
                           ${CMAKE_CURRENT_LIST_DIR}/RTT
                           ${CMAKE_CURRENT_LIST_DIR}/Config
                           )
