# P7-8-HiveMQ_Kafka-M9

# Documentação

O desenvolvimento a seguir foi realizado com o objetivo educacional, visando aprender a integrar o HiveMQ com o Kafka utilizando a plataforma Confluent. O fluxo de dados é iniciado com um publisher desenvolvido em Go, responsável por publicar mensagens em um tópico no broker HiveMQ. Este broker, integrado ao Confluent, encaminha a mensagem para o Kafka. Em seguida, um cliente Kafka, implementado como um código em Go, atua como subscriber, recebendo e consumindo as informações enviadas.

## Documentação das Bibliotecas e Funcionalidades

### `publisher.py`

#### Bibliotecas Utilizadas:

- `github.com/eclipse/paho.mqtt.golang`: Biblioteca para MQTT em Go.
- `github.com/joho/godotenv`: Biblioteca para carregar variáveis de ambiente de um arquivo `.env`.

#### Funcionalidades:

1. **Carregamento de Variáveis de Ambiente**: O código carrega variáveis de ambiente do arquivo `.env`, que contém informações como endereço do broker MQTT, usuário e senha.

2. **Configuração do Cliente MQTT**:
   - Define o endereço do broker e a porta.
   - Define o ID do cliente como "Publisher".
   - Configura usuário e senha para autenticação.
   - Define callbacks para quando a conexão é estabelecida e quando a conexão é perdida.

3. **Conexão e Publicação de Mensagens**:
   - Cria um cliente MQTT com as opções configuradas.
   - Conecta-se ao broker MQTT.
   - Entra em um loop infinito para publicar mensagens no tópico "teste" a cada 2 segundos.

### `subscriber.py`

#### Bibliotecas Utilizadas:

- `github.com/joho/godotenv`: Biblioteca para carregar variáveis de ambiente de um arquivo `.env`.
- `github.com/confluentinc/confluent-kafka-go/kafka`: Biblioteca para consumir mensagens do Kafka em Go.

#### Funcionalidades:

1. **Carregamento de Variáveis de Ambiente**: O código carrega variáveis de ambiente do arquivo `.env`, que contém informações como servidores de bootstrap do Kafka, ID do grupo, chave da API e segredo da API.

2. **Configuração do Consumidor Kafka**:
   - Configura os servidores de bootstrap, ID do grupo e autenticação SASL.
   - Define o modo de redefinição automática do offset para "earliest".

3. **Consumo de Mensagens**:
   - Cria um consumidor Kafka com as configurações fornecidas.
   - Subscreve-se ao tópico "teste".
   - Inicia uma goroutine para consumir mensagens do Kafka e exibir o conteúdo.

4. **Manutenção do Programa em Execução**: Utiliza `select {}` para manter o programa em execução, permitindo que o consumidor continue a receber mensagens.

# Biblicotecas

confluent_kafka

# Funcionamento

Link: https://drive.google.com/file/d/1GE-8m3PiExVPqP71QOVOxgT_qbhKWNXm/view?usp=sharing