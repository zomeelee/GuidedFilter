include_directories ( ${CLUtils_INCLUDE_DIR} )

add_library ( GFAlgorithms STATIC GuidedFilter/algorithms.cpp )
add_library ( GFMath STATIC GuidedFilter/math.cpp )
add_library ( GFHelperFuncs STATIC GuidedFilter/tests/helper_funcs.cpp )

add_dependencies ( GFAlgorithms CLUtils )
add_dependencies ( GFMath CLUtils )
add_dependencies ( GFHelperFuncs CLUtils )

target_include_directories ( 
    GFAlgorithms PUBLIC 
    ${COMMON_INCLUDES} 
)

target_include_directories ( 
    GFMath PUBLIC 
    ${COMMON_INCLUDES} 
)

target_include_directories ( 
    GFHelperFuncs PUBLIC 
    ${COMMON_INCLUDES} 
)

target_link_libraries (
    GFAlgorithms LINK_PUBLIC 
    GFMath
)

install ( DIRECTORY ${PROJECT_SOURCE_DIR}/include/ DESTINATION include )
install ( DIRECTORY ${PROJECT_BINARY_DIR}/lib/ DESTINATION lib/GuidedFilter )
