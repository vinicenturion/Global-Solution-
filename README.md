# Global-Solution-
A diabetes é uma doença que vem crescendo muito ao decorrer do tempo aqui no Brasil, por este motivo fizemos esta solução que simula um sistema no qual visa auxiliar o usuário a monitorar sua pressão arterial, ja em vista que a partir do momento que a doença vai se agravando com o decorrer do tempo,  o paciente pode começar a ter sucessivas quedas de sua pressão, com este aplicativo em mãos o monitoramento ficaria muito mais facil e acessível para todos.
# Descrição
 Nosso projeto visa desenvolver um monitoramento de pressão do usuário (simulado, pois nao possuimos os acessórios necessários). Na intenção de auxiliar o usuário a monitorar sua pressão em prol de controle da diabetes.
 # Funcionalidades
 O Arduino UNO utiliza um potenciômetro para simular a entrada de pressão arterial e um sistema de LED's para sinalizar a regularidade da pressão arterial (Verde para OK  e Vermelho para muito alta/baixa. Para monitorar a pressão, o display mostra "muito baixa" enquanto estiver entre 299 até 0, estável a partir de 300 até 700, o display deve mostrar "muito alta" se acima de 700.
 # Tecnologias e componentes utilizados
- Linguagem C
- IDE Arduino
- Protoboard
- Placa de Arduino
- LEDs (Verde e Vermelho)
- Resistores
- Jumpers
- Display
- Potenciômetro
- LiquidCrystal.h
# Rodando o projeto
Para rodar, você pode acessar a simulação que fizemos a partir link abaixo ou então montar o circuito da imagem e rodar o código a seguir:

![arduino](https://github.com/vinicenturion/Global-Solution-/assets/143764606/20b8ff61-15b1-416d-9564-37e928197a89)

#include <LiquidCrystal.h>

const int pinoPotenciometro = A0;     // Pino analógico onde o potenciômetro está conectado
const int pinoLEDVerde = 13;           // Pino digital onde o LED verde está conectado
const int pinoLEDVermelho = 12;        // Pino digital onde o LED vermelho está conectado
const int pinoBuzzer = 11;             // Pino digital onde o buzzer está conectado


LiquidCrystal lcd(8, 9, 4, 5, 6, 7);

void setup() {
  pinMode(pinoLEDVerde, OUTPUT);
  pinMode(pinoLEDVermelho, OUTPUT);
  
  
  lcd.begin(16, 2);

  
  Serial.begin(9600);
}

void loop() {
  
  int valorPotenciometro = analogRead(pinoPotenciometro);

  
  Serial.print("Valor do Potenciômetro: ");
  Serial.println(valorPotenciometro);

  
  lcd.clear();
  lcd.setCursor(0, 0);
  lcd.print("Pressao: ");
  lcd.print(valorPotenciometro);

  
  if (valorPotenciometro > 300 && valorPotenciometro < 700) {
    digitalWrite(pinoLEDVerde, HIGH);
    digitalWrite(pinoLEDVermelho, LOW);
    lcd.setCursor(0, 1);
    lcd.print("Pressao Estavel");
  } else if (valorPotenciometro >= 700) {
    // Acende o LED vermelho se o valor do potenciômetro estiver muito alto
    digitalWrite(pinoLEDVerde, LOW);
    digitalWrite(pinoLEDVermelho, HIGH);
    lcd.setCursor(0, 1);
    lcd.print("Pressao Alta");
    lcd.setCursor(0, 2);
    lcd.print("(Muito Alto)");

  
  } else {
    
    digitalWrite(pinoLEDVerde, LOW);
    digitalWrite(pinoLEDVermelho, HIGH);
    lcd.setCursor(0, 1);
    lcd.print("Pressao Baixa");
    lcd.setCursor(0, 2);
    lcd.print("(Muito Baixo)");

    
  }

  
}
# Links
- Link simulação: https://www.tinkercad.com/things/d4uSz51gGOx-cool-amur-densor?sharecode=Pps5Lh2xuaZwtNSlL0Kru_ocpWUvokUYq_GCIZIAnPY
- Link vídeo explicativo: https://www.youtube.com/watch?v=sDf_ExaolkI
# Colaboradores
- Jonata Rafael Ferreira Jeronimo - RM: 552939
- Vinicius Centurion Malvero - RM: 554063





 



 
 
 

