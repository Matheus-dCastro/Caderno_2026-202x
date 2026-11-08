****# Processos de Decição de Markov:

modelo matematica que descreve sistemas matematicos e estocaticos; => estacionario
	- estados, todas as estruturas possiveis
	- açoes possiveis de cada estado
	- recompensa valores associados a pares estados-açao
	- PDM finitos todos os pontos anteriores sao finitos os valores deles

modelo para orientar escolhar quando os resultados sao incertos **<font color="#ffff00">(em sequencia)</font>** um somatorio de possibilidades tanto esperança quanto o real;

### Componentes da PDm:

politica (pi)
define a probabilidaed de escolher uma açao em um detreerminado estado s

#### Propabilidade de Markov:
<mark style="background:#ff4d4f">Frozen laken</mark>

PM n tem o agente no ambiente
PDm tem o agente no ambiente

**Parametro de decisao e score**

# Aula 04:

Os algoritmos precisam achar os numeros do proximo estado => isso depende das policas de ações q nos definimos.
realizar todos os possiveis proximos

uma politica so é melhor q a outra se ela for melhor em todos os estagios

Equação de bellman => fazer por casos de substituição e distribuir os estados e probabilidade

# Capitulo 01:

#### O q define a qualidade de uma politica?

- achar a melhor resposta com a menor perca possivel;
- Se o agente conhecer previamente o ambiente o resto se torna trivial
- não-trivial quando: 
		- não tem info previa
		- ele deve interagir com o ambiente para aprender as politicas e tomar as melhores decisoes por si só (ou seja por tentativa e erro) <font color="#00b050">*Trial and error*</font>

## Estado VS Ação:

Descreve a condição/posição do agente no ambiente
ex de estado (State): 
	- uma matriz 3x3 o estado é a sua localização;
	- State Space; 
- dentando uma matriz de 3x3 dando 9 possiveis estado para o agente

ex de ação (action):
	- é se mover entre 5 possibilidades em cada celula

**Estados distintos podem ter açoes distintas**
=> nesse livro sera considera o caso geral em q todas as ações são possiveis em todos os estados

-> se o agente tentar ultrapassar a borda ele sera rebatido de volta (n é possivel sair espaço)

### Politica (Policy)

determina qual ação tomar em cada estado

#### Deterministica VS Estocatica:

**Deterministica:** em cada estado *Apenas* uma ação tem probabilidade de 1

**Estocatica:** pode escolher entre varias de acordo com certas probabilidades.


### Recompensa (Reward):

- sinal escalar de feedback retornado pelo ambiente 
	- negativa
	- positiva
	- nula

### Recompensa imediata VS Total:

+> nao podemos encontrar uma boa politica apenas pela de maior recompesa imediatamente em cada passo.

### Trajetoria

cadeia de ações, estados, recompensas gerada ao seguir uma politica.

### Retorno

basicamente as recompensas de forma acumulada é a soma das obtidas

### Retorno descontado

trajetorias infinitas (agente continua operando indefinidamente mesmo achando o alvo) a soma direta das recompensas diverge:

=> **Fator de desconto Y**
- garante a convergendia matematica da soma
- contrla a visao temporal do agente
- 0 = miope  -> maior peso as imediatas
- 1 visionario/clarividente -> recompensas funtura

**Episodio:** uma trajerotia q acaba quando atige o estado terminal
**Task eps:** possuem termino defindo ja
**Task continuas:** nunca chega o fim sozinha
**Unificação matematica:** podemos tratar de duas formas
		- estado absorvente: O estado é um e é alacansado dali o agente nunca mais sai dele
		- estado norma com auto-loop: trata o alvo como um estado comum onde permace parado rende recompesas
### Processos de descisao de markov:

O conhecimento do estado atual é suficiente para determinar o proximo estado independe dos estados passados.
- se o passado é fundamental para determial o estado futuro n é um processo de descisao de markov
- precisamos apenas do estado presente para determinar o estado de amaha

##### Tem dois tipos de modelo:
**Estacionario:** o modelo n muda com o tempo -> as regras do jogo nunca mudam mesmo com o passar do tempo (xadrez)
**Não Estacionario:** o moldeo muda com o tempo -> as regras do jogo podem mudar com o decorrer do tempo da partida

$\pi$  => define a probabliidade de uma ação acontecer em determinado estado
$\gamma$  => define o coeficiente de ganho de cada ação

**Uma cadeia de markov é quando o estado futuro depende exclusivamente do estado atual**

<font color="#ffff00">O valo de estado é usado para determinar a qualidade da politica em medio tempo</font>
-> para tarefaças episodicas: sem taxa de desconto
-> para tarefaças continuas: com taxa de desconto

=> esta terminal ou estado absorvente


# Equação de Bellman:

Gama é o futuro do babo
fazemos uma equação para cada ação possivel na quele estado

*devemos dividir em dois casos essas equações =>*
1. recompensas imediatas
2. recompensas futuras

quando temos o um caso estocatio ou seja nao determisitico devemos dividir nosso caso em duas ou mais partes e colocar o coeficiente de probabilididade de ser aquele caso e fazer as contas com base nisso 




**NOTA: fazer a questao da aula passada quando ele postar o material das aulas** 

# Aula do dia 24-08:

Valores de estado e equação de Bellman

para cada uma dos possivies estados teremos uma prob

=> Comparar par a par para todos os elementos para poder achar quem é o melhor caminho para a resposta -> para ser melhor tem q ser melhor q todos

**Otimilidade de Bellman:** é a mesmas coisa q a bellman normal so q eu tiro o max pos resolver as equações ou seja eu faço a comparação de forma mais imdiata para achar o melhor. 

*Deterministica goloza*

### Achar os pontos fixos de uma função:

normas da funções -> 2 para euclidiana, 1 para mahanta, inifinito é a de manhanta so q aplicando a max


0<gama<1


## MDP:

Usamos a equação de bellman para poder decisdir qual o melhor trajeto para nosso agente no ambiente, 

dividimos o meio em duas formas o meio

*Deterministico:* O proximo estado é totalmente dependende do estado atual
*<u>Não</u> Deternistico:* É um sistema onde apresenta multiplas posibilidades apartir do estado atual.

A equação de bellman resolver isso achando o caminho que maximize o ganho e diminua as percas no caminho.

Entrando assim no processo de decisão de Markov:
-> Divide em estado S e em ações A
e cada uma pode apresnetar na matriz combinações diferentes para dada ação tomada em cada estado => apresneta sistema de recompesas para o agente.


-> Em um ambiente deterministico usamos a equação:

$$Q(s, a) = r(s, a) + \gamma \max_{a'} Q(s', a')$$
-> Já em um meio nao deterministico usamos:
$$Q(s, a) = R(s, a) + \gamma \sum_{s'} P(s' \vert{} s, a) \max_{a'} Q(s', a')$$

$\pi(a|s)$ Representa a politica adotada em cada escolha nas ações do agente

==sempre cada estado depende APENAS do estado atual.== 

deve ter em memten o fator de desconto $\gamma$ sobre a ação tomada pelo agente. 

Quando a equação esta em função de $V\pi(S)$ a primeira parte sao é das recompensas imediatas q devem ser levadas em conta porem n sao elas q estamos querendo maximas e sim a segunda parte ou seja o segundo termo da equação q sao as recompesas futuras.

=> podemos separa essas duas partes em duas equações diferentes para facilitar


![[APRENDIZADO POR REFORÇO - Aulas-1788733017750.webp]]


#### Verificamos 4 ponto para uma politica ser melhor q outra:

**Existencia:** A politica otima existe
**Unicidade:** Ela é unica?
**Estocasticidade:** Ela é uma politica determistica ou estocastica
**Algoritmo:** Como é calculado os valores otimos e como é obtido a politica.


Quanto maior o valor de $\gamma$ mais o a politica sera corajosa ou seja o modelo irá se aventurar mais quanto menor o valor de $\gamma$ menos o modelo irar se aventurar

quanto mais perto do alvo maior os valores de retorno o oposto tambem é veridico.

se um estado precisa demais passos para chegar ao alvo seu valor é menor pq esta mais longe do "gerador" de pontos


### Algoritmos para achar Otimas politicas:

*Interação de valor*
*Interação de politica*
*Interação de politica truncada*

NOTA: Todos os algoritmos acima precinsam de conhecer previamente o ambiente.
-> Não são muito praticos para problemas muito grandes

### Interação de valor:

vem por meio do algoritmo do ponto fixo:

Ação q maximiza o valor ->

1. Atuliza a politica
2. Atualiza o valor

=> Monta uma tabela e seleciona os estado de maior valor





### Interação de Politica:

Ela não resolve a equação mas no lugar ajuda a convergir em uma otima politica
1. Avaliação de politica
	- Avalia o valor do estado de uma politica dada 
2. Melhoria de politica
	- Gera uma politica melhor que a anterior

=> a solução analitica n é usavel na pratica apenas teorica
ela assim com na de valor maximixa o aragumento ou seja busva o maior valor de forma gulosa
ela descide por um sinal de nova>= anterios

# Metodo de Monte Carlo

# Revisão em sala para prova da unidade 01:

-> A diferença entre as 3 formas de aprendizado de maquina: *Supervisionado, Não-Supervisionado, Reforço*
-> compontes de um ***PDM*** => divisão entre as ideias de ação e estado
-> Propriedade de Markov => 
-> Tipos de política: deterministica e estocatica
-> fromas de recomepensas => imediatistica ou total
-> Equação de bellman => o quao bom é está naquele valor de estado



# Revisão em casa para prova da 1°Unidade:

-> Oq é aprendizado de maquina: *é a forma com que um computador aprende apatir de uma experiência por meio de uma tarefa atravez de uma medida de desempenho.*


processo de aprendizado para classificação (Regreção logistica)
processo de aprendizado para predição (Regreção linear)
processo de aprendizado para resulução (reforço) => tomada de descição para realizar tarefaças em um espaço q pode ser deterministico(sempre a mesma saida) ou estocastivo(aleatoriedade)


estrutura de passos e ações pre-estabelicidas do q o agente pode executar e receber mas as descisões de tomar elas sao do agente/algoritmo ou seja aprende interagindo com o abinete recebendo um estimlo para reforçar aquela ação.

*Estado:* se refere a onde o agente está e define com ele vai tomar a próxima descição
*Ação:* refre-se ao q o agente pode fazer
*Political:* é a regra de descição q o agente irá usar para tomar suas descições ou seja , é uma função ou distribuição de probabilidade denotada por $\pi(a\vert{}s)$ 

### Processos de Decisão de Markov

$MDP = (S,A,R, P, \gamma)$ ela só depende disso para funcionar  sendo 
S -> conjunto de estados possiveis ou seja oq ele ainda pode ir 
A -> conjunto das ações 
R -> S -> $\mathbb{R}$ um map de recompesas para cada estado
P -> Probailiade de transição de um estado para outro dada uma ação
$\gamma$ -> fator de desconto da politica
$\pi$ -> S -> A ou seja é a politica do agente e como ele vai dado um estado atual vá proxima ação pelo agente 


Temos o objetivo de achar a melhor politica para o agente pode andar 
podemos separa nosso horizonte em dois tipos 
*Horizonte finito:* nossa quantidade de ações é finita  -> politica não-estacionaria
- uma contagem de quantos passo eu posso da ate chegar ao meu destino
*Horizonte infinito:* nossa quantidade de ações pode ser infinita para maximizar os ganhos 
- é estacionario ou seja não depende do tempo ou numero de passos 

Nesse processo temos uma função em somatorio q vai no maximo ate 1 q representará probabilidade de recompesa $r(s,a)$-> nao sabemos o proximo estado ja para $r(s,a,a')$ -> representa quando ja sabemos o proximo estado => ambas tratam do valor de recompensa para o agente 

#### Uma PDM -> PM quando fixamos uma politiva $\pi$ nesse processo 

- **O PDM (Processo de Decisão de Markov):** É o cenário geral onde o agente tem **liberdade de escolha** (várias ações possíveis em cada estado).
    
- **O PM (Processo de Markov) / Cadeia de Markov:** Acontece **quando a política é fixada**. Ou seja, se você fixa uma regra de comportamento ($\pi$), o agente deixa de "escolher livremente" e passa a seguir probabilidades estáticas de transição entre os estados.
		- **A relação com Bellman:** Para calcular o valor de um estado sob uma política fixa ($v_\pi(s)$), o PDM vira efetivamente um PM, permitindo que a **Equação de Bellman** monte um sistema de equações lineares para resolver esses valores.
		*No processo de transformar uma PDM em uma PM usamos bellman para pode achar um valor otimo para $\pi$* 


## Interação de valor:

vem do teorema do ponto fisico -> sempre garante q existe um ponto no espaço q sempre terá um ponto fixo em qualquer mapa sendo imposivel misturar e mudar a posição de todos os pontos de forma continua nunca mistura completamente falha sempre em um ponto 

*terá como objetivo achar $\pi *$*  ou seja eu quero achar a melhor polica para o cenario q estou

### Interação de polica:

nao resolve diretamente a eq. bellman porem ela leva a uma politica otima convergendo a eq. bellman

avalia a politica -> melhora a politica

- A iteração de política requer múltiplas iterações internas (avaliação de política). 
-  A iteração de política converge em menos iterações externas, porém cada iteração pode ser custosa. 
- A iteração de valor faz uma atualização mais simples, mas pode precisar de mais iterações para convergir. -> menos custosa

todas os altorimos interativos requem q seja o conhecimento do modelo do sistema/ambiente

### Metodos de diferenças temporais:

#### Algoritmo TD:




# Apresentação:

-> CliffWalking: Trata-se do problema do penhasco (usado para comparar diferentes algoritmos de controle) => dimenções 4x12 e penhasco fica entre o npc e o objetivo dele
a cada passo ele recebe -1 e caso caia ele recebe -100 usamos aqui recompensas negativas para mendir o custo de passos e de explocação do agente para q ele prefira realizar a tarefa de modo menos custos

pode ser inferido um caminho linha para controle do poder de explorar o ambiente e fazer o a gente chegar logo no destino, ou seja controla o quando o agente vai ser "safado"

_Esse dilema nos permite avaliar como a taxa de exploração (_$\epsilon$_) e a escolha do algoritmo (__On-policy_ _vs_ _Off-policy__) influenciam se o agente será 'destemido' e arriscará a borda ou se será 'cauteloso' e preferirá o topo._

### SARSA:

O nome desse algortmo vem por meio do anagrama dos 5 passos para formar a transição dos passos no ambiente:




1. Conceito: O SARSA é um método on-policy. Ele aprende o valor da política que ele realmente está executando (a ε-gulosa). 


2. A Fórmula: Mostre a tupla (Sₜ, Aₜ, Rₜ₊₁, Sₜ₊₁, Aₜ₊₁). Destaque: "O SARSA sorteia a próxima ação Aₜ₊₁ antes de atualizar a tabela Q. Como essa ação pode ser aleatória (exploratória), o agente incorpora o perigo de errar e cair no penhasco." 

3. Resultado: Por isso, a política aprendida e a trajetória gulosa do SARSA escolhem o caminho seguro pelo alto (15 passos). Ele prefere andar mais a correr o risco de tropeçar e levar -100.


4. Efeito dos hiperparâmetros:
 • Com ε maior (0.3), ele sobe ainda mais no grid (mais longe do penhasco). 
 • Com γ = 0 ou 0.5, há "miopia": como todos os passos dão -1, o agente não enxerga o objetivo e fica em loop.

