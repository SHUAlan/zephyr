if(CONFIG_NET_L2_BT OR
    CONFIG_NET_L2_BT_SHELL OR
    CONFIG_NET_L2_DUMMY)

  zephyr_library()
  zephyr_library_include_directories(. ..)
  zephyr_library_compile_definitions_ifdef(
    CONFIG_NEWLIB_LIBC __LINUX_ERRNO_EXTENSIONS__
    )

  zephyr_library_sources_ifdef(CONFIG_NET_L2_BT       bluetooth.c)
  zephyr_library_sources_ifdef(CONFIG_NET_L2_BT_SHELL bluetooth_shell.c)
  zephyr_library_sources_ifdef(CONFIG_NET_L2_DUMMY    dummy.c)

endif()

if(CONFIG_NET_L2_ETHERNET)
  add_subdirectory(ethernet)
endif()

if(CONFIG_NET_L2_IEEE802154)
  add_subdirectory(ieee802154)
endif()

if(CONFIG_NET_L2_OPENTHREAD)
  add_subdirectory(openthread)
endif()
