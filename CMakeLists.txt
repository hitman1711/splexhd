cmake_minimum_required( VERSION 3.8.2 )
project( splexhd )
file( GLOB SOURCES "src/*.cc" )
find_package( SDL REQUIRED )
find_package( OpenGL REQUIRED )
find_package( GLU REQUIRED )
find_package( PNG REQUIRED )
find_package( Freetype REQUIRED )
find_path( OGG_INCLUDE_DIR ogg/ogg.h )
find_path( VORBIS_INCLUDE_DIR vorbis/vorbisfile.h )
find_library( OGG_LIBRARY NAMES ogg )
find_library( VORBIS_LIBRARY NAMES vorbis )
find_library( VORBISFILE_LIBRARY NAMES vorbisfile )
include_directories(
        ${SDL_INCLUDE_DIR}
        ${OPENGL_INCLUDE_DIR}
        ${GLU_INCLUDE_DIR}
        ${PNG_INCLUDE_DIR}
        ${FREETYPE_INCLUDE_DIRS}
        ${OGG_INCLUDE_DIR}
        ${VORBIS_INCLUDE_DIR}
        ${VORBISFILE_INCLUDE_DIR}
)
add_executable( splexhd ${SOURCES} )
target_link_libraries(
        splexhd
        ${SDL_LIBRARY}
        ${OPENGL_LIBRARIES}
        ${GLU_LIBRARIES}
        ${PNG_LIBRARIES}
        ${FREETYPE_LIBRARIES}
        ${OGG_LIBRARY}
        ${VORBIS_LIBRARY}
        ${VORBISFILE_LIBRARY}
)