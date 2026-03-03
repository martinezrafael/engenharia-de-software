**Anotações feitas por um humano durante a aula**

# O que é mensageria?

"Mensageria é um conceito que define que sistemas distribuídos possam se comunicar por meio de troca de mensagens (evento), sendo estas mensagens 'gerenciadas' por um Message Broker (servidor/módulo de mensagens)."

Esse tipo de troca de mensagens, funciona de forma assíncrona.

Conceitos:

Pub/sub - onde temos dois papéis: um de publisher que é quem publica um evento ou uma mensagem e um de subscriber que é quem vai consumir, quem vai ler essa mensagem

rabbitmq

- crio um canal de comunicação
- a partir desse canal, eu crio uma exchange
- eu envio uma mensagem para uma exchange, e essa exchange é configurada para enviar essa mensagem para várias filas ou para uma única fila, etc.

Essa é a ideia por trás de mensageria, você desacoplar totalmente a comunicação e entregar na mão do message broker a resposabilidade de entregar essas mensagens ou eventos.

---

**Conteúdo das anotações melhorado por uma IA**

prompt utilizado:

```
Preciso que você deixe o conteúdo abaixo mais organizado, deixe as explicações mais claras para um iniciante nos estudos de design de código e arquitetura de software, se puder complemente o material sem adicionar muita complexidade.
[conteúdo]
```

A mensageria é um dos pilares da arquitetura de sistemas modernos. Para um iniciante, a melhor forma de entender é pensar nela como o "serviço de correios" do software.

## 📬 O que é Mensageria?

Mensageria é a técnica que permite que dois ou mais sistemas (ou partes de um sistema) conversem enviando mensagens uns aos outros, sem que precisem estar conectados ao mesmo tempo.

- Comunicação Assícrona:Diferente de uma chamada de telefone (onde os dois precisam estar na linha), a mensageria é como o WhatsApp: eu envio a mensagem, sigo minha vida, e você lê quando puder.
- O Message Broker: É o "servidor" ou "intermediário" que recebe, armazena e entrega as mensagens. Ele garante que a mensagem não se perca se o sistema de destino estiver fora do ar.

---

## 🧩 Conceitos Fundamentais

_1. Modelo Pub/Sub (Publish/Subscriber)_
É o modelo mais comum de mensageria. Imagine uma revista:

- Publisher (Editora): Quem envia/publica a mensagem. Ela não sabe quem vai ler, ela apenas entrega ao broker.
- Subscriber (Assinante): Quem tem interesse maquela mensagem. Ele "assina" um tópico e recebe uma mensagem assim que ela chega.

_2. Producer vs. Consumer_

- Producer (Produtor): O sistema que gera a informação (ex: Sistema de vendas que avisa "Pedido Realizado").
- Consumer (Consumidor): O sistema que processa a informação (ex: sistema de estoque que precisa separar os itens do pedido).

---

## 🐰 Exemplo Prático: RabbitMQ

O RabbitMQ é um dos Message Brokers mais famosos. O fluxo dele funciona assim:

1. Canal (Channel): É a "estrada" criada para os dados passarem.
2. Exchange (Roteador): O produtor não envia a mensagem direto para a fila. Ele envia para a Exchange. Ela decide, baseada em regras, para quais filas aquela mensagem deve ir.
3. Queue (Fila): Onde a mensagem fica guardada esperando o cosumidor buscá-la.

---

## 🚀 Por que usar Mensageria? (Complemento)

Para um iniciante em arquitetura, é importante saber o porquê de usar isso:

- Desacoplamento: O sistema de vendas não precisa saber como o sistema de logística funciona. Ele só avisa: "Vendi!".
- Resiliência: Se o sistema de logística cair por 5 minutos, as mensagens ficam guardadadas na fila. Quando ele voltar, ele processa tudo o que acumulou, sem perder nenhum dado.
- Escalabilidade: Se você tiver muitas mensagens, pode colocar 10 sistemas "Consumidores" para lerem a mesma fila, agilizando o trabalho.

---

## 📊 Resumo de Componentes

| Componente            | Função                                   | Analogia                             |
| :-------------------- | :--------------------------------------- | :----------------------------------- |
| **Message Broker**    | Servidor que gerencia as mensagens.      | Agência de Correios.                 |
| **Mensagem / Evento** | O dado que está sendo enviado.           | A carta dentro do envelope.          |
| **Exchange**          | Roteia a mensagem para a fila certa.     | O triador que separa cartas por CEP. |
| **Fila (Queue)**      | Local onde a mensagem aguarda o consumo. | A caixa de correio da sua casa.      |
