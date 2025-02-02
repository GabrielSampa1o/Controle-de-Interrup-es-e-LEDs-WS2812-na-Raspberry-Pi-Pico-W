# == DO NOT EDIT THE FOLLOWING LINES for the Raspberry Pi Pico VS Code Extension to work ==
if(WIN32)
    set(USERHOME $ENV{USERPROFILE})
else()
    set(USERHOME $ENV{HOME})
endif()
set(sdkVersion 2.1.0)
set(toolchainVersion 13_3_Rel1)
set(picotoolVersion 2.1.0)
set(picoVscode ${USERHOME}/.pico-sdk/cmake/pico-vscode.cmake)
if (EXISTS ${picoVscode})
    include(${picoVscode})
endif()
# ====================================================================================

cmake_minimum_required(VERSION 3.13)

set(CMAKE_C_STANDARD 11)
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

# Define a placa Pico W
set(PICO_BOARD pico_w CACHE STRING "Board type")

# Puxa o Raspberry Pi Pico SDK (deve ser antes do `project()`)
include(pico_sdk_import.cmake)

# Define o projeto
project(interrupcoes C CXX ASM)

# Inicializa o Raspberry Pi Pico SDK
pico_sdk_init()

# Adiciona o executável
add_executable(interrupcoes interrupcoes.c)

# Define o nome e versão do programa
pico_set_program_name(interrupcoes "interrupcoes")
pico_set_program_version(interrupcoes "0.1")

# Se estiver usando um arquivo PIO, descomente e certifique-se de que ele existe:
 pico_generate_pio_header(interrupcoes ${CMAKE_CURRENT_LIST_DIR}/blink.pio)

# Habilita ou desabilita a saída via USB/UART
pico_enable_stdio_uart(interrupcoes 1)  # Ativado
pico_enable_stdio_usb(interrupcoes 0)   # Desativado

# Adiciona a biblioteca padrão
target_link_libraries(interrupcoes pico_stdlib)

# Inclui os diretórios necessários
target_include_directories(interrupcoes PRIVATE ${CMAKE_CURRENT_LIST_DIR})

# Adiciona as bibliotecas do hardware necessárias
target_link_libraries(interrupcoes 
    hardware_dma
    hardware_pio
    hardware_timer
)

# Gera arquivos binários extras (UF2, ELF, BIN)
pico_add_extra_outputs(interrupcoes)
