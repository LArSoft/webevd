# ======================================================================
#  webevd main build file
#
#  cd .../path/to/build/directory
#  source .../path/to/webevd/ups/setup_for_development <-d|-p>
#  buildtool [-I /install/path] -bt[i] -jN
# ======================================================================

cmake_minimum_required(VERSION 3.19 FATAL_ERROR)

project(webevd VERSION 09.08.08 LANGUAGES CXX)

# cetbuildtools contains our cmake modules
find_package(cetbuildtools REQUIRED)

include(CetCMakeEnv)
cet_cmake_env()

cet_set_compiler_flags(DIAGS CAUTIOUS
  WERROR
  NO_UNDEFINED
  EXTRA_FLAGS -pedantic -Wno-unused-local-typedefs
)

cet_report_compiler_flags()

find_package(cetlib_except REQUIRED PUBLIC)
find_package(cetlib REQUIRED PUBLIC)
find_package(canvas REQUIRED PUBLIC)
find_package(canvas_root_io REQUIRED)
find_package(gallery REQUIRED PUBLIC)
find_package(art REQUIRED PUBLIC)
find_package(art_root_io REQUIRED PUBLIC)
find_package(nusimdata REQUIRED PUBLIC)
find_package(ROOT COMPONENTS Core REQUIRED PUBLIC)
# these are minimum required versions, not the actual product versions
find_ups_product( larcoreobj )
find_ups_product( larcorealg )
find_ups_product( larcore )
find_ups_product( lardataobj )
find_ups_product( lardataalg )
find_ups_product( lardata )

# macros for dictionary and simple_plugin
include(ArtDictionary)
include(ArtMake)
include(BuildPlugins)


add_subdirectory(webevd)
add_subdirectory(test)
add_subdirectory(ups)

# packaging utility
include(UseCPack)
