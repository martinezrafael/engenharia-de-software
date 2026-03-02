**Anotações feitas por um humano durante a aula**

# O que é arquitetura hexagonal?

Padrão arquitetural que ficou conhecido como Ports and Adapters.

"Arquitetura é o estudo que ajuda a definir como cada um dos componentes vão conversar entre si dentro da aplicação."

1. Definir quais componentes criar
2. Como os componentes serão organizados na aplicação

Ports and adapters: a ideia desse padrão arquitetural é que a gente isole toda a nossa regra de negócios que também pode ser chamada de domínio.

Então, iremos isolar todo o nosso domínio(regra de negócio), deixaer ele em um local centralizado e toda a comunicação que não está diretamente relacionada ao domínio vai ficar no mundo externo e para essa comunicação acontecer, ela vai utilizar alguma porta que a nossa aplicação vai abrir e essa porta vai enviar alguma mensagem, vai enviar dados e algum adaptador vai conseguir ler essas informações que cghegam por essa porta.

Nós podemos ter nessa arquitetura, formas diferentes de tratar as entradas em portas diferentes.
a
Nós temos dois tipos de adapters:

Primary Adapters: são os que recebem dados e enviam para a nossa regra de negócios

Secondary Adapters: são os que pegam dados da nossa regra de negócio e enviam para fora da nossa aplicação

---

**Conteúdo das anotações melhorado por uma IA**

prompt utilizado:

```
Preciso que você deixe o conteúdo abaixo mais organizado, deixe as explicações mais claras para um iniciante nos estudos de design de código e arquitetura de software.
[conteúdo]
```

A arquitetura hexagonal, também conhecida como ports and adapters (portas e adaptadores), é um dos conceitos mais importantes para quem quer criar sistemas que não "envelhecem" mal.

## ⬢ O que é Arquitetura Hexagonal?

Imagine que sua regra de negócio (a lógica que faz sua empresa ganhar dinheiro) é o "coração" do sistema. A arquitetura hexagonal serve para criar uma blindagem em volta desse coração, impedindo que as tecnologias externas (como bancos de dados, APIs ou telas) "sujem" ou prendam a sua lógica.

_O objetivo principal: Isolação do domínio_
O foco é isolar o domínio(regras de negócio). Ele deve ser independente: se você decidir trocar o seu banco de dados MySQL por um MongoDB, a sua regra de negócio não deveria mudar nem uma linha de código.

---

## O Conceito de Ports and Adapters

Para que o "mundo externo" converse com o seu "domínio" sem que eles se misturem, usamos dois componentes:

1. Ports(Portas): são as interfaces. Elas definem o que o sistena deve fazer, mas não como.

- Exemplo: Uma porta diz: "Eu preciso de um lugar para salvar o usuário". Ela não sabe se esse lugar é um arquivo TXT ou um banco de dados SQL.

2. Adapters (Adaptadores): São as implementações. Eles traduzem a conversa entre o mundo externo e a sua aplicação.

- Exemplo: Um adaptador de banco de dados sabe exatamente como escrever o código SQL para salvar o usuário que a porta pediu.

---

## ⬅️ Entradas vs. Saídas ➡️

A arquitetura divide os adaptadores em dois grupos, dependendo de quem inicia a conversa:

### 📥 Primary Adapters (Direcionadores)

Eles recebem dados do usuário ou de outro sistema e entregam para a sua regra de negócio. Eles "dirigem" a aplicação.

- Exemplos: Uma API Rest, uma interface de linha de comando (CLI), uma tela de formulário.
- Fluxo: `Mundo Externo -> Adapter -> Port -> Domínio`

### 📤 Secondary Adapters (Direcionados)

Eles são chamados pela sua regra de negócio para buscar ou enviar dados para fora. Eles são "dirigidos" pela aplicação.

- Exemplos: Envio de e-mail, salvar no banco de dados, consultar um serviço externos de CEP.
- Fluxo: `Domínio -> Port -> Adapter -> Mundo Externo`

---

## 📋 Resumo para Estudo

| Termo                   | O que é?                                   | Analogia                    |
| :---------------------- | :----------------------------------------- | :-------------------------- |
| **Domínio**             | Onde ficam as regras de negócio.           | O motor do carro.           |
| **Porta (Port)**        | O contrato/interface de conexão.           | A tomada na parede.         |
| **Adaptador (Adapter)** | O código que conecta a tecnologia à porta. | O plugue do seu carregador. |

_Porque isso é bom?_

1. Testabilidade: Você pode testar a sua regra de negócio sem precisar de internet ou banco de dados
2. Flexibilidade: Trocar tecnologias (o "como") fica muito mais seguro.
3. Foco: O desenvolvedor foca no problema do cliente (domínio) antes de se preocupar com o banco de dados.

---

_Links Extras:_

- [Arquitetura hexagonal](https://medium.com/@marcio.kgr/arquitetura-hexagonal-8958fb3e5507)
- [The Hexagonal (Ports & Adapters) Architecture](https://alistair.cockburn.us/hexagonal-architecture)
