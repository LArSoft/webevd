# webevd/ArtSupport/CMakeLists.txt
#
# David Adams
# September 2015
#
# CMake instructions for the AXServices library which holds
# helper classes for dealing with art services.
cet_make_library(SOURCE
  ArtServiceHelper.cxx
  LIBRARIES
  PUBLIC
  art::Framework_Services_Registry
  art::Utilities
  PRIVATE
  fhiclcpp::fhiclcpp
)

install_headers()
install_fhicl()
