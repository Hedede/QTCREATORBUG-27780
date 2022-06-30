cmake_minimum_required(VERSION 3.5)

project(QTCREATORBUG-27780)

find_package(Qt5LinguistTools)

set(ts_files "${CMAKE_CURRENT_SOURCE_DIR}/ts1.ts" "${CMAKE_CURRENT_SOURCE_DIR}/ts2.ts")
set(qm_file mega_qm.qm)
add_custom_target(mega_qm DEPENDS ${qm_file})
add_custom_command(
    OUTPUT ${qm_file}
    COMMAND ${Qt5_LRELEASE_EXECUTABLE}
    ARGS ${ts_files} -qm ${qm_file}
    DEPENDS ${ts_files}
    COMMAND_EXPAND_LISTS VERBATIM)
