# Instruções para Instalação/Execução KAFKA

## Instalando Kafka ##########
### Fazendo Download
```
cd Downloads/ && curl "https://dlcdn.apache.org/kafka/3.2.0/kafka_2.13-3.2.0.tgz" -o ~/Downloads/kafka.tgz
mkdir ~/kafka && cd ~/kafka
```
### Descompactando (dentro da pasta atual '/kafka')
```
tar -xvzf ~/Downloads/kafka.tgz --strip 1
```


## Executando ##########
### Primeiro executar 'zookeeper' e logo após iniciar executar 'kafka'
#### (Verificar/Mudar versão do java: `sudo update-alternatives --config java`)
```
cd kafka
bin/zookeeper-server-start.sh  config/zookeeper.properties
bin/kafka-server-start.sh config/server.properties
```


### Criando um tópico
```
bin/kafka-topics.sh --create --bootstrap-server localhost:9092 --replication-factor 1 --partitions 1 --topic LOJA_NOVO_PEDIDO
```

### Listando os tópicos
```
bin/kafka-topics.sh --list --bootstrap-server localhost:9092
```

### Enviando mensagens
```
bin/kafka-console-producer.sh --broker-list localhost:9092 --topic LOJA_NOVO_PEDIDO

# pedido0, 110
# pedido1, 120
# pedido2, 130
```

### Consumindo Mensagens
```
bin/kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic LOJA_NOVO_PEDIDO
```
#### Consumindo Mensagens (do inicio)
```
bin/kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic LOJA_NOVO_PEDIDO --from-beginning
```

### Mostra mais detalhes dos tópicos
```
bin/kafka-topics.sh --describe --bootstrap-server localhost:9092
```
