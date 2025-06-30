find_package(Python3 REQUIRED COMPONENTS Interpreter Development)
include_directories(${CMAKE_CURRENT_SOURCE_DIR})
include_directories(${Python3_INCLUDE_DIRS}) # Add this line

message(STATUS "Python3_LIBRARIES findme: ${Python3_LIBRARIES}")
if (CYTHON_FOUND)
    cython_add_module(connector
        connector.pxd
        connector.pyx
    )
    target_link_libraries( connector Python3::Module ) # Modify this line
install(TARGETS connector
    RUNTIME DESTINATION bin
    LIBRARY DESTINATION ${PYTHON_SITE_INSTALL_DIR}
    )

endif()
