# Copyright (C) 2015-2017 Bayerische Motoren Werke Aktiengesellschaft (BMW AG)
# This Source Code Form is subject to the terms of the Mozilla Public
# License, v. 2.0. If a copy of the MPL was not distributed with this
# file, You can obtain one at http://mozilla.org/MPL/2.0/.

cmake_minimum_required (VERSION 2.8)

project(SUB_AND_PUB_TEST)

set (VSOMEIP_NAME vsomeip3)

set(CMAKE_THREAD_LIBS_INIT "-lpthread")

add_executable(subscribe-sample subscribe-sample.cpp)
target_link_libraries(subscribe-sample ${VSOMEIP_NAME} ${Boost_LIBRARIES} ${DL_LIBRARY} ${CMAKE_THREAD_LIBS_INIT})

add_executable(notify-sample notify-sample.cpp)
target_link_libraries(notify-sample ${VSOMEIP_NAME} ${Boost_LIBRARIES} ${DL_LIBRARY} ${CMAKE_THREAD_LIBS_INIT})

add_dependencies(subscribe-sample notify-sample)

install (
    TARGETS subscribe-sample notify-sample
    RUNTIME DESTINATION "${INSTALL_BIN_DIR}" COMPONENT bin
)

###################################################################################################
