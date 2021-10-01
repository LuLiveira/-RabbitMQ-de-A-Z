## Aula 1 - Introdução

## Aula 2 - Instalação Erlang OTP
1. https://www.erlang.org/downloads

## Aula 3 - Instalacão RabbitMQ

1. Comando docker para iniciar um RabbitMQ: 
    `docker run -d  --hostname my-rabbit --name rabbit13 -p 8080:15672 -p 5672:5672 -p 25676:25676 rabbitmq:3-management`


## Aula 7-8 - Filas

**Obs:** *Por padrão o RabbitMQ quando tem 2 consumidores de 1 mesmo tópico o rabbitMQ vai alternando entre os consumidores.*

Ex: Se eu enviar 2 mensagens vai 1 para cada consumidor.

## Aula 9 - Manual Acknowledge (Confirmação de leitura)

*Podemos fazer o acknowledge de forma programática, deixando a cargo do programador ou manual. Se não realizamos o acknowledge da mensagem o RabbitMQ a mantém na fila até ela ser consumida e o acknowledge ser enviado*

## Aula 10 - Exchange e chave de roteamento

No RabbitMQ primeiro a mensagem é pega pelo `exchange` que seria algo semelhante a um "pré-tópico" e a partir dele o RabbitMQ manda a mensagem para o `routing_key` que seria a fila (ou tópico) de fato.

Obs: `exchange` vázio é o default do RabbitMQ se passamos vázio não precisamos criar um exchange.


## Aula 11 - Exchange FANOUT

Para que os nossos consumidores de uma fila processe todas as mensagens independente se é apenas 1 consumidor ou 'n' precisamos criar um `exchange` personalizado
O primeiro tipo de `exchange` é chamado de ***FANOUT*** e o trabalho dele é receber mensagens e enviar para todas as filas associadas a ele.

## Aula 12 - Exchange DIRECT

Diferente do `FANOUT` o exchange `DIRECT` faz uso do `routing_key` para tomar decisões de para qual das filas associadas a ele, ele deve enviar aquela mensagem.

Ex: 2 consumidores associador ao `exchange` porém apenas 1 vai ler mensagems com `routing_key` do tipo **LOG_ERROR**
