# ======================================================================
#  webevd main build file
#
#  cd .../path/to/build/directory
#  source .../path/to/webevd/ups/setup_for_development <-d|-p>
#  buildtool [-I /install/path] -bt[i] -jN
# ======================================================================

cmake_minimum_required(VERSION 3.20 FATAL_ERROR)
# cmake_policy(VERSION 3.19) ### MIGRATE-ACTION-COMPATIBILITY (migrate-3.13.00) - Uncomment to preserve compatibility with older CMake versions

find_package(cetmodules REQUIRED)
project(webevd VERSION 09.08.09 LANGUAGES CXX)

# cetbuildtools contains our cmake modules

include(CetCMakeEnv)
cet_cmake_env()

cet_set_compiler_flags(DIAGS CAUTIOUS
  WERROR
  NO_UNDEFINED
  EXTRA_FLAGS -pedantic -Wno-unused-local-typedefs
)

cet_report_compiler_flags() ### MIGRATE-ACTION-RECOMMENDED (migrate-3.13.00) - add args: REPORT_THRESHOLD VERBOSE

find_package(cetlib_except REQUIRED EXPORT)
find_package(cetlib REQUIRED EXPORT)
find_package(canvas REQUIRED EXPORT)
find_package(canvas_root_io REQUIRED)
find_package(gallery REQUIRED EXPORT)
find_package(art REQUIRED EXPORT)
find_package(art_root_io REQUIRED EXPORT)
find_package(nusimdata REQUIRED EXPORT)
find_package(ROOT COMPONENTS Core REQUIRED EXPORT)
# these are minimum required versions, not the actual product versions
find_package( larcoreobj REQUIRED )
find_package( larcorealg REQUIRED )
find_package( larcore REQUIRED )
find_package( lardataobj REQUIRED )
find_package( lardataalg REQUIRED )
find_package( lardata REQUIRED )

# macros for dictionary and simple_plugin
include(ArtDictionary)
include(ArtMake)
include(BuildPlugins)


add_subdirectory(webevd)
add_subdirectory(test)

# packaging utility
cet_cmake_config()
