### 1) Recomendações do Professor Branquinho

#### 1.1) Exemplo de MQTT em Python

Utilização da biblioteca Paho-Mqtt para realizar a comunicação via MQTT.

#### 1.2) Pré-requisitos

Para esse exemplo funcionar é necessário o uso do Python 3 e da biblioteca Paho-Mqtt.

#### 1.3) Instalando o Paho-Mqtt
```
pip install paho-mqtt
```
- O broker utilizado foi do Eclipse, com o tópico "fatec/bdd/g1/"

- Executando o exemplo sub - para subscrever um tópico

- Executando o exemplo pub - para publicar num tópico

- Autor

    - **Diogo Branquinho Ramos** - *Initial work* - [diogobranquinho](https://github.com/diogobranquinho)

### 2) Estudo

O MQTT (Message Queuing Telemetry Transport) é um protocolo de comunicação leve, baseado em publicação/assinatura (pub/sub).

Ele é muito usado em IoT (Internet das Coisas) porque consome poucos recursos e funciona bem em redes instáveis ou de baixa largura de banda.

A arquitetura básica envolve três papéis:

- Broker (servidor): é o intermediário. Recebe as mensagens dos publicadores (PUB) e repassa para os assinantes (SUB). Ex.: test.mosquitto.org.

- Publisher (publicador): quem envia mensagens em um tópico.

- Subscriber (assinante): quem recebe mensagens de um ou mais tópicos.

- Exemplo:

    - Sensor de temperatura (PUB) envia "25°C" para o tópico casa/sala/temperatura.

    - App no celular (SUB) recebe automaticamente essa mensagem sempre que estiver inscrito no mesmo tópico.

### 3) Características e vantagens do MQTT

- Modelo PUB/SUB: separa quem envia de quem consome → mais escalável e flexível.

- Tópicos hierárquicos: você pode organizar canais como empresa/setor/maquina1/temperatura.

- Leve e eficiente: mensagens pequenas, baixo overhead → ótimo para IoT, dispositivos com pouca bateria e rede lenta.

- QoS (Quality of Service):

    - 0: "At most once" → mensagem enviada sem garantia de recebimento.

    - 1: "At least once" → garantido que chega, mas pode duplicar.

    - 2: "Exactly once" → chega uma única vez (mais custoso).

- Retained messages: broker guarda a última mensagem publicada em um tópico → novo SUB recebe logo ao se conectar.

- Persistência: se o cliente cair e voltar, pode continuar do ponto onde parou (dependendo da configuração).

Vantagens:

- Ótimo para cenários com milhares de dispositivos IoT.

- Funciona bem mesmo em conexões intermitentes.

- Muito usado em telemetria, sensores, automação residencial, veículos conectados etc.

### 4) Testes

- 4 terminais foram criados

    - Esquerda Superior: sub
    - Esquerda Inferior: pub
    - Direita Superior: sub
    - Direita Inferior: pub

- Ações (ordem de execução):
    
    - ES

    ```
    D:\pessoal\fatec\4-sem\iot\listas\Lista-2\mqtt>python sub.py
    Running sub
    D:\pessoal\fatec\4-sem\iot\listas\Lista-2\mqtt\sub.py:18: DeprecationWarning: Callback API version 1 is deprecated, update to latest version
    con = mqtt.Client()
    Connected with result code 0
    ```

    - EI
    ```
    D:\pessoal\fatec\4-sem\iot\listas\Lista-2\mqtt>python pub.py
    D:\pessoal\fatec\4-sem\iot\listas\Lista-2\mqtt\pub.py:5: DeprecationWarning: Callback API version 1 is deprecated, update to latest version
    con = mqtt.Client()
    Running pub
    ```

    - DS
    ```
    D:\pessoal\fatec\4-sem\iot\listas\Lista-2\mqtt>python sub.py
    Running sub
    D:\pessoal\fatec\4-sem\iot\listas\Lista-2\mqtt\sub.py:18: DeprecationWarning: Callback API version 1 is deprecated, update to latest version
    con = mqtt.Client()
    Connected with result code 0
    ```

    - DI
    ```
    D:\pessoal\fatec\4-sem\iot\listas\Lista-2\mqtt>python pub.py
    D:\pessoal\fatec\4-sem\iot\listas\Lista-2\mqtt\pub.py:5: DeprecationWarning: Callback API version 1 is deprecated, update to latest version
    con = mqtt.Client()
    Running pub
    ```

    - quando eu digito "Cliente 1" no termnal inferior a esquerda e "Cliente 2" no terminal inferior a direita, esses dois comandos aparecem no sub conforme imagem abaixo

<img src="/mqtt/mqtt1.png" alt="MQTT Execução" height="500">