# Modelagem de eventos

_Definição Formal_
"Event Modeling is a method of describing systems using an example of how information has changed within them over time."

_Tradução_
"Event Modeling é um método de descrever sistemas usando um exemplo de como a informação mudou dentro deles ao longo do tempo."

eu vou descrever todas as ações do meu sistema através de eventos e de copmo essa informação foi modificada ao longo do tempo

_Fases_

1. Brainstorming
2. Ordenação Lógica (the plot)
3. Storyboard
4. Identificando Entradas
5. Identificando saídas
6. Lei de conway
7. Elaboração de cenários

Eventos que alteram o estado da aplicação

_Brainstorming_

"We have someone explain the goals of the project and other information. The participants then vision what system would look and behave like. They put down all the events that they can conceive of having happened. Here we gently introduce the concept that only state changing events are to be specified. Often, people will name "guest viewed calendar for room avaliability". We put those aside for now - they are not events."

_Tradução_
"Nós temos alguém que explica os objetivos do projeto e outras informações. Os participantes, então, visualizam como o sistema seria e como ele se comportaria. Eles anotam todos os eventos que conseguem imaginar que tenham acontecido. Aqui, introduzimos gentilmente o conceito de que apenas eventos que alteram o estado devem ser especificados. Frequentemente, as pessoas sugerem coisas como 'hóspede visualizou o calendário de disponibilidade de quartos'. Nós deixamos esses de lado por enquanto — eles não são eventos."

---

_Ordenação Lógica_
"Now the task is to create a plausible story made of these events. So they are arranged in a line and everyone reviews this time line to understand that this makes sense as events that happen in order."

---

_Storyboard_
"Next, the wireframes or mockups of the story are needed to address those that are visual leaners. More importantly, each field must be represented so that the blueprint for the system has the source of and destination of the information represented from the user's perspective."

---

_Identificando entradas_

"From the earlier section we saw that we need to show how we enable the user to change the state of the system. This is usually the step in wich we do this introduction of these blue boxes. Each time an event is stored due to a users action, we link that to the UI by a command that shows what we are getting from the screen or implicity from client state it's a web application."

---

_Identificando saídas_

"Again looking back at our goals for the blueprint, we now have to link information accumulated by storing events back into the UI via views (aka read-models). These may be things like the calendar view on our hotel system that will show the availability of rooms when a user is looking to book a room."

---

_Lei de conway_

"Now that we know how information gets in and out of our system, we can start to look at organizing the events themselves into swimlanes. We need to do this to allow the system to exist as a set of autonomous parts that separate teams can own. This allows specialization to happen to a level that we control instead of falling ou of the composition of teams."

---

_Elaboração de cenários_

"Each workflow step is tied to either a commandor or a view/read-model.[...] how we make them still collaboratively with all participants in the same space. A Give-When-Then or Given-Then can be constructed one after the other very rapidly while being reviewed by multiple role representatives."

---

**Conteúdo das anotações melhorado por uma IA**

prompt utilizado:

```
Preciso que você deixe o conteúdo abaixo mais organizado, traduza o que está em ingles para pt-br, deixe as explicações mais claras para um iniciante nos estudos de design de código e arquitetura de software, se puder complemente o material sem adicionar muita complexidade.
[conteúdo]
```

O Event Modeling (Modelagem de Eventos) é uma técnica visual e colaborativa para projetar sistemas focando no que realmente importa: o que acontece com a informação ao longo do tempo.

Para um iniciante, nisso como criar "o roteiro de um filme" do seu software antes de começar a programar.

---

## 📽️ O que é Event Modeling?

Definição: É um método de descrever sistemas através de exemplos de como a informação muda dentro deles ao longo do tempo.

Em vez de desenhar tabelas e banco de dados complexas, nós desenhamos uma linha do tempo. Nessa linha, registramos apenas eventos que mudam o estado do sistema (algo que "ficou gravado" no passado).

Em vez de desenhar tabelas de banco de dados complexas, nós desenhamos uma linha do tempo. Nessa linha, registramos apenas eventos que mudam o estado do sistema (algo que "ficou gravado" no passado).

---

## 🚀 As 7 Fases da Modelagem

Abaixo, os conceitos explicados e traduzidos para facilitar seu estudo:

_1. Brainstorming (Chuva de Ideias)_
Tradução: "Alguém explica os objetivos do projeto. Os participantes visualizam como o sistema seria e se comportaria, anotando todos os eventos que imaginam ter acontecido. Introduzimos aqui o conceito de que apenas eventos que alteram o estado devem ser especificados."

- Dica: "Hópede visualizou o calendário" não é um evento, pois nada mudou no sistema. "Reserva Atualizada" é um evento.

_2. Ordenação Lógica(A trama)_
Tradução: "A tarefa agora é criar uma história plausível com esses eventos. Eles são organizados em uma linha do tempo para garantir que a ordem faz sentido."

- O que é: Colocar os post-its de eventos em ordem cronológica (Ex: Primeiro o "Cadastro Criado", depois "Produto Adicionado").

_3. Storyboard (Esboço Visual)_
Tradução: "Em seguida, criamos protótipos (wireframes) da história. Cada campo deve ser representado para que o mapa do sistema mostre a origem e o destino da informação sob a perspectiva do usuário."

- O que é: Desenhar as telas simples que ficam entre os eventos, para vermos onde o usuário clica.

_4. Identificando Entradas (Inputs)_
Tradução: "Precisamos mostrar como permitimos que o usuário altere o estado do sistema. Introduzimos os 'blocos azuis'(comandos). Cada vez que um evento é armazenado por uma ação do usuário, nós o ligamos à interface por um comando."

- O que é: O comando é a intenção do usuário (ex: Botão "Finalizar Compra").

_5. Identificando Saídas (Outputs)_
Tradução: "Agora ligamos a informação acumulada pelos eventos de volta para a interface através de views (modelos de leitura). Podem ser coisas como a visualização do calendário que mostra a disponibilidade de quartos."

- O que é: É o que o usuário vê na tela após o processamento dos dados.

_6. Lei de Conway(Organização de Times)_
Tradução: "Agora que sabemos como a informação entra e sai, organizamos os eventos em raias (swimlanes). Isso permite que o sistema exista como partes autônomas que times separados podem gerenciar."

- O que é: Dividir o sistema em módulos (ex: time de pagamento cuida de uma parte, time de estoque de outra).

_7. Elaboração de Cenários_
Tradução: "Cada etapa do fluxo é ligada a um comando ou uma visualização. Criamos cenários do tipo `Dado que` - `Quando` - `Então` (Given-When-Then) rapidamente com todos os participantes."

- O que é: Criar testes lógicos. Ex: Dado que o estoque tem 1 item, quando eu clico em comprar, então o estoque deve ir para 0.

---

## 📋 Resumo dos Elementos Visuais

| Elemento              | Cor Comum  | O que representa?                          | Exemplo              |
| :-------------------- | :--------- | :----------------------------------------- | :------------------- |
| **Comando**           | Azul 🟦    | Uma intenção ou ação do usuário.           | `Cadastrar Usuário`  |
| **Evento**            | Laranja 🟧 | Algo que já aconteceu e mudou o sistema.   | `Usuário Cadastrado` |
| **View / Read Model** | Verde 🟩   | Informação exibida na tela para o usuário. | `Lista de Usuários`  |

---

## 💡 Complemento: Por que isso ajuda no Design de Código?

Ao usar Event Modeling, você descobre naturalmente as necessidades do seu Domínio (DDD). Você percebe quais dados precisam ser validados (no Comando) e quais precisam ser persistidos (no Evento), evitando criar códigos desnecessários.
