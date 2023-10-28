set(SOURCES
  main.cpp)

add_executable(mathexpr ${SOURCES})

target_link_libraries(mathexpr ${LLVM_LIBS})
add_library(mathexprlib STATIC ${SOURCES})

# Add additional definitions
IF (WIN32)
    ADD_DEFINITIONS(-DOS_WINDOWS)
ELSE()
    ADD_DEFINITIONS(-DOS_UNIX)
ENDIF()