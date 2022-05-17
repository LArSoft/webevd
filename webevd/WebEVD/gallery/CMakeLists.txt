cet_make_exec(webevd SOURCE webevd.cxx
  LIBRARIES PRIVATE
  webevd::WebEVD
  webevd::ThreadsafeGalleryEvent
  webevd::ArtSupport
  lardata::DetectorPropertiesService
  larcore::Geometry_Geometry_service
  gallery::gallery
  art::Framework_Services_Registry
  canvas::canvas
)

install_headers()
install_source()
