cmake_minimum_required(VERSION 3.16)

set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTOUIC ON)
set(CMAKE_AUTORCC ON)

find_package(Qt5 REQUIRED COMPONENTS Widgets OpenGL)
find_package(OpenGL REQUIRED)
find_package(ZLIB REQUIRED)

add_executable(brdf
    BRDFAnalytic.cpp
    BRDFBase.cpp
    BRDFImageSlice.cpp
    BRDFMeasuredAniso.cpp
    BRDFMeasuredMERL.cpp
    ColorVarWidget.cpp
    DGLFrameBuffer.cpp
    DGLShader.cpp
    IBLWidget.cpp
    IBLWindow.cpp
    ImageSliceWidget.cpp
    ImageSliceWindow.cpp
    FloatVarWidget.cpp
    LitSphereWindow.cpp
    main.cpp
    glerror.cpp
    MainWindow.cpp
    ViewerWindow.cpp
    ParameterGroupWidget.cpp
    ParameterWindow.cpp
    SharedContextGLWidget.cpp
    ShowingDockWidget.cpp
    PlotCartesianWindow.cpp
    PlotCartesianWidget.cpp
    PlotPolarWidget.cpp
    Plot3DWidget.cpp
    LitSphereWidget.cpp
    SimpleModel.cpp
    Paths.cpp
    Quad.cpp
    Sphere.cpp
    ptex/PtexReader.cpp
    ptex/PtexUtils.cpp
    ptex/PtexCache.cpp
    ptex/PtexHalf.cpp
)

target_compile_definitions(brdf PRIVATE PTEX_STATIC NOMINMAX)

target_include_directories(brdf PRIVATE
    ${CMAKE_CURRENT_SOURCE_DIR}
    ${CMAKE_CURRENT_SOURCE_DIR}/ptex
    ${CMAKE_CURRENT_SOURCE_DIR}/glm
)

target_link_libraries(brdf PRIVATE
    Qt5::Widgets
    Qt5::OpenGL
    OpenGL::GL
    ZLIB::ZLIB
)

if(APPLE)
    set_target_properties(brdf PROPERTIES MACOSX_BUNDLE OFF)
endif()

install(TARGETS brdf
    RUNTIME DESTINATION ${CMAKE_INSTALL_BINDIR}
)

install(DIRECTORY ../brdfs/ DESTINATION share/brdf/brdfs)
install(DIRECTORY ../data/ DESTINATION share/brdf/data)
install(DIRECTORY ../images/ DESTINATION share/brdf/images)
install(DIRECTORY ../probes/ DESTINATION share/brdf/probes)
install(DIRECTORY ../shaderTemplates/ DESTINATION share/brdf/shaderTemplates)

install(FILES brdf.pc DESTINATION ${CMAKE_INSTALL_LIBDIR}/pkgconfig)
