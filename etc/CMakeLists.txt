install(FILES "ELProxy.conf"
  DESTINATION "${SYSCONF_INSTALL_DIR}"
  COMPONENT config
  )

if(UNIX)
  if(NOT APPLE)
    get_filename_component(FULL_BIN_INSTALL_DIR
      ${BIN_INSTALL_DIR} REALPATH BASE_DIR ${CMAKE_INSTALL_PREFIX})
    get_filename_component(FULL_SYSCONF_INSTALL_DIR
      ${SYSCONF_INSTALL_DIR} REALPATH BASE_DIR ${CMAKE_INSTALL_PREFIX})

    configure_file("${CMAKE_CURRENT_SOURCE_DIR}/openelp.service.in"
      "${CMAKE_CURRENT_BINARY_DIR}/openelp.service"
      @ONLY)

    install(FILES "${CMAKE_CURRENT_BINARY_DIR}/openelp.service"
      DESTINATION "${SYSTEMD_SERVICES_INSTALL_DIR}"
      COMPONENT systemd
      )
  endif()
endif()
