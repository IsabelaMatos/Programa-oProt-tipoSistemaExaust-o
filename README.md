# SISTEMA AUTOMATIZADO DE CIRCULAÇÃO E PURIFICAÇÃO DO AR - PROTÓTIPO
O algorítimo a seguir tem como objetivo principal simular o funcionamento do sistema em um protótipo. 
## CIRCUITO
![texto](/image.png)


## ALGORÍTIMO

```c++
//DEFININDO OS PINOS
const int echoPin = 2;
const int trigPin = 3;
const int led1 = 4;
const int led2 = 5;
const int led3 = 6;
const int motor = 12;



//DEFININDO O TIPO DAS ENTRADAS(ENTRADA OU SAÍDA)
void setup() {
  pinMode(echoPin, INPUT);
  pinMode(trigPin, OUTPUT);
  pinMode(led1, OUTPUT);
  pinMode(led2, OUTPUT);
  pinMode(led3, OUTPUT);
  pinMode(motor, OUTPUT);

}
//REPETIÇÃO
void loop() {
  //DECLARANDO AS VARIÁVEIS DE TESTE
  long duracao, distanciaCM;

  //TRIGER ENVIA O SINAL SONORO
  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);
  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);

  //RECEBE O ECHO(SINAL SONORO)
  duracao = pulseIn(echoPin, HIGH);

  //CALCULA A DISTÂNCIA EM CM
  distanciaCM = duracao * 0.034 / 2;

  //TESTANDO A DISTÂNCIA E ACIONA OS COMPONENTES
  if(distanciaCM<10){
    ligaLed3();
  }else if(distanciaCM<20){
    ligaLed2();
  }else if(distanciaCM<30){
    ligaLed1();
  }else{
    desligaLeds();
  }
delay(500); 

}

//DECLARANDO AS FUNÇÕES
void ligaLed1(){
  digitalWrite(led1, HIGH);
  digitalWrite(led2, LOW);
  digitalWrite(led3, LOW);
  digitalWrite(motor, LOW);
}

void ligaLed2(){
  digitalWrite(led1, LOW);
  digitalWrite(led2, HIGH);
  digitalWrite(led3, LOW);
  digitalWrite(motor, LOW);
}

void ligaLed3(){
  digitalWrite(led1, LOW);
  digitalWrite(led2, LOW);
  digitalWrite(led3, HIGH);
  digitalWrite(motor, HIGH);
}

void desligaLeds(){
  digitalWrite(led1, LOW);
  digitalWrite(led2, LOW);
  digitalWrite(led3, LOW);
  digitalWrite(motor, LOW);
}

```
