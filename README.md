# Monitoramento de Condições de Pneus para Carros de Fórmula E

## Colaboradores

- Iago Kutelak - RM: 554698
- João Vicente - RM: 556561
- Lucca Saraiva Borges - RM: 554608
- Pietro Vitor Pezzente - RM: 557283

## Descrição do Problema e Solução

O monitoramento das condições dos pneus é crucial em corridas de carros de Fórmula E para garantir a segurança dos pilotos e o desempenho dos veículos. Este projeto visa criar um sistema de monitoramento que detecta a temperatura e a pressão dos pneus em tempo real, fornecendo alertas visuais e sonoros em caso de condições inadequadas. Isso ajuda a prevenir acidentes e otimizar o desempenho durante as corridas.

## Componentes Utilizados

- Arduino Uno
- Sensor de Pressão
- Sensor de Temperatura
- LED Vermelho
- LED Amarelo
- LED Verde
- Buzzer
- 3 Resistores de 220 Ohms
- 1 resistor de 1 KOhm
- 13 Jumpers

## Objetivo

O objetivo deste projeto é desenvolver um sistema de monitoramento para os pneus de carros de Fórmula E, que alerta os pilotos sobre condições de temperatura e pressão inadequadas dos pneus, garantindo a segurança e o desempenho durante as corridas.

## Funcionamento do Código

- Configuração dos pinos dos componentes e inicialização da comunicação serial.
- Leitura da pressão e conversão para PSI.
- Leitura da temperatura e conversão para Celsius.
- Verificação das condições de alerta e acionamento dos LEDs e do buzzer.
- O LED verde indica condições normais, o LED amarelo indica alerta intermediário e o LED vermelho indica condições críticas.
- O buzzer emite um som de alerta em caso de condições críticas.
- O código é executado em loop, monitorando continuamente as condições dos pneus.

## Imagem de Exemplo

[Adicione uma imagem ou link para uma demonstração visual do projeto, se aplicável.]

## Link Tinkercad

Você pode acessar o nosso projeto e simulação aqui: [Link para o projeto no Tinkercad]

## Conclusão

Este projeto demonstra como utilizar Arduino e sensores para criar um sistema de monitoramento eficaz para os pneus de carros de Fórmula E. Com este sistema, os pilotos podem tomar medidas proativas para garantir a segurança e o desempenho durante as corridas, evitando acidentes e maximizando o potencial de seus veículos.
