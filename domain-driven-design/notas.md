Estou fazendo um curso de DDD para fazer o nosso negócio.

Essas são as anotações que fiz até o momento:

Preciso que você analise os tópicos abordados até o momento e me diga quais coisas são interessantes de aplicarmos nesse processo:

## O preço de não entender o negócio

- Case: Healthcare.gov (Projeto desenvolvido pelo governo dos EUA para fazer matrícula dos cidadãos americanos no sistema de saúde)

Diferença entre débito técnico e débito de domínio

débito técnico:

- testes insuficientes
- código duplicado
- Acoplamento Excessivo
- Performance ruim

débito de domínio:

- conceitos modelados incorretamente
- regras de negócio mal compreendidas
- Linguagem inconsistente
- processos mal representados

---

## Entendendo o conceito de "grande bola de lama"

sinais de alerta na organização

- ninguem entende o sistema completo
- Essa mudança simples vai afetar tudo
- Só o João sabe como isso funciona
- Vamos reescrever do zero

consequencias para o negócio

- aumento de custos e atrasos
- impacto no time
- velocidade de desenvolvimento despenca
- cliente insatisfeito

grande bola de lama
Definição: sistema sem arquitetura coerente, alto acoplamento, regras espalhadas, nomes genéricos

Sintomas: Classes gigantes, nomes genéricos, dependências circulares, métodos "faz-tudo"

Causa Profunda: Ausência de limites claros baseados no domínio

---

## Diferenciando complexidades: essencial x Acidental

complexidade essencial:

- inerente ao problema
- não pode ser eliminada
- razão de existir do software
- fonte de valor para o usuário

complexidade acidental:

- introduzida pela solução
- pode ser reduzida/eliminada
- obstaculo ao valor real
- absorve recursos desnecessariamente

Framework de avaliação da complexidade do domínio

Usando 6 critérios, cada um pontuando de 0 a 3 pontos.
Pontuação total (máx. 18 pontos):

Baixa: 0-6 pontos
Média: 7-12 pontos
Alta: 13-18 pontos

1. Quantidade de regras de negócio: avalia o volume e a ligação entre as regras de negócio

0(Baixa): Poucas regras, claras e separadas
1 (Moderado): Médio número de regras, com algumas ligações
2 (Alta): Muitas regras, complexas e ligadas entre si
3 (Muito Alta): Enorme volume de regras, mudam muito rápido ou são contraditórias.

2. Variabilidade das regras: Considera a frequência e a forma como as regras mudam

0 (Estável): Muito estáveis, quase sem mudanças esperadas.
1 (Esporádica): Mudanças raras ou em épocas certas
2 (Frequente): Mudanças constantes, exige adaptação continua
3 (Continua): Mudanças sem parar e imprevisíveis, muita volatilidade.

3. Invariantes críticas: Analisa o número e a complexidade das codições que não podem ser quebradas:

0 (simples): poucas invariantes claras e simples
1 (moderada): Número médio de invariantes, algumas com validações complexas
2 (complexa): Muitas invariantes, com grandes impactos no sistema e validação cruzada
3 (sutil): criticas e dificeis de ver, falhas podem ter consequências catastróficas.

4. Políticas e exceções: Avalia a quantidade e o impacto de exceções e caminhos alternativos:

0 (rara): poucas exceções, raras e bem explicadas.
1 (comum): número médio de exceções, algumas com processos especiais
2 (Impactante): Muitas exceções, afetam a lógica principal do negócio
3 (Dominante): Exceções demais, difícil de padronizar ou automatizar.

5. Conformidade e Regulação: Considera o peso das exigências legais e regulatórias

0(baixa): Quase sem exigẽncias legais ou regulatórias.
1 (clara): Leis claras, atualizam todo ano
2 (Dinâmica): Várias leis, interpretações complexas e atualizações frequentes
3 (volátil): Ambiente regulatório altamente instável e ambíguo, exige monitoramento constante

6. Ritmo de mudança do mercado: Avalia a velocidade das transformações no mercado e setor:

0 (lento): Mercado maduro, com mudanças lentas e esperadas
1 (moderado): Mudanças nop mercado em ritmo moderado, com novidades pontuais
2 (Rápido): Mercado em rápida evolução, com novas tecnologias e concorrentes surgindo sempre.
3 (disruptivo): Mercado em constante disrupção, exige reinventar-se e adaptar0se sem parar.

Interpretação do Score

0-6 complexidade baixa

- Frameworks opinativos
- Admin generators, low-code
- foco na entrega rápida

7-12: Complexidade Média

- Arquitetura limpa básica
- Alguns padrões de domínio
- Modelagem seletiva

13-18 Complexidade Alta

- Domains-Driven Design completo
- Modelagem colaborativa
- Padrões avançados de domínio

Plano de ação

_Podar complexidade acidental_

- eliminar configurações desnecessárias
- simplificar pipeline de deploy
- reduzir conversões de dados
- Escolher ferramentas mais simples

_Investir na complexidade essencial_

- Modelar o domínio cuisdadosamente
- Criar linguagem ubíqua com o negócio
- Implementar regras explicitamente
- Testar comportamentos de negócio

---

## O que é DDD, afinal?

Fundamentos e filosofia do Domain-Driven Design

_Entendendo o Domínio_

O que é domínio?

Domínio é a esfera de conhecimento, influência ou atividade ao redor da qual, o software é construído.

- Esfera de conhecimento: O que os especialistas sabem sobre e-commerce
- Esfera de influência: Onde decisões de negócio impactam
- Esfera de Atividade: O que realmente acontece no dia a dia

_Problema vs Solução_

Espaço do Problema (O QUÊ)

- clientes abandonam carrinho
- produtos ficam sem estoque
- devoluções são complexas
- marketing quer dados

Espaço da Solução (COMO)

- sistema de e-mail marketing
- API de controle de estoque
- Fluxo de devolução automatizado
- Analytics e dashboards

---

## O conceito de Domain-Driven Design

Eric Evans: Consultor de Software, observou que projetos fracassavam não por limitações técnicas, mas por falhas na comunicação.

_Os 3 pilares filosóficos do DDD_

- Foco no domínio central
  - [] "Vamos usar a arquitetura mais moderna"
  - [x] "Vamos entender profundamente o negócio"
- Exploração de modelos
  - [] "Analistas fazem levantamentos -> Devs implementam"
  - [x] "Modelagem iterativa e colaborativa"
- Linguagem Ubíqua
  - []"Traduzir" entre negócio e TI
  - [x]"Falar a mesma lingua em código e reuniões"

"Use o modelo como a espinha dorsal de uma linguagem. Comprometa o time a exercitar essa linguagem implacavelmente em toda comunicação dentro do time e no código."

---

## Diferenciando DDD estratégico e tático

_DDD Estratégico(O Mapa)_

- ONDE focar os nossos esforços?
- COMO organizar o sistema?
- COMO as partes se comunicam?

- Subdomínios
  - Quais áreas principais do negócio?
  - Qual é o Core? Supporting ou Generic?
  - Onde investir melhores talentos?
- Bounded Contexts (Contextos delimitados)
  - Onde estão as fronteiras naturais?
  - Como evitar conflitos entre times?
  - Que modelos são válidos em cada contexto?
- Context Mapping (Mapeamento de contexto)
  - Como contextos vão se integrar?
  - Quem é fornecedor, quem é cliente?
  - Que tipo de tradução é necessária?

_DDD Tático (O GPS)_

- COMO implementar cada parte?
- QUE padrões usar no código?
- COMO estruturar classes?

- Building Blocks
  - Entities vs Value Objects
  - Aggregates e suas fronteiras
  - Domain Services
  - Repositories
- Domain Model Patterns
  - Como expressar regras de negócio?
  - Como garantir invariantes?
  - Como lidar com complexidade?
- Arquitetura Interna
  - Layered Architecture
  - Hexagonal Architecture
  - Separação domínio/infraestrutura

## Quando usar o DDD?

Não use DDD se:

- Prova de conceito (POC)
  - Timeline: semanas
  - Objetivo: validar hipótese
  - Use: NestJs, Laravel, Rails, Django, frameworks opinativos.
- CRUD simples
  - Baixa complexidade de regras
  - Principalmente Creat/Read/Update/Delete
  - Use: Admin generators, low-code
- Sistema Temporário
  - Vai ser descartado em < 1 ano
  - Budget limitado
  - Use: Soluções prontas, Saas

"Se você esá em dúvida se deve usar DDD, provavelmente não deve (ainda)."

---

## Explorando a Linguagem Ubíqua

_Linguagem Ubíqua e descoberta do domínio_

Construindo a ponte entre negócio e código

## A torre de babel digital

O mesmo conceito, multiplos nomes:

_Carrinho de compras_

- Frontend: "cart"
- Backend: "basket"
- Banco: "shopping_session"
- Negício: "cesta"

Resultado: bugs, reuniões intermináveis e código incompreensível

## O que é linguagem ubíqua?

Uma única linguagem compartilhada

- Mesmos termos no código, conversas e documentação

Criada colaborativamente

- Não é o dev que decide sozinho nem o PO que impõe

Viva e evolutiva

- Não é documento morto, evolui com o entendimento

## O que não é linguagem Ubíqua (anti padrão)

- Não é linguagem ubíqua, simplesmente eliminar a linguagem técnica
- Não é usar portugues no código
- não é um dicionário de sinonimos

## Construindo o glossário

_Glossario Vivo_

- Wiki colaborativa/Markdown no repositório
- Criado pelo time todo
- Atualizado continuamente
- Próximo ao código

---

_Formato do glossário_

# Glossario AluraStore

## Carrinho de Compras

**Definição:** Container temporário onde o cliente adiciona produtos.
**Não é:** Pedido, Lista de Desejos, Favoritos.
**Código:** `CarrinhoDeCompras`, `ItemCarrinho`
**Banco:** tabela `carrinho_compras`
**Regras:** - Expira em 7 dias sem atividade - Máximo 50 itens

Cada termo deve ter: definição precisa, o que não é, mapeamento para código, regras e exemplos.

---

## Exemplos

_Ruins_

- Genéricos: Processor, Handler, Manager
- Ambíguos: Status (de quê?)

_Bons_

- Precisos: CalculadoraFrete, ValidadorCPF
- Claros: StatusPedido, StatusPagamento

---

## Governança da Linguagem Ubíqua

1.  Pessoas: Guardiões da linguagem (2-3 pessoas com rotação)
2.  Processos: Checkpoints em planning, code review e definição de pronto
3.  Ferramentas: Linters, Github Actions, Validadores Automáticos
4.  Cultura: Celebrar bons exemplos, gamificação, onboarding estruturado

---

## Identificando os especialistas de domínio

_Quem são?_

- Óbvios: PO, gerentes, analistas
- Ocultos: funcionários experientes
- Externos: clientes, fornecedores

_Quando envolver?_

- Descoberta Inicial
- Definição de termos
- Regras complexas
- Validação do modelo

---

## Entrevistas e Observação

_Entrevista_
O que as pessoas DIZEM que elas fazem

_Observação_
O que as pessoas REALMENTE fazem

A pessoa contar como é o dia a dia dela, ajuda na parte da entrevista

_Técnicas Eficazes:_

- Técnica do "última vez"
- Técnica dos "5 porquês"
- Técnica do alienígena
- Técnica da exceção

---

## Entendendo o EvensStorming

Workshop Colaborativo para descoberta rápida do domínio usando post-its coloridos.

Eventos do domínio -> Fatos relevantes que alteram o estado do sistema ou alteram algum estado do processo.

_1. Exploração Caótica_
Todos os eventos possíveis

_2. Timeline_
Ordenar cronologicamente

_3. Estruturação_
Validar termos e identificar fronteiras

---

## Explorando o conceito de domain storytelling

_Storytelling de domínio_
Ensina a contar histórias visuais do domínio usando pictogramas.

- Atores: quem realiza as ações;
- Objetos: Com o que interagem;
- Atividades: Ações realizadas.

_Exemplo de Domain Storytelling_
História: Cliente compra um produto

1. Cliente busca produto por marca
2. Sistema mostra produtos
3. Cliente seleciona produto
4. Cliente adiciona ao carrinho
5. Cliente informa CEP

Descobertas: cliente busca por marca, CEP antes do checkout

---

# Combinando as técnicas

EventStorming: QUANDO acontece

Domain Storytelling: COMO acontece

Observação: O QUE REALMENTE acontece

Entrevistas: POR QUE acontece

---

## Do domínio ao contexto

_O que são subdomínios?_

Subdomínios, seriam basicamente subdivisões do nosso domínio principal.

**Finalidade Própria**
Catalogo: organiza e busca produtos

**Regras Especifícas**
Precificação: margens, descontos, promoções

**Atores Próprios**
Marketing e Financeiro: atores distintos

**Vocabulário Distinto**
Produto: descrição (catálogo), SKU (Estoque)

_Mapeamento de Subdomínios_

- Catálogo: Gerencia produtos e descrições
- Pagamentos: Processa transações
- Entrega: Gerencia logística
- Cliente: Gerencia dados e preferências

_Subdomínios Core_

- Coração do negócio e razão da sua existência no mercado.
- Principal diferencial competitivo.
- Área prioritária para excelência e geração de valor.
- Ligado à missão e visão da empresa, exige investimento contínuo em pesquisa e desenvolvimento.

_Subdomínios de Suporte_

- Necessários para o funcionamento do core.
- Não é o diferencial principal do negócio.
- Requer customização moderada.
- Deve ser bem feito, mas não precisa ser revolucionário.

_Subdomínios Genéricos_

- Problemas comuns e já resolvidos pela indústria.
- Não oferece diferenciação competitiva.
- Soluções padronizadas e commoditizadas disponíveis no mercado.
- Candidatos ideais para compra, terceirização ou uso de soluções prontas.

---

## Implicações Práticas

_Core_

- Melhores Talentos
- Sistemas robustos, orientados ao domínio
- Experimentos e melhorias sempre
- Deploys com alta frequência

_Supporting_

- Times bons, mas não os mais experientes
- Sistemas sólidos e simples
- Deploys com média frequência

_Generic_

- Prefira soluções prontas
- Se precisar criar, siga os padrões do mercado
- Atualize quando for necessário
- Pense em terceirizar

## Erros de classificação

- Tecnologia como core
  - Confundir tecnologia (IA/Blockchain) com valor de negócio.
- Estrutura Organizacional
  - Classificar departamento (ex:RH) como subdomínio.
- Subestimar suporte
  - Classificar gestão de usuários como genérico, quando é suporte.
- Core muito amplo
  - Marketplace englobando vendedores e compras num Core Único

## Erros de estratégia de implementação

- Customizar Genéricos
- Terceirizar o Core
- Over-engineering em suporte
- Uniformizar estratégias de implementação

## Checklist de revisão

- Valor comprovado:
  - Gera diferencial em métricas (conversão, retenção, NPS)?
- Vantagem Competitiva:
  - Se copiado, perderiamos mercado?
- Ritmo de Mudança:
  - Frequência de mudança alinhada a classificação?
- Investimento Proporcional:
  - Investimento alinhado ao retorno?

---

## Heurísticas de Cortes

- Linguagem
- Ritmo de Mudança
- Regras Interdependentes
- Ator Decisor
- Usuário e Objetivo
- Qualidade de Serviço
- Fonte da Verdade

_Sinais de mau corte_

- Efeito dominó
- Guerra de Nomenclatura
- Orquestração Complexa
- Conflito de Ownwership
- Sincronização Excessiva

---

## Como contextos se conversam

Principios de Comunicação

- Independência: Falhas isoladas.
- Tradução: Adaptação de vocabulários
- Acordo: Contratos claros

Mecanismos de Comunicação

- Linguagem Publicada
- Camada Anti-Corrupção
- Eventos

Controle das Mudanças

- Lider x Seguidor

---

## Por que usar padrões táticos?

_Padrões Táticos_
Organizando o código com a linguagem do domínio

---

## Entidades e Objetos de Valor

_Entidades_
Conceitos com identidade e ciclo de vida:

- Identidade estável (ID natural/técnico);
- Regras de ciclo de vida encapsuladas;
- Igualdade por identidade

_Objetos de Valor_

- Imutabilidade
  - Não muda; substitui-se por outro valor.
- Igualdade por valor
  - Dois objetos com mesmos valores são iguais.
- Substituível
  - Pode trocar por outro equivalente.

Exemplos: Preço, CPF, Endereço, Período

---

## Implementando Agregados

_Agregados_
Cluster de Objetos que mantêm consistência juntos:

- Uma raiz como único ponto de acesso
- Fronteira Transacional clara
- Tamanho pequeno e focado

---

## Entendendo o Serviço de Domínio

_Serviços de Domínio_

Quando usar:

- Lógica que envolve múltiplos objetos e não tem "causa natural"

Caracteristicas:

- Sem estado, contrato claro, vocabulário do contexto

Exemplos: Cálculo de frete, política de preços, recomendações

---

## O padrão repositório

_Repositórios_
Abstração de persistência orientada a agregado:

- Interface no domínio
- Implementação na infraestrutura
- Métodos com intenção de negócio

---

## O padrão tático de eventos de domínio

_Eventos de Domínio_

Fato ocorrido: Representam mudanças importantes no domínio
Publicação: Emitidos pelo agregado após mudança
Reação: Handlers independentes processam o evento
