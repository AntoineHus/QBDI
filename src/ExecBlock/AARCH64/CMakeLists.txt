# Add QBDI target
set(SOURCES "${CMAKE_CURRENT_LIST_DIR}/ExecBlock_AARCH64.cpp")

if(QBDI_PLATFORM_LINUX OR QBDI_PLATFORM_ANDROID)
  list(APPEND SOURCES "${CMAKE_CURRENT_LIST_DIR}/linux-android-AARCH64.s")
elseif(QBDI_PLATFORM_OSX)
  list(APPEND SOURCES "${CMAKE_CURRENT_LIST_DIR}/osx-AARCH64.s")

  #elseif(QBDI_PLATFORM_IOS)
  #  list(APPEND SOURCES ${CMAKE_CURRENT_LIST_DIR}/ios-AARCH64.s)

else()
  message(FATAL_ERROR "No stub for ${QBDI_PLATFORM} (${QBDI_ARCH})")
endif()

target_sources(QBDI_src INTERFACE "${SOURCES}")
