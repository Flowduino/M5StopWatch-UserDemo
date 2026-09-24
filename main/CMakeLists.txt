file(GLOB_RECURSE MY_SRCS
    "apps/*.c"
    "apps/*.cc"
    "apps/*.cpp"
    "assets/*.c"
    "assets/*.cc"
    "assets/*.cpp"
    "hal/*.c"
    "hal/*.cc"
    "hal/*.cpp"
)

set(MY_INCS
    "."
)

# FluidBox is a real-time particle solver. Its standalone StopWatch build uses
# -O2 deliberately; keep that optimization for the solver without changing the
# optimization policy of the rest of the factory demo.
set_source_files_properties(
    "${CMAKE_CURRENT_SOURCE_DIR}/apps/app_fluidbox/FluidBox.cpp"
    PROPERTIES COMPILE_OPTIONS "-O2"
)

idf_component_register(
    SRCS 
        "main.cpp"
        ${MY_SRCS}
    INCLUDE_DIRS 
        ${MY_INCS}
    EMBED_FILES
        "assets/sfx/boot_sfx.bin"
    EMBED_TXTFILES
        "hal/utils/config_ap/assets/badge_config_ap.html"
)
