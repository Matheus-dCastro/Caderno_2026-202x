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

uso do gradiente => vetor das derivadas parciais do custo em relação a cada paramentro escolhido pelo modelo apontando para direção de maior  crescimento -> aponta para o crescimento do erro do modelo

o Gradiente *Descendente*  funciona atualizando cada valor por cada passo q o modelo usa na direção oposta ao do gradiente ate q o custo do modelo parar de cair -> usa para tentar dinimiuir o erro do modelo


**O passo para esses dois casos é usado apartir do hiperparamento da taxa de aprendizado do modelo**
-> ==sendo esse o valor mais senssivel durante o treino do modelo==

**A parada é oq define o numero maximo de epocas ou o custo abaixo de um limiar**

quanto maior a taxa de aprendizado, mais a chance do modelo ser burro quanto menor mais a chance dele decorar 

a regreção logisca pode ser usar para classicar as coisas em classes e preve essas classes
a regressao linear pode ser usar para prever valores e classificar esses valores

#### A função sigmoid:

a função opera entre -1 a 1 pela derivada da probabilidade da entradas
-> a saida vira probabilidade
-> a derivada é barata

**Fronteira de decisão:** recorte de um hiperplano para clusterizar os dados recebidos 
**Verossimilhança:** quão plausivel é este modelo (o quanto esse modelo tem de qualidade ou qual seria a qualidade desse modelo)


*Estimação:* escolhemos parametros para aumentar maximizar a verossimilhaça


para resolver problemas com hiper planos podemos 
ou aumentar o hiperplano e achar um forma de passar a faca nele e achar um reta q o desenhe ou podemos dobrar os dados assim iremos achar uma resposta sem precisar gasta processamento subindo os dados

separamos o neuronio em dois a parte dos parametros da parte de ativação -> que descide o tipo de saida 

Conhecer os parametros de origem pode ser util para comparar no final oq cada metodo recuperou
=> usa aqui bastante o MSE 
quando pegamos a matriz de solução add uma matriz de 1 e multiplicamos pelo bias(vies) oq faz trazer ele para dentro do mesmo vetor $\theta$ 

como as matrizes sao inversiveis as condiçoes tornam inviavel o metodo para milhes de parametros em uma rede neural

os valores de vies add nessa matriz ficam proximos dos dados de geração mas a diferença é dada pelo ruido palicado 

O logit percorre toda a reta real e a sigmoid traz esses numeros de volta a serem probabilidades

## Redes neurais

#### Inspiração neurocinetifica:

**Entrada:** as n partes de um vetor X
**Pesos:** será um por cada tipo de entrada medindo o quanto é significante para a informação final 
**Vies (bies):** desloca as coisas sem depeder da entrada
**Ativação:** uma função aplicado ao numero Z

As camadas de neuronios possuem parametros proprios cada um com seu vies e nada entre essas camadas é compartilhado -> **CAMADA DENSA OU FULLY CONNECTED**

as camadas ocultas sao camadas desensas q formam representaçoes *intermediarias* da entrada q n da para voltar e saia é a parte q o modelo devolvo do q ele produz

Só é espeficicado da primeira camada e a saida dos dados ja processados mas nada entres eleas

o uso da camada da função de ativação se da pq varias comadas lineares montam outra saida linear e o papel de ativação é impedir justamente q as matrizes se juntem em uma unica representração

-> sigmoid= entre 0 e 1 -| vem de logistica e sai como probabilidede
-> tanh= entre -1 e 1   -| da a camada seguinte valores de media nula

tanto a sigmoid e tanh tem derivadas baratas de se produzir
-> ReLu= entre 0 e $+\infty$  com a ReLu zera a parte negativa mante a parte ativa da rede q é somente realemente necessario para gerar o melhor conjunto de resposta do modelo


a leaky da uma leve indicativa para o lado negativo ja a gelu é mas como uma curva zerando o lado negativo ao poucos => a ReLu ainda é o padrao de mais moderno no mercado 

as camadas de redes multicamadas eles sao capazes de setar os proprios pesos assim a rede é capaz de escolher oq cada parametro irá representrar difente de antes q quem definia isso era quem desenhava/criava a rede oq além de mais autonomia traz mas desempenho aos modelo pois agora todas as camadas estao conectadas a todos os tipos de entrada de dados 

O forward pass é o processo dos dados passarem cama a cama até produzir uma resposta 

o broardcast é o processo de repetir o uso da matriz de vies porem se construir ela apartir de um matriz de 1s

pega os logits coloca a um exponensial e depois normalizar pelo soma -> produs as K classes

ele passa por
	exponecial -> invariancia(processo da soma) -> estabilidade(subitrai o maior logit)

quando a informação de um resultado cresce quando a probabilidade dele cai

**O backpropagation:** se trata da regra da cadeia aplicada diretamento no forward pass
	- a 1° guarda as ativações e a 2° passagem aplica a derivada no processo
	- como o custo de voltar aplicando as derivadas custa quase o mesmo q guarda as coisas de ativação torna viavel treinar grandes redes

_Em Resumo_ uma camada oculta ela opera sobre varias matrizes lineares sobre funções de ativação n lineares e é escrita como um grande produto de matrizes

-> a softmax nos devolve a distrubuição dos dados e a cross entropia compara com os rotulos as saidas dos modelo

### Backpropagation:

-> **Custo:** A função de perda mede o erro do q o modelo preveu errado
	- os pesos variam 
	- o exemplos de treino sao **in**variavies
	- e foca em achar pesos q dexem o menor possivel o custo


##### Formas de diferenciação:

**Simbolico:** aplica na expreção -> a expressão é refeita a cada mudaça
**Numérico:** duas avaliações por peso e o resultado é aproximado -> pertuba o peso e ve o custo
**Automático:** percorre um grafo -> guardao o valor do forward


 *o resto do conteudo é baseado no metodo automático*

cada fator é a derivada de uma etapa
as cadeias ficam longas com quanto mais etapas encadeadas entram oq faz o produto ganhar mais fatores 

a volta do forward é a multiplicação das derivadas por um fator por etapa (aqui é o inicio do backpropagation)


***Fatores*** -> em relação a $W$ 
- 1°depende apenas f.perda escolhida
- 2° é a derivada da ativação avalianda na etapa de pre
- 3° é a derivada da pre em relação aos pesos (a propria entrada)


***Fatores*** -> em relação a $b$

- 3° é a pre q depende do vies com coeficiente igual a 1 pq sera uma soma
- **Conta reaproveitada** o produto entre o 1°e o 2°fator serve para o peso e o viés

### Otimizadores:

Minimo local: o ponto (passo de aprender) fica proximo e cresce em qualquer direção igualmente
Plato: n diverge muito e o ponto n chega a esta em um minimo -> avança muito poucoo
Vale: crece para em uma estremidade mais q outra o ponto fica no centro do vale ->
Sela: o ponto n esta no minimo local e o formato fica com se fosse um chips de batata e o passo se anula

curva para cima positiva 
curva para baixo negativa
curva reta nula


a depender do angulo terá uma movimentação dos dados difetente a depender de como analisemos podemos ter uma curma mais ou menos asentuada e até diferente para o modelo se comportar 

em um estado de minimo local o passo converge pense em um prato para cima

em um estado de maximo local o passo diverge pense no mesmo prato so q de cabeça para baixo

sinais oposto o passo se anula pense na sela de cavalo

proximo a zero será o platô pense em um pato e o quando ele anda devagar e passo fica igual -> baixo

**Batch** o gradiente sobre todo o volume dos dados se da de forma determinisitca e o passo estabiliza sobee o minimo -> cada passo se torna caro em um conjunto muito grande

**stochastic** o gradiente q vem de um ex sorteado tem maior variância e n fica estabilizado no minimo

**Mini** quando vem de uma amostra provente de um sorteio, usado para o regime de treino e com a memoria limitada do acelerador

#### Momentum 

O momento guada uma media das interações anteriores e seus caminhos

-> Adam combina a ideia do momentum em guardar o caminho da interações do gradiente descendetem como o MSE (Ambas as medidas começam em zero e depois se normalizam)

*Himmelblau:* serve para ver a trajetorio de um problma cabendo a visualização em um grafico possue 4 minimos todos com o valor zero
cristas e pontos de sela

basicamente se escreve em ordem o numeros debaixo para cima pela len deles eu vou ter do mais lento ao mais rapido com as diferença entre seus comportamentos

# Aula do dia 19/10:

Detection object: passamos um oq foi achado em um box (como é um jogos) para q possamos fazer o fining tuning dos objetos para dentro do modelo e ele ja treinado clusterisar e tentar dizer oq o objeto passado é

# Aula do dia 21/10:

### Seguimentação de imagens:

processo inverso de se fazer um poling
-> oq ele faz é passar cada pixel a ser um canal usando cross entropia nas imagens geradas.

mesmo com uma baixa aparição na imagem modelos q o nunca nem viram essa class vao ter um bom acerto por aquela fração da imagem ser tao baixo.

é possivel usar um IoU aplicado em pixel n pelas classes.
da para aprender o objeto n apenas fazer um clustering diferencial do q o k-men q seria algo mais sistematico.

# Revisão para prova:

