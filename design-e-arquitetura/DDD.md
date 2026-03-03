**Anotações feitas por um humano durante a aula**

# Domain-Driven Design (DDD) - O que é?

Design de Código Orientada ao Domínio

Design orientado a domínio é o conceito de que a estrutura e o idioma do seu código devem corresponder ao domínio comercial.

Isso quer dizer que o seu código, precisa refletir a realidade do negócio.

Então basicamente o design orientado a dominio é pegar a realidade dop negócio e traduzir isso no nosso código

Padrões estratégicos

- Linguagem Ubíqua (Onipresente): se eu tenho um conceito no meu negócio, o meu código precisa refletir esse conceito
- Contextos delimitados: quando a gente tem módulos maiores na nossa aplicação e a gente divide eles em contextos
- Domínio e Subdomínio: domínio principal (core domain) e subdomínios (satélites)
- ...

Padrões táticos (blocos de construção)

- Entidades
- Repositórios
- Eventos
- Módulos
- Serviços
- ...

E a arquitetura? Como isso está relacionado a arquitetura?

No livro do DDD existe uma sugestão de arquitetura em camadas, mas eu quero deixar bem claro que DDD não é um padrão arquitetural, DDD está mais para uma filosofia de desenvolvimento, onde você busca atender os requisitos do domínio, do negócio, só que existe uma sugestão no livro do DDD onde voc?ê separa a sua aplicação em algumas camadas:

- User Interface
- Application
- Domain
- Infrastructure

Então é muito comum, nos pegarmos os conceitos de arquitetura sugeridos no livro de DDD e aplicar dentro de algum padrão arquitetural, como o clean architecture

---

**Conteúdo das anotações melhorado por uma IA**

prompt utilizado:

```
Preciso que você deixe o conteúdo abaixo mais organizado, deixe as explicações mais claras para um iniciante nos estudos de design de código e arquitetura de software.
[conteúdo]
```

O Domain-Driven Design (DDD), ou Design Orientado ao Domínio, pode parecer complexo no início porque ele não é uma "receita de bolo", mas sim uma mentalidade. O foco deixa de ser "como o banco de dados funciona" e passa a ser "como o negócio do cliente funciona".

## 🧩 O que é DDD (Domain-Driven Design)?

Criado por Eric Evans, o DDD é uma abordagem de modelagem de software que afirma : a estrutura do seu código deve ser reflexo fiel das regras de negócio.

Se o dono da empresa chama um processo de "Faturamento", no seu código deve existir uma classe ou método chamado `Faturamento`, e não algo genérico como `ProcessarDados`.

---

## 🎯 Padrões Estratégicos (A Visão do Gestor)

Estes padrões servem para organizar o design em alto nível, antes mesmo de começar a programar as funções.

1. Linguagem Ubíqua (Onipresente): É o vocabulário comum entre desenvolvedores e especialistas do negócio (stakeholders). Todos devem usar os mesmos termos para evitar falhas de comunicação.
2. Contextos Delimitados (Bounded Contexts): É a divisão do sistema em "fronteiras". O conceito de "Cliente" no contexto de vendas pode ser diferente do "Cliente" no contexto de suporte. O DDD sugere separar essas responsabilidades.
3. Domínio e Subdomínio:

- Core Domain: O coração do negócio, o que traz dinheiro e diferencial competitivo.
- Subdomínios: Serviços de apoio (ex: sistema de envio de e-mails ou autenticação)

---

## 🛠️ Padrões Táticos (A Visão do Programador)

São os "blocos de construção" que usamos para implekentar o domínio no código:

- Entidades: Objetos que tem uma identidade única que se mantém no tempo (ex: um `Usuario` com ID 123).
- Value Objects (Objetos de Valor): Objetos que não tem identidade, valem pelo que carregam (ex: um `Endereço` ou uma `Cor`).
- Repositórios: Portas de acesso para salvar e buscar suas entidades.
- Serviços de Domínio: Lógicas que não pertencem a uma única entidade, mas fazem parte do negócio.
- Eventos de Domínio: Algo que aconteceu no negócio e que outras partes do sistema precisam saber (ex: `Pedidofinalizado`)

---

## 🏗️ DDD vs. Arquitetura

É aqui que muitos iniciantes se confumdem: DDD não é uma arquitetura, é uma filosofia. No entanto, o livro original sugere uma divisão em 4 camadas para suportar essa filosofia:

| Camada             | Responsabilidade                                                       |
| :----------------- | :--------------------------------------------------------------------- |
| **User Interface** | Exibir informações e traduzir as ações do usuário.                     |
| **Application**    | Coordena as tarefas, mas não contém regras de negócio (é o "maestro"). |
| **Domain**         | Onde mora o coração do sistema (Entidades, Regras, Lógica).            |
| **Infrastructure** | Implementações técnicas (Banco de dados, Mensageria, APIs externas).   |

Nota importante: É por isso que o DDD combina tão bem com a Clean Architecture ou a Arquitetura Hexagonal. Todas elas buscam proteger o Domain das influências externas da Infrastructure.
