
add_executable(MakeTable MakeTable.cxx)
add_custom_command(
        # OUTPUT ${CMAKE_CURRENT_BINARY_DIR}/Table.h
        OUTPUT RANDOM_NAME
        COMMAND MakeTable ${CMAKE_CURRENT_BINARY_DIR}/Table.h
        DEPENDS MakeTable
)

add_library(MathFunctions
        mysqrt.cxx
        #${CMAKE_CURRENT_BINARY_DIR}/Table.h #let CMake know that mysqrt.cxx depends on the generated file Table.h
        RANDOM_NAME
        )


target_include_directories(MathFunctions
        INTERFACE ${CMAKE_CURRENT_SOURCE_DIR}
        PRIVATE ${CMAKE_CURRENT_BINARY_DIR}
        )


install(TARGETS MathFunctions DESTINATION lib)
install(FILES MathFunctions.h DESTINATION include)