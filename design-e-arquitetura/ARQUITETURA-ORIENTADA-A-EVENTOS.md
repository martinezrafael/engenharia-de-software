Preciso que você deixe o conteúdo abaixo mais organizado, deixe as explicações mais claras para um iniciante nos estudos de design de código e arquitetura de software.

**Anotações feitas por um humano durante a aula**

# O que é uma arquitetura orientada a eventos?

A gente vai modelar a nossa arquitetura de uma forma diferente, para que os componentes sejam eles o que forem, podem ser microsserviços por exemplo se comuniquem de forma diferente do que a gente está habituado que é através de requisições.

geralmente, a gente utiliza o que é conhecido como modelo de requisições.

a ideia de ter uma arquitetura orientada a eventos é que você descople toda essa comunicação

exemplo

um produto é adicionado no carrinho

um evento é enviado para um centralizador de eventos

centralizador de eventos: especializado em armazenar esses eventos e distibuir depois

o que esse centralizador vai fazer é:

- identificar que recebeu um evento de carrinho
- enviar esse evento para o serviço de pedido
- o serviço de pedido cria um novo evento que é enviado para o serviço de catalogo
- esse serviço de catalogo cria um evento que é enviado para algum outro serviço
- e o fluxo segue até finalizar

O que isso tras pra gente de vantagem?

De cara, podemos ver que a complexidade aumenta, mas enquanto a complexidade aumenta podemos identificar alguns ganhos, por exemplo o ganho de escalabilidade:

Existem 3 tipos de escalabilidade:

1. Escalabilidade Horizontal
2. Escalabilidade Vertical
3. Em profundidade

A de profundidade é um pouco menos comum quando falamos de escalabilidade de sistemas, ela é muito mais utilizada em armazenamento de dados.

A escalabilidade vertical é a mais tranquila de entender, que é basicamente: quando o serviço está recebendo muita requisição, coloca mais hardware nele, mais memória, mais cpu, o que mais precisar.

Já a escalabilidade horizontal é simplesmente adicionar mais instancias, essa aplicação está recebendo muitas requisições, coloca mais um servidor, e isso é meio que infinito, você pode adicionar quantos servidores quiser, só que hoje em dia, com a tecnologiua que temos, a gente não consegue adicionar quanta memória ram a gente quer no mesmo serviço, no mesmo servidor, por isso a escalabilidade horizontal é mais fácil de ser aplicada e no longo prazo ela reduz custos.

E com essa separação dos componentes se comunicando por serviços, essa separação é muito mais fácil, porque eu posso ter um serviço completamente independente daquele outro que a gente nem sabe qual é e se algum erro acontecer o meu outro serviço continua recebendo requisições sem problema.

isso faz com que o nosso sistema consiga lidar melhor com cenários de falha

Event Bus: centralizador de eventos que normalmente é implementado através de serviços de mensageria.

Event Sourcing

Garantir que cada modificação no estado de uma aplicação é capturada em um evento e que esses eventos são em si, armazenados em sequencia de forma que eles conseguem criar uma timeline.

---

**Conteúdo das anotações melhorado por uma IA**

prompt utilizado:

```
Preciso que você deixe o conteúdo abaixo mais organizado, deixe as explicações mais claras para um iniciante nos estudos de design de código e arquitetura de software.
[conteúdo]
```

## 🏗️ O que é Arquitetura Orientada a Eventos?

Tradicionalmente, usamos o Modelo de Requisição/Resposta (Síncrono), onde um serviço chama o outro e fica esperando a resposta. Na EDA, os componentes se comunicam de forma Assíncrona através de fatos que já ocorreram.

O Fluxo na Prática:

1. Ação: Um produto é adicionado ao carrinho.
2. O Evento: O sistema de carrinho publica um evento: "ProdutoAdicionado".
3. O Centralizador (Event Bus): Recebe esse evento e o distribui para quem estiver interessado.
4. Reação: O serviço de Pedidos ouve o evento e cria um rascunho de pedido; o serviço de Estoque ouve e reserva o item.

---

## 📈 Vantagens e Escalabilidade

Embora seja mais complexa de configurar, essa arquitetura oferece ganhos massivos em como o sistema cresce.
Os 3 Tipos de Escalabilidade:

| Tipo                | Como funciona?                                          | Analogia                                                           |
| :------------------ | :------------------------------------------------------ | :----------------------------------------------------------------- |
| **Vertical**        | Aumenta o poder do servidor atual (mais RAM, mais CPU). | Comprar um caminhão maior para levar mais carga.                   |
| **Horizontal**      | Adiciona mais servidores trabalhando em paralelo.       | Contratar 10 motoboys em vez de apenas um.                         |
| **Em Profundidade** | Focada em otimizar o armazenamento e camadas de dados.  | Organizar melhor as prateleiras do armazém para caber mais coisas. |

Por que a EDA ajuda? Como os serviços são independentes, você pode escalar horizontalmente apenas o serviço que está "sofredo". Se o Estoque está lento, você cria 5 instâncias dele, sem precisar mexer no resto do sistema.

---

## 🛡️ Resiliência (Lidando com Falhas)

Em uma arquitetura comum, se o serviço de Pagamento cai, o sistema de Vendas trava.

Na Arquitetura Orientada a Eventos:

- Se o serviço de Pagamento cair, o evento de `PedidoRealizado` fica parado no Event Bus.
- Assim que o serviço de Pagamento voltar, ele lê a fila e processa tudo.
- Resultado: O usuário não recebe um erro; o sistema apenas demora um pouco mais para processar "nos bastidores".

---

## 📚 Conceitos Avançados (Sem Complicação)

_Event Bus (Barramento de Eventos)_
É o "correio" central. Geralmente implementado com ferramentas de Mensageria (como RabbitMQ ou Kafka). Ele garante que a mensagem saia do produtor e chegue aos consumidores.

Event Sourcing

Em vez de salvar apenas o "estado atual" no banco de dados (ex: Saldo: 100), você salva a história completa de como chegou ali:

1. `DinheiroDepositado: 50`
2. `DinheiroDepositado: 70`
3. `DinheiroSacado: 20`

Isso cria uma Timeline (Linha do Tempo) perfeita. Se você perder o saldo final, basta somar os eventos novamente para descobrir o valor exato.

---

_Resumo para Fixação:_

| Conceito           | Definição Simples                                             |
| :----------------- | :------------------------------------------------------------ |
| **Evento**         | Um registro de algo que já aconteceu (Passado).               |
| **Desacoplamento** | Um serviço não precisa saber que o outro existe.              |
| **Assíncrono**     | Enviar a mensagem e não precisar esperar a resposta imediata. |
| **Event Sourcing** | Armazenar a história dos fatos, não apenas o resultado final. |
