# Load man_MANS from shared file
#
# SPDX-License-Identifier: curl
# License-Filename: COPYING
#
transform_makefile_inc("Makefile.inc" "${CMAKE_CURRENT_BINARY_DIR}/Makefile.inc.cmake")
include("${CMAKE_CURRENT_BINARY_DIR}/Makefile.inc.cmake")

add_manual_pages(man_MANS)

string(REPLACE ".3" ".html" HTMLPAGES "${man_MANS}")
string(REPLACE ".3" ".pdf" PDFPAGES "${man_MANS}")
add_custom_target(opts-html DEPENDS ${HTMLPAGES})
add_custom_target(opts-pdf DEPENDS ${PDFPAGES})
add_dependencies(html opts-html)
add_dependencies(pdf opts-pdf)
