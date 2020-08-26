# Processamento de Sinal Impulsivo - Detecção de tiros

## Motivação
A ideia do projeto é reduzir drasticamente os custos de um projeto já feito anteriormente com o myRIO da National Instruments, de forma a viabilizar a produção de aparelhos que identifiquem sinais impulsivos em tempo real (disparos de armas de fogo, gritos etc).

## Escopo do Projeto 
Inicialmente pretendemos utilizar a biblioteca de Processamento Digital de Sinais para adquirir e interpretar os dados pelo microfone da STM32 F4 Discovery. Depois, vamos implementar o processamento do sinal adquirido pelo método GCC-PHAT (Generalized Cross Correlation Phase Transform).

Não entraremos em um valor ótimo de treshold para identificarmos corretamente o sinal. Somente faremos a aquisição e processamento com um sinal de referência armazenado em um array.

Com esse sinal de referência, aplicamos o GCC e pegamos o pico de correlação com o sinal de entrada. Se este valor extrapolar um limite setado, consideraremos o sinal de entrada semelhante (do mesmo tipo) do sinal de referência.

Uma apresentação breve do projeto realizado em LabVIEW pode ser observado nos assets deste repositório, com link abaixo.

Link: https://github.com/Microcontroladores-2020/Shiraga_ProcessamentoSom/blob/master/assets/IME%20GDS.pdf

## Periféricos utilizados
Para a realização do projeto foi utilizado um microcontrolador STM32 F429 do Discovery kit, a qual já possui um microfone.
![stm32f429-discovery-kit](https://github.com/Microcontroladores-2020/Shiraga_ProcessamentoSom/blob/master/assets/stm32f429-discovery-kit.jpg)

## Programa e guias utilizados
### Programa
STM32Cube IDE foi a interface de desenvolvimento escolhida.

### Guias e links úteis
1. Biblioteca de processamento digital de sinais (DSP) stm32f4 discovery: http://stm32f4-discovery.net/tag/dsp/;
2. Tutorial I2C Audio Codec: https://www.youtube.com/watch?v=QIPQOnVablY&pp=qAMBugMGCgJwdBAB;
3. Tutorial de algoritmos DSP com stm32f4 discovery: https://www.embarcados.com.br/algoritmos-dsp-stm32f4discovery-parte1/;
4. Drive/bizu com alguns projetos de DSP: https://drive.google.com/file/d/0ByfGO_ITCy2tc0lmOFNaNko1YXM/edit.

## Diagrama / Tabela de Pinagem
Também seguindo os tutoriais encontrados, usamos o seguinte Diagrama e Tabela de Pinagem:
![pinagem]https://github.com/Microcontroladores-2020/Shiraga_ProcessamentoSom/blob/master/assets/pinagem.png

Com as seguintes funcionalidades (tabela de pinagem):

| Pinos         | Função         | 
| ------------- |:--------------:| 
|      PH0      |   RCC_OSC_IN   | 
|      PH1      |   RCC_OSC_OUT  |  
|      PD12     |   GPIO_Output  |
|      PD13     |   GPIO_Output  |
|      PD14     |   GPIO_Output  |
|      PD15     |   GPIO_Output  |
|      PC7      |   I253_MCK     |
|      PC10     |   I253_CK      |
|      PC12     |   I253_SD      |
|      PB6      |   I2C1_SCL     |
|      PB9      |   I2C1_SDA     |
|      PA4      |   I253_W       |


## Fluxo de funcionamento do projeto (Firmware)
Seguindo a referência encontrada nos tutoriais, utilizamos o fluxo descrito 
![fluxo_dsp_basico](https://github.com/Microcontroladores-2020/Shiraga_ProcessamentoSom/blob/master/assets/fluxo_dsp_basico.png)
