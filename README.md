# Controle-de-Interrup-es-e-LEDs-WS2812-na-Raspberry-Pi-Pico-W

## Descrição do Projeto
Este projeto utiliza uma **Raspberry Pi Pico W** para controlar uma matriz de LEDs WS2812 e exibir números de 0 a 9. A exibição do número pode ser alterada através de dois botões de entrada (BUTTON_A e BUTTON_B), permitindo a navegação entre os valores. O LED vermelho (
LED_R) pisca a cada 200ms para indicar que o sistema está operando corretamente.

## Componentes Utilizados
- **Raspberry Pi Pico W**
- **Matriz de LEDs WS2812** (5x5, totalizando 25 LEDs)
- **Dois botões** para incremento e decremento do número exibido
- **LED vermelho** para indicar funcionamento

## Estrutura do Código
O projeto é dividido nos seguintes arquivos:

### 1. **`main.c`** (Arquivo principal)
Responsável por inicializar a Pico, configurar o hardware e controlar a exibição dos números.

### 2. **`frames.h`**
Contém a representação dos números de 0 a 9 na matriz de LEDs.

### 3. **`ws2812.pio.h`**
Arquivo que define as rotinas para controle dos LEDs WS2812 via PIO (Programável I/O).

## Funcionalidades
- Exibição dos números de 0 a 9 na matriz de LEDs.
- Uso do **DMA (Direct Memory Access)** para atualização eficiente da matriz.
- **Tratamento de debounce** nos botões para evitar leituras indesejadas.
- LED vermelho pisca a cada **200ms** para indicar funcionamento.
- **Botão A**: Incrementa o número exibido.
- **Botão B**: Decrementa o número exibido.

## Configuração do Hardware
### **Pinos utilizados:**
| Componente | Pino na Pico W |
|------------|--------------|
| Matriz WS2812 | GPIO7 |
| Botão A | GPIO5 |
| Botão B | GPIO6 |
| LED Vermelho | GPIO13 |

## Como Compilar e Rodar
### **1. Instale o Raspberry Pi Pico SDK**
Siga as instruções oficiais do SDK:
https://github.com/raspberrypi/pico-sdk

### **2. Clone este repositório**
```sh
    git clone https://github.com/GabrielSampa1o/Controle-de-Interrup-es-e-LEDs-WS2812-na-Raspberry-Pi-Pico-W.git
    cd Controle-de-Interrup-es-e-LEDs-WS2812-na-Raspberry
```

### **3. Abra o VS Code** e **importe o projeto**:
   - Vá até a **Extensão Raspberry Pi Pico**.
   - Selecione **Import Project**.
   - Escolha a pasta do repositório clonado.
   - Clique em **Import**.

### **4. Compilar o código**:
   - Utilize a opção de **Build** da extensão.

### **5. Carregue o binário na Pico**
1. Pressione e segure o **botão BOOTSEL** da Raspberry Pi Pico W.
2. Conecte-a ao PC via **USB**.
3. Copie o arquivo `.uf2` gerado para a unidade montada.

## Exemplo de Uso
1. A matriz de LEDs inicia apagada.
2. Pressionar **Botão A** exibe o próximo número.
3. Pressionar **Botão B** exibe o número anterior.
4. O LED vermelho pisca a cada 200ms para indicar funcionamento.


## Autor
- [Gabriel Silva Sampaio]
- [Vídeo de demonstração](https://github.com/seu-usuario)

