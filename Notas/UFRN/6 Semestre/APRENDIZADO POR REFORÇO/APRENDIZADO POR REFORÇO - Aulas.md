# Processos de Decição de Markov:

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

# Equação de Bellman:

Gama é o futuro do babo
fazemos uma equação para cada ação possivel na quele estado

**NOTA: fazer a questao da aula passada quando ele postar o material das aulas** 

# Aula do dia 24-08:

Valores de estado e equação de Bellman

