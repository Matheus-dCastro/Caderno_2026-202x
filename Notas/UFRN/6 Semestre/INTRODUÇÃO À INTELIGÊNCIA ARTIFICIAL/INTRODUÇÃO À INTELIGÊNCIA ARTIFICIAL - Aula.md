# Aula 03 - Agentes:

Ambiente >- sensor -< action -> ambiente

Quando um comportamento n te um clasuara de parada => Clasura erradica (**Irracional**)
*<font color="#ffc000">Medida de desempenho</font>*

### Principios da Racionalidade em IA:

- media de desempenho que define o criterio de sucesso
- o conhecimento previo que o agente tem do ambiente
- as ações q o agente pode executar
- a sequência de percepções do agente ate o instante atual

Mapiar o ambiente e seus limites
-> regras n gatante q crie racionalidade;

#### Racionalidade != Onisciência

maximizar o desempenho não garante soluções otimas(oni)

### Modelagem de agentes racionais

parece com levantamento de requisitos de engenharia de software;
<mark style="background:#affad1">Medida de desempenho (P), Ambiente (E), Atuadores (A), Sensores (S)</mark>

#### Tipos de ambiente:
- Totalmente observavel vs parcialmente
- Agente unico vs multiagente
- deterministico vs estocastico
- episodico vs senquêncial

### Estrutura do Agente:

agente = arquitetura + programa (modelo)


# Aula 04 -

### T#eoria dos grafos:
tarefas de busca espacionalmente definida

-> Representação do ambiente: espaço de estados, agentes baseados em objetos

cidade = vertices
estradas = arestas

#### Estrura de Agente:

#### Arvores de Busca:

**Tipos de busca:** largura, profundidade, 

# Aula 05 Resolução de problemas com metodos de buscas:

o algotmo da estrela pode ser interpretado como uma versão com um plus do da busca gulosa
um no ja fechado pode ser reusado a depender do estado atual
<mark style="background:#9254de">euristica dimisivel </mark>

# Aula 07: Busca em Ambientes Complexos parte 02:

Não possue o ambiente mapeado -> n tem conhecimento sobre todos os dados ja q parte dele é inserido em tempo real por ex
*nem sempre excolher de forma imediatista* 
-> dar pesos para aumentar a probalidade q estão se saindo melhor no momento porem ainda é feita uma escolha aleatoria

*algoritmos evolutivos e geneticos* 
-> segue a mesma ideia da genetica tentando pegar os melhores projenitores de cada rodada dos algoritmos.


# Aula 08: Laboratorio pratico

# Estudo dirigido e Revisão para prova:

-> campo da ciência do desing de agentes
=> **Fromas reflexo de um *Agente*** 
		- Reflexo **Simples**
		- Reflexo **baseado em modelo**
		- Reflexo **Objeto**
		- Reflexo **Utilidade**

podemos ter algumas abordagens:
*Não informada:* explora sem ter conhecimento previo
*Informada:* Utiliza conhecimento previo (heuristica)
*Local e de otimização:* funciona como um algoritomo de busca em profundidade ou em largura
*Adversarial:* seta o objetivo no player e faz o npc se mexer atraz do player

Filosofia: Conceitos como a mente como máquina, conhecimento e ação. 

Matemática: Lógica formal, teoria da probabilidade, algoritmos, computabilidade e intratabilidade (problemas NP-completos). 

Economia: Teoria da decisão, teoria da utilidade, teoria dos jogos, otimização de operações e o conceito de satisficing (encontrar soluções "boas o suficiente"). 

Neurociência: Entendimento do cérebro, neurônios e processamento de informações. 

Psicologia: Estudo do pensamento e comportamento humanos, cognição e processamento de informações. 

Engenharia da Computação: Desenvolvimento de hardware (computadores digitais, paralelismo massivo) e software (sistemas operacionais, linguagens de programação) que tornam a IA possível 

Teoria de Controle e Cibernética: Foco em sistemas auto-reguláveis e otimização de funções de custo


#### Tipos de agentes:

**Completamente** tem todas as infos acessiveis
**Parcialmente** tem partes das infos n acessiveis
**Discreto** o estado e as ações são finitas
**Contínuo** o estado e as ações são infinitas (só aumentam com o passar do tempo)
**Episodico** suas ações n dependem do estado anterior
**Sequencial** as ações influênciam tanto o ambiente quando as proximas escolhas
**Estatico** o ambiente n muda com o tempo 
**Dinamico** o ambiente muda com o tempo

![[INTRODUÇÃO À INTELIGÊNCIA ARTIFICIAL - Aula-1790106483587.webp]]

**Agente baseado em tabela** ele monta uma tabela com todas as ações possivesi para todas as sequências perceptivesi possivel.

**Agente reativo simples** 


# Busca Adversarial e MCTS

# Aula 10:

mundo wumpus: => agente de busca, agnete baseado emconhecimento analisar um ambiente pre definido ou estocastico (muda) casos de games para fazer a ia trabalhar em um ambiente

o cicio tell -> adk -> tell

# Aula do dia 19/10
#### Agentes logicos wumpus *laboratorio*:

-- implementação de como saber se esta safe ou n aquela casa e como ele interagi com o mundo
-- Agente logicos sao conservadores, mas seguros para manter em mundos estocasticos

# Aula do dia 21/10:

algoritmo baseados em temora "bayes" quase dado o conhecido qual a chance daquele conjunto eu obeter x


# Aula do dia 26/10:
### Laboratorio_Agentes_Probabilisticos_Wumpus:
