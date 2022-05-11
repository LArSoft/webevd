# webevd/ArtSupport/CMakeLists.txt
#
# David Adams
# September 2015
#
# CMake instructions for the AXServices library which holds
# helper classes for dealing with art services.

art_make(
  LIB_LIBRARIES
    art_Framework_EventProcessor
    art::Framework_Services_Registry
    art::Utilities
    canvas::canvas
    fhiclcpp
    cetlib::cetlib
    cetlib_except::cetlib_except
    ROOT::Core
) ### MIGRATE-ACTION-RECOMMENDED (migrate-3.13.00) - deprecated: use art_make_library(), art_dictonary(), and cet_build_plugin() with explicit source lists and plugin base types

install_headers()
install_fhicl()
