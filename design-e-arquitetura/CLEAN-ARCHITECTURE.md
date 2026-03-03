**Anotações feitas por um humano durante a aula**

## O que arquitetura de software?

Definição dos componentes, suas propriedades externas e seus relacionamentos com outros softwares.

É como você organiza componentes do seu software para que ele seja de maneira mais fácil: manutenivel, ou seja, para que você consiga dar manutenção para ele de forma fácil, para que você consiga adicionar novas funcionalidades de forma indolor.

Então, na prática é como você organiza em uma visão de alto nível o seu código.

- A arquitetura de pastas da sua aplicação, faz parte da sua arquitetura de software.
- Quais classes você vai colocar e onde, faz parte da sua arquitetura de software

# Clean Architecture (Arquitetura Limpa) - O que é?

- entities: o núcleo da camada, ou seja, a camada mais interna, uma camada que todas as outras podem ver, porém uma camada isolada que não conversa com ninguém.

O que são entities (entidades)?
segundo o DDD é um tipo de classe que possui uma identidade
nas entities, ficam as regras de negócio da nossa aplicação

e para acessar essas entidades/regras de negócios utilizamos os use cases

use cases que, para quem estuda ddd, pode ser chamado de application services (serviço de aplicação)

um use case, nada mais é do que uma classe que vai oprganizar o fluxo da regra de negócios

um use case pode ser chamado através de um

- cotroller
- comando na linha de comando
- requisição de uma mensageria

tendo use cases, nós ficamos agnóstiscos de mecanismos de sistema de entrega

e na camada um pouco mais externa, nós temos alguns detalhes de infraestrutura:

- controllers
- presenters: algum adaptador de detalhes do framework
- gateways

e a camada mais externa, é a camada que só tem detalhes de infraestrutura

- framework web
- web
- interface com o usuário
- qualquer interfaze externa que a gente permita acessar a nossa aplicação
- endpoints de uma api
- banco de dados

na camada mais externa não tem regra nenhuma de negócios

as camadas mais externas tem acesso as camadas mais internas, mas ao contrário não

---

**Conteúdo das anotações melhorado por uma IA**

A Clean Architecture (Arquitetura Limpa), popularizada por Robert C. Martim (Uncle Bob), é focada em uma única regra de ouro: o código de negócio não deve depender de tecnologia.

## 🏗️ O que é Arquitetura de Software?

A arquitetura não é sobre o código que faz o cálculo, mas sobre onde esse código mora e como ele se comunica.

- Visão de alto nível: É o desenho das pastas, componentes e a estratégia de organização.
- Manutenibilidade: O objetivo principal é permitir que o software cresça sem se tornar um "monstro" impossível de alterar.
- Independência: Uma boa arquitetura permite que você troque o banco de dados ou framework web sem quebrar a lógica principal do negócio.

---

## 🧼 Clean Architecture (Arquitetura Limpa)

A ideia central é organizar o sistema em círculos concêntricos. A regra de dependência é simples: as camadas externas podem conhecer as internas, mas as internas nunca sabem nada sobre as externas.

_1. Entities(Entidades) - O núcleo_
É a camada mais interna e protegida.

- O que são: Classes que representam os conceitos do negócio (ex: `Cliente`, `Pedido`, `Produto`).
- Regras de negócio cruciais: Aqui ficam as regras que existiriam mesmo se não houvesse um computador (ex: "Um pedido deve ter pelo menos um item").
- Isolamento: Elas não conhecem banco de dados, nem APIs, nem frameworks.

_2. Use Cases (Casos de Uso) - A orquestração_
Também chamados de Application Services.

- O que são: Classes que ditam o "passo a passo" de uma ação especifíca (ex: `RealizarCheckout`, `AlterarSenha`).
- Função: O use Case recebe os dados, chama a entidade para validar e manda salvar (através de uma interface).
- Agnóstico: Ele não sabe se quem o chamou foi um site, um aplicativo ou um robô.

_3. Interface Adapters (Adaptadores)_
A camada que traduz os dados para o formato mais conveniente para os Use Cases e para as telas/bancos.

- Controllers: Recebem a entrada do usuário e passam para o Use Case.
- Presenters: Pegam o resultado do Use Case e formatam para exibir na tela.
- Gateways: Interfaces que definem como o sistema conversa com o mundo externo (como o banco de dados).

_4. Frameworks & Drivers - A camada externa_
Aqui ficam os "detalhes" que mudam com frequência.

- Onde moram:O banco de dados (SQL, MongoDB), o Framework Web (Spring, Express, .NET), a interface do Usuário (UI) e as APIs externas.
- Regra: Esta camada não possui regra de negócio. Ela apenas entrega dados e exibe resultados.

---

## 📊 Resumo de Fluxo e Dependência

| Camada        | Tipo de Lógica                            | Conhece a camada... |
| :------------ | :---------------------------------------- | :------------------ |
| **Entities**  | Regras de Negócio Globais                 | Ninguém (Isolada)   |
| **Use Cases** | Fluxo da Aplicação                        | Entities            |
| **Adapters**  | Conversão de Dados (Controllers/Gateways) | Use Cases           |
| **Infra/Web** | Ferramentas e Frameworks                  | Adapters            |

---

### Por que usar essa estrutura?

Ao separar o cérebro (Entidades/Use Cases) dos Membros (Web/Banco de dados), você ganha liberdade. Se o banco de dados ficar lento e você precisa trocar o seu "Cérebro" nem vai perceber a mudança.
