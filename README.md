# ROBERT_PROJETO_REDES_DE_COMPUTADORES_IOT_SPRINT_8


## Objetivo do projeto

Objetivo do projeto é fazer o monitoramento de um rack de redes remotamente, tendo em mente verificar se o rack esta aberto ou fechado.
O projeto foi desenvolvido para ser o mais acessivel possivel tanto na parte da montagem e na parte de uso para os usarios.o projeto foi desenvolvido com  uma placa arduino onde tem um sensor magnetico que irá verificar se a porta esta ABERTA ou FECHADA, um modolu Ethernet que irá fazer a conexão
a internet da placa arduino e um servidor MQTT hospedado na **Amazon web service (AWS)** que vai fornecer a comunicação entre o rack e o dispositivo movel do usuario que estara com o aplicativo [MQTT Dash](https://play.google.com/store/apps/details?id=net.routix.mqttdash&hl=en&gl=US) para visualização do 
estado do rack.

![](https://github.com/redeslinuxcode/ROBERT_PROJETO_REDES_DE_COMPUTADORES_SPRINT_8/blob/main/projeto_arduino.png)

bibliotecas utlizada:
- [UIPEthernet](https://github.com/UIPEthernet/UIPEthernet) (conexão do ENC28J60 com o Arduino)
- [pubsubclient](https://github.com/knolleary/pubsubclient) (cliente MQTT para o Arduino)

---

## expecificaçoes dos materiais e protocolos usados

### Placa arduino UNO:
O Arduino Uno é uma placa de código aberto baseada no microcontrolador Microchip ATmega328P e desenvolvida pela Arduino.cc. A placa está equipada com conjuntos de pinos de entrada / saída digitais e analógicos que podem ser conectados a várias placas de expansão e outros circuitos sendo assim é um sistema de prototipagem rápida que permite o desenvolvimento de projetos sem a necessidade de maiores investimentos na criação de placas de circuito impresso o projetos eletrônicos.

![](https://github.com/redeslinuxcode/ROBERT_PROJETO_REDES_DE_COMPUTADORES_SPRINT_8/blob/main/arduino--uno.png)
---
### Sensor magnético (MC-38);

utilizado para detecção de portas ou janelas para quando há algum tipo de de violção do sistema de segurança.
Dentro do sensor possui dois fios, e quando enconstado a um ima que se encontra na segunda metade do sensor, o curto é fechado e seu valor passa a ser 0 *FECHADO*.
E se a segunda metade é afasta, o curto é aberto e dessa forma o seu valor passa ser 1  *ABERTO*.


![](https://github.com/redeslinuxcode/ROBERT_PROJETO_REDES_DE_COMPUTADORES_SPRINT_8/blob/main/Sensor_magn%C3%A9tico.jpg)  ![](https://github.com/redeslinuxcode/ROBERT_PROJETO_REDES_DE_COMPUTADORES_SPRINT_8/blob/main/funcionamento_sensor_magnetico2.PNG)
---
### Módulo de Ethernet (ENC28J60)

O Módulo Ethernet ENC28J60 é utilizado para atribuir ao Arduino a conexão ethernet / internet, dessa forma torna-se possível controlar o Arduino a partir da rede interna (ethernet) ou através da rede externa (internet).

![](https://github.com/redeslinuxcode/ROBERT_PROJETO_REDES_DE_COMPUTADORES_SPRINT_8/blob/main/mudulo_ethernet_.jpg.png)
---
### Jumpers:

Os Jumpers são pequenos fios condutores que podem ser conectados a uma protoboard para interligar dois pontos do circuito em projetos eletrônicos, geralmente utilizados em conexões com Arduino.

![](https://github.com/redeslinuxcode/ROBERT_PROJETO_REDES_DE_COMPUTADORES_SPRINT_8/blob/main/jumpers___.PNG.png)
---
### Protocolo MQTT:
  O MQTT- Message Queue Telemetry Transport ( Transporte de Filas de Mensagem de Telemetria) é um Protocolo de Comunicação baseado na pilha TCP/IP, sendo extremamente útil para desenvolvimento de projetos de comunicação entre Máquina-Máquina (M2M), seu conceito de transmissão é do tipo Publicação/Assinatura.
  A publicação e recebimento de dados são feitos através de um servidor nomeado de Broker. Um cliente no papel de Pulicador ou Publisher, que é a pessoa que transmite a mensagem, escreve um tópico de destino da mensagem e o seu Payload (conteúdo da mensagem), essa mensagem então é transmitida ao Broker que será responsável por gerir e encaminhá-la ao Subscrito ou Subscriber previamente inscrito no tópico. Da mesma forma, quando um cliente quer se tornar um Subscrito em um determinado tópico, ele encaminha uma mensagem de solicitação ao Broker, que fará essa interligação entre cliente e tópico.
  
- Publicador/ Publisher:  Quem envia dados para um tópico, emissor.
  
- Subscrito/ Subscriber:  Pessoa que está inscrita no tópico e recebe os dados, receptor.

- Broker: Intermédio de comunicação entre Publicador e Subscrito, responsável por receber, enfileirar e enviar as mensagens.
Payload: Conteúdo da mensagem enviada.

- Cliente/Client: Elemento capaz de interagir com o Broker, seja para enviar, receber ou os dois.

- Mensagem: Pacote de dados trocados entre Clientes e Broker.

- Tópico: Endereço para o qual os dados serão encaminhados.

- Unsubscribe: Deixar de assinar um tópico.

| ![](https://github.com/redeslinuxcode/ROBERT_PROJETO_REDES_DE_COMPUTADORES_SPRINT_8/blob/main/comunicacao_mqtt.png.png)
|---
## circuito:

![](https://github.com/redeslinuxcode/ROBERT_PROJETO_REDES_DE_COMPUTADORES_SPRINT_8/blob/main/circuito2.PNG.png)

### Ligação dos Jumpers 

|| PINOS ENC28J60 | Pinos Arduino |
|
|| -------------- |:------------- | 
|| 	       CS| 	10    	 | 
||	SI       |     	11	 |   
|| 	SO       | 	12       |    
||      SCK	 | 	13	 |
||      VCC	 |     3.3 V	 |
|      GND	 |	GND    	 |
---
 



