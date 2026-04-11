add_library(thread_pool STATIC)
target_sources(thread_pool PUBLIC FILE_SET CXX_MODULES FILES ${CMAKE_CURRENT_SOURCE_DIR}/BS.thread_pool.cppm)
target_include_directories(thread_pool PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})

include(GNUInstallDirs)
install(
    TARGETS thread_pool
    ARCHIVE DESTINATION ${CMAKE_INSTALL_LIBDIR}
    CXX_MODULES_BMI DESTINATION ${CMAKE_INSTALL_LIBDIR}/cxx/bmi
)
configure_file(${CMAKE_SOURCE_DIR}/packaging/thread_pool.pc.in thread_pool.pc @ONLY)
install(
    FILES ${CMAKE_CURRENT_BINARY_DIR}/thread_pool.pc
    DESTINATION ${CMAKE_INSTALL_LIBDIR}/pkgconfig
)
