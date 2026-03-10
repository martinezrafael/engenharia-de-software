# O que são Microsserviços?

Em um projeto web, mais especificamente onde o servidor processa a resposta, nós temos diversas formas de organizar nossa aplicação ou o nosso projeto.

Uma das formas mais comuns é o que a gente conhece como aplicações monolíticas.

_Alguns problemas_

- Demoras no deploy
- Falhas podem derrubar o sistema todo
- 1 projeto = 1 tecnologia

_Arquitetura de Microsserviços_

Cada parte da aplicação é um serviço independente

- api gateway (ponto central)

## Definição formal

Microsserviços são uma abordagem arquitetônica e organizacional do desenvolvimento de software no qual o software consiste em pequenos serviços indpenedentes que se comunicam usando APIs bem definidas. Esses serviços pertencem a pequenas equipes autossuficientes.

APIs RESTful são bastante comuns nesse cenário.

## Algumas vantagens

- Projetos independentes = tecnologias independentes
- Falha em 1 serviço é isolada
- Deploys menores e mais rápidos

## Algumas desvantagens

- Maior complexidade de desenvolvimento e infra
- Debug mais complexo
- Comunicação entre os serviços deve ser bem pensada
- Diversas tecnologias podem ser um problema
- Monitoramento é crucial e mais complexo

## Quando utilizar?

- Começar escrevendo uma aplicação monolitica
- se for necessário, você vai quebrando em serviços separados

## Tipos de microsserviços

- Data Service
- Business Service
- Translation Service
- Edge Service
