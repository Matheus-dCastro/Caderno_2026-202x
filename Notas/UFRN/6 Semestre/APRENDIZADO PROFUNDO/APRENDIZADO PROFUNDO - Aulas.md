Como formar as informações atravez dos dados e saber identificar as coisas;
-> Abstrair principal causas;sintonização

task, performace, experience


- separação treino validação test implanta sintonização 

Representation learning;

# Aula do dia 12/08

### Revisão e intro a pytcho

``` python

s = torch.tensor()
s.ndin # informa o numeroa da dimencoes do tensor

randn isso faz com que use uma gausiana com devio padrao igual 0

o mean n pode ser acessado pelo type int diratamente quando estamos trabalhando com tensor apenas pelo tipo float

view serve para mudar o formato mas n mudar na memoria o var q passei

x = torch.arange(12) # vetor com 12 elementos
passar o -1 no resheape ele competa as dimençoes do vetor dividindo pelo outro numero q eu passei




```

# Aula 03

### Revisao de calculo e algebra + probabilidade:

Probabilidade +> determinismo e incerteza linguagem do q nao sabemos -> yugioh

**Frenquntista:** probabilidade é a frequencia realtiva do evento sobre a repetição do evento.
**Bayesiana:** sobre cresça, probabilidade é o grau de crença sobre o evento, daod o conhecimento disponivel.

revisao da materia de tetso
revisao de calculo

vetores sao representações de data point(as coordenadas sao os valores de cada feture)

Como o numero é retornado define ja a relação entre dois vetores: 

**positivo:** essa projeção as direções são semelhantes e se colocar um sobre o outro tem o mesmo sentido
**negativo:** direções opostas, projeção aponta para o sentido aposto
**ZERO:** são ortogonais nenhuma parte de um é projetada no outro 


# Aula 04:

Modelos lineares: deve satisfazer duas propriedades:
	- A transformação da soma é igual a soma das transformações
	- escalar a entrada escala proporcionalmente a saída
	=> o modelo supoem que a saida é uma combinação linear das entrada mais um deslocamento
		os pesos dizem o quanto aquela feture pesa(é significante) para formar aquela saida
		o vies desloca a saida quando todos os pesos são nulos
		a superfice da resposta é sempre um hiperplano no espaço das fetures
		A **Fronteira** é sempre d-1 dimensoes sendo d o numero de dimenções(caracteristicas) dos dados
		-> na pre-ativação da função é onde a parte linear e unico lugar em que vai aparecer
		-> na função é onde add a parte não linear do modelo e é aqui q descide qual tipo de saida o modelo irá produzir.
	
Gradiente descendente extocatico
Regressao logistica

Definição de neuronio => modelo linear com uma nao lineariedade no final com pesos, para produzir a saida


# Redes Neurais:

pre-ativação -> ativação => determina a imagem de saida

### Limites dos modelos lineares:

deformar o espaço para achar um hiperplano q separe perfeitamente ou quase os dados
cada peso de cada neuronio é idependente e cada peso por cada neuronio cria uma nova representação da entrada

+> introduzir n linearidade
sigmoid = para saida probabilistica
tahh = para saidas de ecopo de -1 a 1
relu = para saidas lineares -> zera o lado negativo e deixa o positivo intacta 


#### Saturação e Gradiente:

satuação: pre-ativação o grandiente a derivada tende a zero

### Teorema do aproximador universal

pode ser continua e descontinua contado q esteja em um espaço medio compacto

# Aula do dia 31/08

Revisão de tensor inicial

Revisar OO, revisar tensorflow, revisar estrutura de camadas de um neural network,

# Aula do dia 14/09
### Estabilidade e Treinamento:

**scaling:** esta preoculpado em fazer a normalização das escalas muito distintas => normalizando logo nas entradas 
***liner -> BN -> ReLu*** a ordem mais aceita para as camadas de ativação. 
<font color="#00b050">queremos sempre evitar picos</font>  
**Clipping por normal e valor** tenta evitar a exposisão do gradiente limitando o tamanho maximo do vetor reduzida tambem o custo -> Durante o treinamento da rede neural.


# Aula do dia 16/09:

no processo de zera as coisa => como se parace de fazer os neuronios vissar com as coisas
*L2:* tende a condesar as coisas no ponto zero mais n zerar
*L1:* vai levar varias features a zero e ficar relamente somente com oq é mais relavante

*adamW:* faz com que ele reduza erro de validação e serve para otimizar o aprendizado do modelo
*dropout:* para reduzir a redundancia -> aumenta a variancia dos dados



# Revisão para prova da unidade 01:

#### Revisão matematica:
representramos dados como vetores assim podemos representar dados muito complexos de maneira simples e estruturada, oq permite a mdelos serem mais eficiente na hora de interpretar dados.
as matrizes sao dataframes q ajudando a tornar o uso desses dados mais leves desde numericos literais imagens e afins

atravez dos espaços vetoriais podemos abstrair a ideia de aproximação entre os pontos oq ira convergir na ideia de um RAG assim ideias parecidas tenderam a se acumular mais proximas uma das outras (a distancia entre vetore e seus angulos passam a ser dados de analise para o modelo)

- **Combinação Linear e Subespaço Gerado (Span):**
	- **Combinação Linear:** É a soma ponderada de vetores ($c_1 v_1 + c_2 v_2 + \dots + c_k v_k$), onde os números $c_i$ multiplicam (esticam, encolhem ou invertem) cada vetor antes de somar.
	- **Subespaço Gerado:** É o conjunto de **todas** as combinações lineares possíveis que aquele grupo de vetores consegue formar. É todo o "território" (linha, plano 2D, volume 3D) que você consegue cobrir brincando com esses multiplicadores.
	- **Conexão com Redes Neurais (Camada Densa):**
		- Uma camada linear apenas calcula combinações lineares das entradas, onde os **pesos ($W$)** são justamente esses coeficientes.
		- Se você empilhar várias camadas lineares puras sem ativação no meio, o resultado continua sendo apenas uma combinação linear (a rede fica presa no mesmo subespaço plano).
		- **Por isso a não-linearidade (ReLU, etc.) é obrigatória:** ela quebra essa restrição e deforma o espaço para a rede conseguir separar dados complexos.

essas camadas fazem necessario q eu coloque uma camada de n lineareidade para aumentar a variança das probabilidades do emberdings

**Norma:** mede o tamanho do vetor ou seja o tamanho de sua informação
**Distancia entre vetores:** mede o quanto duas informações estão proximas ou o quanto elas se diferem no espaço das features
-> 
	Norma:
		- L2, Euclidiana: distancia em linha reta 
		- L1, Manhattan: deslocamento em uma grade
		- L $\infty$, Chebyshev: a coordenada que mais separa
*O numero devolvido pela operação ja classifia a relação entre os dois vetore (as contas são feitas em tuplas de pares)*

**Zero:** ortogonaiz
**Positivo:** direção semelhante
**Negativo:** direções opostas

#### 03 Modelos Lineares:

**Linearidade:** 
	- *Aditividdade:* a soma das transformação é igual a transformação das somas
	- *Homogeneidade:* Escalar a entrada escala a saida igualmente

**Supõe que a saida é uma combinação linear das entradas mais um deslocamento.**

A fronteira entre os dados é sempre um hiperplano.

O modelo opera com 3 pontos importantes:

Entrada
pesos
vies

*Pré-ativação e ativação:*

Pre: lado linear do modelo é onde passamos os parametros
ativaçãao: a parte não linear que decide q tipo de saida o neuronio irá produzir


Na ativação pode trabalhar com duas funções
a de identidade onde sera qualquer valor real -> regressao linear
sigmoid trabalhar entre 0 e 1 e faz uma regressão logistica

### Função de custo: erro quadratico médio

o custo opera sobre um número ao quadrado e o modelo erra sobre esse conjunto inteiro

ele faz isso ao quadrado para q possa penalizar erro ainda maiores mais q proporcionalmente e elimina o residou do sinal

e usa a media para tornar o valor de erro comparavel entre os conjuntos de sizes diferente

# Parametros