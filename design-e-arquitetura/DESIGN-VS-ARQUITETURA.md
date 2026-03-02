**Anotações feitas por um humano durante a aula**

# Design de código vs Arquitetura de software

_Design vs Arquitetura_
Tem diferença ou é a mesma coisa?

## Definições chatas e formais

_Design de código_
Design orientado a objetos é a disciplina de definir os objetos e suas interações para resolver um problema que foi identificado e documentado durante a análise orientada a objetos.

_Arquitetura de software_
A arquitetura de software de um sistema consiste na definição dos componentes de software, suas propriedades externas, e seus relacionamentos com outros softwares.

---

## Analogia com uma casa

- Um arquiteto faz a planta da casa.
- Um designer de interiores define como os móveis vão estar.

_Agora trazendo para TI_

- A arquitetura de software é justamente essa visão de mais alto nível: como você vai organizar as suas pastas, os seus namespaces, seus pacotes, etc. Para isso, nós temos estudos de clean architecture, arquitetura hexagonal, onion architecture.Então a arquitetura de software é uma visão de alto nível de como você vai modelar o seu sistema.
- Agora, quando vamos mais para baixo nível e falamos de código especifíco: como uma classe se relaciona com outra, essa minha classe está muito acoplada? Essa minha classe tem muitos atributos? isso podemos definir como design de código e entramos em outro tipo de estudo. (Principios de orientação a objetos, SOLID, DRY, KISS, DDD, Design Patterns), então esses detalhes aqui estão mais relacionados a uma visão de um pouco mais baixo nível de software, ou seja, do código em si.

Arquitetura: Visão de mais alto nível. Separação de camadas, pastas da aplicação.
Design: Visão de mais baixo nível. Como escrever cada classe, quais padrões aplicar.

---

**Conteúdo das anotações melhorado por uma IA**

prompt utilizado:

```
Preciso que você deixe o conteúdo abaixo mais organizado, deixe as explicações mais claras para um iniciante nos estudos de design de código e arquitetura de software.
[conteúdo]
```

## 🏗️ Arquitetura vs. Design: Qual a diferença?

Embora andem de mãos dadas, a diferença principal está no nível de detalhe e no impacto das decisões.

1. Arquitetura de Software (O "Macro")
   A arquitetura é a fundação. São as decisões estratégicas que são difíceis de mudar mais tarde. Ela foca em como o sistema é dividido e como essas partes se comunicam.

- Onde foca: Estrutura global, performance, escalabilidade e segurança.
- Decisões comuns: "Vamos usar microsserviços?", "Onde os dados serão salvos?", "Como as camadas (UI, Banco, Lógica) se separam?".
- Padrões famosos: Clean Architecture, Hexagonal (Posts and Adapters), Microsservices.

2. Design de Código (O "Micro")
   O design (ou Low-level Design) foca na implementação. É a tática aplicada no dia a dia para garantir que o código seja fácil de ler, testar e manter.

- Onde foca: Classes, funções, interfaces e a lógica interna.
- Decisões comuns: "Esta classe está fazendo coisas demais?", "Como evito repetir este código?", "Como este objeto conversa com aquele?".
- Ferramentas: Princípios SOLID, Design Patterns (Strategy, Observer, Factory), DRY (Don't Repeat Yourself).

---

## 🏠 A Analogia da Construção

Para facilitar, imagine que estamos construindo um prédio:

| Aspecto         | Arquitetura                                                                  | Design de Código                                                                      |
| :-------------- | :--------------------------------------------------------------------------- | :------------------------------------------------------------------------------------ |
| **A Casa**      | A planta estrutural: onde ficam os pilares, a rede elétrica e o encanamento. | O projeto dos cômodos: onde ficam as tomadas, a disposição dos móveis e o acabamento. |
| **No Software** | Como as pastas e serviços são organizados (Ex: Clean Architecture).          | Como as classes e métodos são escritos (Ex: SOLID / Design Patterns).                 |
| **Mudança**     | **Difícil e caro:** Mudar o banheiro de lugar depois de pronto.              | **Mais simples:** Trocar a cor da parede ou a posição de um sofá.                     |

---

## 📝 Resumo Direto ao Ponto

- Arquitetura é sobre o ONDE e o COMO o sistema se sustenta (Alto nível).
- Design é sobre o COMO o códigop é escrito e se organiza internamente (Baixo nível).
