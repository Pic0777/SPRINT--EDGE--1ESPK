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

## Código utilizado
```cpp

// Definição dos pinos dos componentes
int VERMELHO = 8; // Pino do LED vermelho
int AMARELO = 9; // Pino do LED amarelo
int VERDE = 10; // Pino do LED verde
int buzzer = 2; // Pino do buzzer
int FORCEPIN = A1; // Pino para leitura do sensor de pressão
int FORCEVALUE = 0; // Variável para armazenar o valor da pressão
int TempSensor = A2; // Pino para leitura do sensor de temperatura
int RawValue= 0; // Variável para armazenar o valor bruto do sensor de temperatura
double tempC = 0; // Variável para armazenar a temperatura em Celsius
double Voltage = 0; // Variável para armazenar a voltagem

void setup() {
  // Inicialização da comunicação serial
  Serial.begin(9600);
  
  // Configuração dos pinos como entrada ou saída
  pinMode(FORCEPIN, INPUT); // Pino de leitura da pressão como entrada
  pinMode(VERMELHO, OUTPUT); // Pino do LED vermelho como saída
  pinMode(AMARELO, OUTPUT); // Pino do LED amarelo como saída
  pinMode(VERDE, OUTPUT); // Pino do LED verde como saída
}

void loop() {
  // Leitura da pressão
  FORCEVALUE = analogRead(FORCEPIN);
  float AREA = 0.31;
  float PRESSURE = (FORCEVALUE / 9.81) / AREA;
  Serial.print ("PSI: "); // Impressão do valor da pressão
  Serial.println(PRESSURE);
  
  // Leitura da temperatura e conversão para Celsius
  RawValue = analogRead(TempSensor);
  Voltage = (RawValue / 1023.0) * 5000;
  tempC = (Voltage - 500) * 0.1;
  
  Serial.print ("Temperatura do pneu: "); // Impressão da temperatura
  Serial.println(tempC);
  Serial.println("////////////////////////////////"); // Separador
  delay(1000); // Atraso de 1 segundo
  
  // Verificação das condições de alerta e acionamento dos LEDs e buzzer
  if ((PRESSURE > 50 or PRESSURE < 18) or (tempC < 85 or tempC > 104)) {
    digitalWrite(VERMELHO, HIGH); // Aciona o LED vermelho
    digitalWrite(AMARELO, LOW); // Desliga o LED amarelo
    digitalWrite(VERDE, LOW); // Desliga o LED verde
    tone(buzzer, 1000, 3000); // Aciona o buzzer com frequência de 1000 Hz por 3 segundos
  } else {
    digitalWrite(VERMELHO, LOW); // Desliga o LED vermelho
    noTone(buzzer); // Para o buzzer
    digitalWrite(AMARELO, LOW); // Desliga o LED amarelo
    digitalWrite(VERDE, HIGH); // Aciona o LED verde
  }
  
  // Verificação das condições de alerta intermediário e acionamento do LED amarelo
  if ((PRESSURE >= 45 and PRESSURE <= 50 or PRESSURE < 23 and PRESSURE > 18 ) or (tempC > 88 and tempC < 91 or tempC > 101 and tempC <104)) {
    digitalWrite(AMARELO, HIGH); // Aciona o LED amarelo
  } else {
    digitalWrite(AMARELO, LOW); // Desliga o LED amarelo
  }
}

```

## Funcionamento do Código

- Configuração dos pinos dos componentes e inicialização da comunicação serial.
- Leitura da pressão e conversão para PSI.
- Leitura da temperatura e conversão para Celsius.
- Verificação das condições de alerta e acionamento dos LEDs e do buzzer.
- O LED verde indica condições normais, o LED amarelo indica alerta intermediário e o LED vermelho indica condições críticas.
- O buzzer emite um som de alerta em caso de condições críticas.
- O código é executado em loop, monitorando continuamente as condições dos pneus.

## Imagem de Exemplo

![Copy of SPRINT - EDGE](https://github.com/Pic0777/SPRINT--EDGE--1ESPK/assets/162361580/d12d8936-068d-440f-9119-d0aea79fa479)

## Link Tinkercad

Você pode acessar o nosso projeto e simulação aqui: https://www.tinkercad.com/things/10wL79CaLIo-sprint-edge

## Conclusão

Este projeto demonstra como utilizar Arduino e sensores para criar um sistema de monitoramento eficaz para os pneus de carros de Fórmula E. Com este sistema, os pilotos podem tomar medidas proativas para garantir a segurança e o desempenho durante as corridas, evitando acidentes e maximizando o potencial de seus veículos.
