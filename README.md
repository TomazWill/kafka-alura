# Instruções para Instalação/Execução KAFKA

## Instalando ##########

### Fazemdo Dowload
```
cd Downloads/ && curl "https://dlcdn.apache.org/kafka/3.2.0/kafka_2.13-3.2.0.tgz" -o ~/Downloads/kafka.tgz
mkdir ~/kafka && cd ~/kafka
```
### Descompactando (dendo da pasta atual '/kafka')
```
tar -xvzf ~/Downloads/kafka.tgz --strip 1
```


## Executando ##########

### Primeiro executar 'zookeeper' após iniciar executar 'kafka'
#### (Verificar versão de java: `sudo update-alternatives --config java`)
```
cd kafka
bin/zookeeper-server-start.sh  config/zookeeper.properties
bin/kafka-server-start.sh config/server.properties
```


### Criando um topico
```
bin/kafka-topics.sh --create --bootstrap-server localhost:9092 --replication-factor 1 --partitions 1 --topic LOJA_NOVO_PEDIDO
```

### Listando os topicos
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
#### Pega mensagens do inicio
```
bin/kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic LOJA_NOVO_PEDIDO --from-beginning
```

### Mostra detalhes dos topicos
```
bin/kafka-topics.sh --describe --bootstrap-server localhost:9092
```
