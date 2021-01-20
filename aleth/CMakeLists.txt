set(
    sources
    AccountManager.cpp AccountManager.h
    main.cpp
    MinerAux.cpp MinerAux.h
)

add_library(aleth SHARED ${sources})
target_link_libraries(
    aleth
    PRIVATE ethereum ethashseal evm web3jsonrpc webthree devcore Boost::program_options
)

target_include_directories(aleth PRIVATE ../utils)

if(MINIUPNPC)
    target_compile_definitions(aleth PRIVATE ETH_MINIUPNPC)
endif()

install(TARGETS aleth DESTINATION bin)
