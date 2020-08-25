# Processamento de Sinal Impulsivo - Detecção de tiros

## Motivação
A ideia do projeto é reduzir drasticamente os custos de um projeto já feito anteriormente com o myRIO da National Instruments, de forma a viabilizar a produção de aparelhos que identifiquem sinais impulsivos em tempo real (disparos de armas de fogo, gritos etc).

## Escopo do Projeto 
Inicialmente pretendemos utilizar a biblioteca de Processamento Digital de Sinais para adquirir e interpretar os dados pelo microfone da STM32 F4 Discovery. Depois, vamos implementar o processamento do sinal adquirido pelo método GCC-PHAT (Generalized Cross Correlation Phase Transform).
Não entraremos em um valor ótimo de treshold para identificarmos corretamente o sinal. Somente faremos a aquisição e processamento com um sinal de referência armazenado em um array.

## Periféricos utilizados
Para a realização do projeto foi utilizado:
1. Controlador STM32 F429;
![STM32 F429]
