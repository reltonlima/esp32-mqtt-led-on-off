# esp32-mqtt-led-on-off

Controla o LED interno do ESP32 pela internet através de um serviço MQTT.

## Descrição do Projeto

Este projeto utiliza um ESP32 para controlar o LED interno (GPIO 2) através de comandos enviados via MQTT. O ESP32 se conecta a uma rede Wi-Fi e a um broker MQTT, onde escuta mensagens no tópico `esp32/led`. Comandos como `on` e `off` podem ser enviados para ligar ou desligar o LED.

## Configurações Necessárias

1. **Wi-Fi**: Atualize as constantes `SSID` e `PASSWORD` no código com o nome e a senha da sua rede Wi-Fi.
2. **Broker MQTT**: O código está configurado para usar o broker público `broker.emqx.io` na porta `1883`. Você pode alterar o broker e o tópico MQTT (`esp32/led`) conforme necessário.

## Instruções de Utilização

1. **Configurar o Ambiente**:
   - Certifique-se de ter o Arduino IDE instalado.
   - Instale as bibliotecas necessárias:
     - `WiFi` (inclusa no ESP32 Core)
     - `PubSubClient` (pode ser instalada via o gerenciador de bibliotecas do Arduino IDE).

2. **Carregar o Código**:
   - Conecte o ESP32 ao computador.
   - Abra o arquivo `sketch_esp32-mqtt-led-on-of.ino` no Arduino IDE.
   - Atualize as configurações de Wi-Fi e MQTT no código, se necessário.
   - Selecione a placa ESP32 e a porta correta no menu "Ferramentas".
   - Faça o upload do código para o ESP32.

3. **Testar o Projeto**:
   - Após o upload, abra o monitor serial para verificar as mensagens de conexão ao Wi-Fi e ao broker MQTT.
   - Use um cliente MQTT (como o MQTT Explorer ou o comando `mosquitto_pub`) para enviar mensagens ao tópico `esp32/led`:
     - Envie `on` para ligar o LED.
     - Envie `off` para desligar o LED.

4. **Exemplo de Comando MQTT**:
   - Para ligar o LED:
     ```bash
     mosquitto_pub -h broker.emqx.io -t esp32/led -m "on"
     ```
   - Para desligar o LED:
     ```bash
     mosquitto_pub -h broker.emqx.io -t esp32/led -m "off"
     ```

## Observações

- Certifique-se de que o ESP32 esteja na mesma rede que o cliente MQTT.
- O broker público `broker.emqx.io` é usado apenas para testes. Para produção, considere usar um broker privado ou seguro.

## Licença

Este projeto está licenciado sob a GNU General Public License v3. Consulte o arquivo [LICENSE](http://_vscodecontentref_/1) para mais detalhes.

## Autor
Relton Lima
