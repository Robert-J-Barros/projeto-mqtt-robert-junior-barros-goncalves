~~~c++

#include <PubSubClient.h> //
#include <UIPEthernet.h> // biblioteca para utilizada para conectar o arduino há internet
#include <utility/logging.h>
#include <SPI.h>


//Define o endereço MAC que será utilizado
byte mac[] = {0x74, 0x3E, 0x1C, 0x95, 0xE1, 0xC7};
//74-3E-1C-95-E1-C7

//Inicia o cliente Ethernet
EthernetClient client;

int sensor=2;  //determina qual a porta que o sensor esta conectada
bool estado_sensor; //variavel para verdadeira ou falsa

bool mensagem;

PubSubClient mqttClient(client);//inicia cliente mqtt

void setup() {
    //Inicia o controlador Ethernet e solicita um IP para o servidor de DHCP
    Ethernet.begin(mac);

    //Inicia o monitor Serial
    Serial.begin(9600);

    //Exibe no Monitor Serial as informações sobre o IP do Arduino
    Serial.print("O IP do Arduino e: ");
    Serial.println(Ethernet.localIP());

    //Exibe no Monitor Serial as informações sobre a Máscara de Rede do Arduino
    Serial.print("A Mascara de Rede do Arduino e: ");
    Serial.println(Ethernet.subnetMask());

    //Exibe no Monitor Serial as informações sobre o Gateway do Arduino
    Serial.print("O Gateway do Arduino e: ");
    Serial.println(Ethernet.gatewayIP());

    //Exibe uma linha em branco
    Serial.println("");

    mqttClient.setServer("54.161.191.80", 1883); // IP do servidor MQTT que esta na AWS

      pinMode(2, INPUT_PULLUP); // determina o modo de funciomanto do sensor

}

void loop() {
  estado_sensor=digitalRead(sensor); //vai ler a variavel e quarda o resultado dentro da variavel estado_sensor
  mqttClient. connect("usuario");//definir nome do usuario 
  
  if (estado_sensor==1){ 
      Serial.println("o sensor esta aberto");
    
      Serial.println(estado_sensor);// no serial monitor vai mostrar o estado do sensor
  mensagem=mqttClient. publish("usuario", "aberto");}// determina o nome do topico no qual as mensagens vai ser armazenada e a mensagem que vai ser enviada 
  if(estado_sensor==0){
  Serial.println(" o sensor esta fechado");
  Serial.println(estado_sensor);
  mensagem=mqttClient. publish("usuario", "fechado");}
  

 mqttClient.loop(); // fazer a verificação a conexão entre o servidor MQTT e o usuario evitando o contato com o servidor
  
}
