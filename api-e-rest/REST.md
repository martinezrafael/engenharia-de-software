**Anotações feitas por um humano durante a aula**

# O que é REST?

Representational State Transfer, abreviado como REST, não é uma tecnologia, uma biblioteca, e nem tampouco uma arquitetura, mas sim um modelo a ser utilizado para se projetar arquiteturas de software distribuído, baseadas em comunicação via rede.

REST é um dos modelos de arquitetura que foi descrito por Roy Fielding, um dos principais criadores do protocolo HTTP, em sua tese de doutorado e que foi adotado como o modelo a ser utilizado na evolução da arquitetura do protocolo HTTP.

---

O Roy Fielding estudou na Tese de Doutorado dele: Projeto de arquiteturas de software baseadas em rede

e ele defendeu esse tal de REST que são princípios de aplicações distribuídas.

um dos principios do REST é que a comunicação ocorra entre clientes e servidores

servidor - quem possui recursos
cliente - quem requerem recursos

uma maquina que é cliente não precisa ser cliente para sempre
uma maquina que é servidor não precisa ser servidor para sempre

um dos outros pontos do REST é que ele seja Stateless

Stateless (Sem Estado)

um utro ponto que define o rest é a interface uniforme

Interface Uniforme: Linguagem comum entre clientes e servidores

- Recursos devem ser identificáveis

Exemplo: A web utiliza a url para identificar os recursos

Outro ponto é que a manipulação de recursos deve ser feita através de representações
Ex: um json pode ser a representação

mas eu posso usar também: XML, HTML, ...

outro ponto importante sobre o REST é o uso de hypermedia

---

**Conteúdo das anotações melhorado por uma IA**

prompt utilizado:

```
Preciso que você deixe o conteúdo abaixo mais organizado, deixe as explicações mais claras para um iniciante nos estudos de design de código e arquitetura de software, se puder complemente o material sem adicionar muita complexidade.
[conteúdo]
```

O REST (Representational State Transfer) é o "idioma" oficial da Web moderna. Para um iniciante, o conceito mais importante é entender que o REST não é uma ferramenta que você instala, mas um conjunto de regras que, se seguidas, tornam sua API organizada, escalável e fácil de usar por qualquer um.

Aqui está o conteúdo organizado e simplificado para suas anotações:

---

## 🌐 O que é REST?

REST é um modelo de design (um guia de boas práticas) para criar sistemas que conversam através de uma rede. Ele foi definido por Roy Fielding e serve como a base para como a Web funciona hoje.

Se uma API segue todos os princípios do REST, dizemos que ela é RESTful.

---

## 📏 Os 4 Pilares do REST

Para uma aplicação ser considerada REST, ela precisa respeitar alguns princípios fundamentais:

_1. Cliente-Servidor (Client-Server)_
Existe uma separação clara de responsabilidades.

- Servidor: É o dono dos dados (recursos). Ele guarda a informação e as regras de negócio.
- Cliente: É quem pede os dados para exibir ao usuário.
- Vantagem: Você pode mudar a tecnologia do Banco de Dados (Servidor) sem precisar mexer no aplicativo do celular (Cliente).

_2. Sem Estado (Stateless)_
Cada requisição do cliente para o servidor deve conter todas as informações necessárias para ser compreendida.

- O servidor não guarda memória de requisições anteriores.
- Exemplo: É como se cada vez que você falasse com o garçom, tivesse que dizer seu nome e o número da sua mesa, porque ele não "decora" quem você é entre um pedido e outro.

_3. Cacheável (Cacheable)_

As respostas da API devem dizer explicitamente se podem ser armazenadas (em cache) pelo cliente. Isso evita que o cliente peça a mesma coisa várias vezes, economizando internet e processamento.

_4. Interface Uniforme_

É aqui que o REST se diferencia de outros modelos. Ele define uma linguagem comum para a comunicação:

- Identificação de Recursos: Tudo é um recurso (usuário, produto, venda) e cada um tem um endereço único chamado URI/URL (Ex: meusite.com/produtos/10).
- Representação: Um recurso não é o dado em si, mas uma representação dele. Você pode pedir o mesmo "Produto" em formato JSON, XML ou HTML.
- HATEOAS (Hypermedia): O servidor envia links na resposta que dizem ao cliente o que ele pode fazer a seguir (como botões em uma página web).

---

## 🛠️ REST na Prática: Verbos HTTP

O REST aproveita os verbos que já existem no protocolo HTTP para indicar ações:

| Verbo      | Ação (CRUD)       | Exemplo de URL                            |
| :--------- | :---------------- | :---------------------------------------- |
| **GET**    | Ler / Buscar      | `GET /usuarios` (Lista todos)             |
| **POST**   | Criar / Inserir   | `POST /usuarios` (Cria um novo)           |
| **PUT**    | Atualizar (Tudo)  | `PUT /usuarios/1` (Substitui o usuário 1) |
| **PATCH**  | Atualizar (Parte) | `PATCH /usuarios/1` (Muda só o e-mail)    |
| **DELETE** | Remover           | `DELETE /usuarios/1` (Apaga o usuário 1)  |

---

## 📋 Resumo

| Conceito       | Explicação Simples                                            |
| :------------- | :------------------------------------------------------------ |
| **Recurso**    | O "objeto" que você quer acessar (ex: um livro, um carro).    |
| **URI**        | O caminho/endereço do recurso na rede.                        |
| **Stateless**  | O servidor não "lembra" de você entre uma chamada e outra.    |
| **JSON**       | O formato de representação mais usado no REST hoje em dia.    |
| **Hypermedia** | Links que guiam o usuário sobre quais são os próximos passos. |

---

_💡 Dica de Ouro:_

Muitos devs dizem que fazem REST, mas apenas usam JSON e URLs bonitas. O "verdadeiro REST" exige o uso correto dos Status Codes (como o famoso 404 para "Não encontrado" ou 201 para "Criado com sucesso").
