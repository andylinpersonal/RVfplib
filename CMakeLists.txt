file(GLOB SRCS "src/asm/ieee754/**.*")

idf_component_register(
    SRCS
        "${SRCS}"
    LDFRAGMENTS
        "linker.lf"
)

if(CONFIG_RVFPLIB_OPTIMIZATION_SIZE)
    idf_build_set_property(COMPILE_DEFINITIONS "SIZE=1" APPEND)
else()
    idf_build_set_property(COMPILE_DEFINITIONS "PERFORMANCE=1" APPEND)
endif()
