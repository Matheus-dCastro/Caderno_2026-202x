<mark style="background:#d3f8b6">=> Dimensão é o grau de liberdade que descreve um ponto (quantas variaveis de um vetor sao precisas para representar aquele ponto no espaço)</mark>


quanto maior a dimensao menor é a variabilidade


# Maldição da Dimensionalidade

Esse fenonimo acontece quando analisamos dados com varias features ou seja varias dimensões centenas ou milhares => não acontece em espaços de baixa dimensionalidade.

1- O esvaziamento -> o volume vai para as bordas
2- Concentração de distancias -> toda distancia entre pontos tente a ser iguais

## Volume de uma Hiperesfera

Como nessas figuras o volume se concentra nos cantos/bordas das imagens temos q 
para ML os dados se tornam extremamente separados/<mark style="background:#40a9ff">**Esparsos**</mark> a quantidade de dados para comprir o espaço precisa crescer exponencialmente


**Esparsidade**
n podemos usar algoritmos de distancia
tente a ouverfit
quanto maior as dimensões masi o volume da hiper-esfera é mandado para as bordas

**Concentraçã9 de distancias**

distancia euclidiana-> tem seu comportamento de formca critica
- A diferença entre o ponto mais proximo e o ponto mais distante tende a zero
- Vai existir um ponto na diagonal ou no enterno do ponto analizado tanto para menor e maior distancia q vai ser sempre a proxima maior e menor distancia
=> vetores com alta dimensão tendem a ser quase ortogonais
=> vetores proximos em baixa 
=> d maior -> vetores em diresões cada vez mais distintas
=> angulo tente a 90°

Isso implica no ponto de vista q todos os pontos ficam quase a mesma distancia

> Impacto:
> - k-means n consegue trabalhar para dividir os clusters
> - ao encontrar otimos locais ruins converge pois a distribuição espacial se dissolve



**Ortogonalidade Assintota**
Vetores aleatorios tendem a ser ortoganais entre si
direçoes distintas entre vetores a tender a 90°


# Como lidar com a maldição?

redução da dimensionalidade, de forma q preserve as estruturas mais importantes


## Benção de nao uniformidade:

muitas vezes os dados estao retrintos a subespaços ou varidade de baixa dimen
-> dimensionalidade intriseca é muito menor q a o proprio espaço

cada ponto é pertencente ao um grupo de vizinhos

## Autovetores e Autovalores 

estudar essa parte de matrizes de novo, livro de algebra e fazer algumas questoes so para relembrar 

-> usa a matriz de covariancia para fazer a redução em auto valores e auto vetores

- **Autovetores**: Representam as direções dos eixos no novo espaço de características. No contexto do PCA, eles são os **componentes principais**. Eles são ortogonais entre si.

- **Autovalores**: Indicam a magnitude da variância dos dados ao longo das direções dos autovetores.


### Manifolds:

espaço q em regiões pequenas se comporta como espaço euclidiano
podem formar um mapa de coordenadas entre o real e o espaço plano
reduz a dimensão preserva relações locais
pode capitar a geometria intriceca


## PCA
analise da componente principal usa uma matris de convariancia para reduzir o espaço vetorial em d-1 dimenções geralmente apartir de uma matriz de transformação usando autovetores e autovalores


=> a recosntrução da pca geralmente a depender do numero de autovetores usado para realiza-la pode n ser tao fidedigna 


### Eigenfaces com o LFW dataset

visao computacional, reconhecimento facial 
-> trata cada imagem de um rosto como um vetor separa pela escala dos pixes
-> captura a variançoes mais significativas em um espaço de baixa dimensionalidade
-> representao os ingrediente principais de onde qualquer rosto do dataset pode ser contruido
PCA é usado para encontrar subespaçoes de baixa dimensionalidade preservando a variancia

**PCA em matematicamente:**

indentificar um numero menor de variaveis correlacionadas => capturar padroes
maior variabilidade dos dados agrupando pela sua covariancias entre elas 

<mark style="background:#40a9ff">obteção das variaveis mais importantes</mark> 

#### limitações da PCA:
apenas captura relações lineares
se estruturar nao lineares tem poucas componetes podem ser mal representadas
conserva a variancia nao a separação de grupos
precisa passar pelo processo de normalização
baixa interpretabilidades
Outliers podem distorcer a direção de maior variância



# T-Distributed Stochastic Neighbor Embedding -> t-SNE


É uma tecnica de redução de dimencionalidade não linear bastante eficaz para datasets de grande dimensões. ele diferentimente da PCA ele tenta preservar a estrutura local dos dados => simlilaridade entre os pontos vizinhos tenta diminuir a divergencia entre distribuições de baixa e alta similaridade

- 1° constroi a probabilidade sobre pares de pontos de dados na alta dimensionalidade => pontos similares tem mais chance de serem escolhidos ja pontos nao similares tem uma baixa chance de serem escolhidos.
- 2° depois tenta reconstruir em baixa dimensão de mode similar nos pontos essa distribuição de similariedade

-> aqui queremos preservar as relações de vizinhança: a proximidade entres os pontos

-> converte distancias em probabilidade de similaridade
	a similaridade sera alta se no espaço original ele estao proximos 
	- cria duas distribuções:
		- uma no espaço original p
		- uma no espaço reduzido q
		o processo de otimização foca em reduzir a diferença entre os dois espaços, assim se preserva a estrutura local
modela por uma curva gausiana

-> essa similaridade é definida entre os pontos de xi e xj 

+> probabilidade condicional de q xi escolheria xj se os vizinhos fossem escolhidos pela proporção a sua densidade sob uma Gaussiana centrada em xi.
a variancia é dada pela diferença de i para j e de j para i

-- entropia pode ser usada para quantificar informações
	se a distribuição for:
			uniforme: entropia alta
			concentrada em poiucos evento: entropia baixa

Cada ponto x possui a sua propria variancia q define o seu alcance
usando a perplexidade(mede a incerteza da distribuição entre os vizinhos => numero efetivo de vizinhos considerados) hiperparametro fica entre 5~50 controlamos assim q regioes densas tenham um sigma pequeno ja regioes pouco densas teram sigmas grandes

H(p) => media da informação de eventos

ja baixa dimensionalidade geralmente em 2D e 3D a distrubição segue t de Student com um grau de liberdade => distribuição de cauda longa, mas cada ponto yi representa um xi no espaço de baixa dimensionalidade

> objetivo é q Q reproduza a relaçoes de locais descritas por P
> -> se P e Q forem semelhantes => relaçoes de vizinhança sao preservadas
> -> a difrença entre P e Q mede a distoção entre os espaços
> -> para medir a diferença usa KL tenta otimizar via minimização de<mark style="background:#fff88f"> divergencia de KL</mark>

distrbuição de Kullback-laibler -> pede a quantidade de informação perdida de P para Q durante a redução das dimensões esse é o parametro de <font color="#00b050">custo de usar t-SNE</font>

usar o gradiente desendente para otimizar os parametros de uma função de custo

- indica a direção de maior almento e sera otimizado no sentido oposto
- cada passo é ajustado dependendo da taxa do passo
- é o vetor das derivadas parciais 
- magnitude: o quanto  uma função cresce 
![[Aprendizado-1780780326033.webp]]

Otimização co  SGD é o processo de achar um Y similar de alta relação para iniciar de forma mais similar.


# Uniform Manifold Approximation ande Projection (UMAP): Notebook 09



ele se destaca por ser capaz de preservar a estrutura dos dados tanto em alta quanto em baixa dimensionalidade. => baseado em geometria Riemanniana e topologia algebrica

constroi uma representação topologica dos dados em alta dimensão e em seguida busca otimizar um embedding de baixa dimensão q sera estruturalmente equivalente

Topologia: uma caneca é o mesmo q uma rosquina
Topologia toroidal: uma coisa da uma coisa nela mesmo jogo do pac-man => uma rosquina

1. constroe uma estrutura de grafo levando encosideração k-vinhos de um ponto aleatorio => isso para cada cluster não é a distancia mais sim uma probabilidade de conexão
2. e leva para um conjuto fuzzy (conjunto simplificado e cada ligação deixa de ser meramente binaria e passa a ter peso) oq no manifold preserva a estrutura original so q em baixa dimensionalidade => otimização de embedding 

NENHUM PONTO DEVE ESTA ISOLADO, A CONFIANÇA DA VIZINHANÇA DEVE DECAIR SUAVEMENTE COM A DISTANCIA

Conectividade rigina => valor fixo independente da densidad
Conectividade Difusa => quanto mais denso menor o raio quanto menos desenso maior o raio 

![[Aprendizado-1780786051250.webp]]


UMAP minimiza a diferença entre Q e P
usa a entropia como medida de deissimilaridade +> a incerteza
penaliza conexo erradas com vizinhos errados


## Cross-Enropy:


Cross-Entropy mede a incerteza média de p quando usamos q para codificar os eventos É a média da "surpresa" segundo q, para eventos que de fato vêm de p


Geramos dois tipos de força sobre os pontos

uma de atração => aproxima os pontos com alta conexão
uma de repulção => afasta os pontos com baixa conexão ajuda a empedi q colapsem no embergs e faz melhora as chances de n caracterizar vizinhos errados

![[Aprendizado-1780786365602.webp]]

o empurra e puxa é no plano 2d

# Autoencoders e Representações Latentes: Notebook 10

### Neuronios artificiais

Continou -> Continua
calula combinação linear em seguida uma nao linear
produz uma ativação como saida

uma camada é vista como varias funções em paralelo
cada neuronio tem suas entradas aplica seus pesos e manda sua ativação

### Função de ativação 

define como sera a tranformação da saida de um neuronio
add nao-linearidade
cada função tem suas vantagens e suas limitações
a escolha da função afeta como um todo o modelo


#### Sigmoid:

reduz os valores reais entre [0;1]
para modelos probabilisticos
valores extremos geram gradientes pequenos

#### Tanh:

fica entre [-1;1]
cetragem no 0 ajuda em alguns modelos
tambem sofre de saturação


#### ReLu:

padrao em redes profundas (MLps, CNNs)
eficais computacionalmente e minimiza o vanishing gradient q afeta as outras funções
se a derivada for constantes e do lado posstivo => aprendizado estavel


## Em classificação:

A entrada pode ser representações numericas de caracteristicas
A saia geralmente é um vetor de probabilidades

## Em Regressão:

valores numericos continuos
busca relações entre entrada e saida
imagem f é os reais

# Limitações:

tendem a supor relações lineares de entrada e saida
N consegue entender padrões complexos e nao lineares
sua fronteira de descisão fica em retas 2D ou em hiperplanos nD
Sofre de XOR 

=> para resolver os problemas isolados de um neuronio utilizamos -> REDES NEURAIS

Aprender nao linearidade em camadas intermediarias

## Multiplas camadas:

Cada camada realiza transformações parametrizadas seguidas de função de ativação nao lineares assim podem aproximar qualquer mapeameto não linear
a pronfundidade da rede permir modelar coisas complexas e representa-las em hierarquia

-> feedforward: sequencia de combinação de funções
=> a profundidade da rede é o numero de funções
=> termo central -> abstração: coisas complexas sao geralmente formadas de coisas simples combinadas fazer analise de forma hierarquica

### Camadas ocultas:
treino supervisionado: ajudatamos f(x) para aproximar f*(x)
hidden layers **não é especificado nos dados**
ele descide como vai usar essas camadas 

O ajuste dos pesos é feito focando em reduzir mais rapido os custos => a gradiente indica o quanto a função varia pelos pesos

### Função custo

mede o erro entre a saida prevista e o valor real 
gia o aprendizado via otimização
define o objetivo durante o treino pelo qual deve minimizar

=> otimização ocorre focando em: Gradient Descendente 
	- mexe nos parametros passo a passo 
	- ve para onde esta o maior valor de crecimento 
	- descemos os valores no sentido oposto do crecimento

## Backpropagation:

- o erro é propagado da saida para entrada 
- aplica tambem a regra da cadeia
- pesos tambem seguem o processo de otimizar acima 


# Autoencoders:

> reconstruir a propria entrada

Codificação interna dos dados
 ===> Composto por encoder, espaço latente e decoder

#### Espaço latente:

representação de forma comprimida dos dados
pode mostrar tanto os clusters quando oq os formaram
baixa interpretação
bom para ve downstream tasks

#### Espaço latente:

codificador: mapea um dado de entrada para um vetor dentro do espaço
decodificador: recebe o vetor e tenta mapea-lo de volta para a origem com o minimo de perca

#### Função custo:

quão bom esta a reconstrução da entrada
MSE
varia conforme o tipo de dados
o processo de redução foca em preservar informações relavantes

### Aplicações:

- remoção de ruidos
- extrair features


## Etapas do uso dos autoencoder:

No processo de treinamento, iteramos por 20 épocas. A cada iteração:

1. Achatamos as imagens de entrada de formato $28 \times 28$ para vetores 1D de 784 elementos.

2. Executamos a passagem direta (forward propagation) para obter a reconstrução.

3. Calculamos a perda de reconstrução (MSE Loss) contra as imagens originais limpas.

4. Realizamos a retropropagação (backpropagation) e atualizamos os pesos com o otimizador Adam.

quando a muitas dimensoes e n podemos plotar diretamente pode utilizar o t-sne para reduzir as dimençoes 

+> se o modelo conseguir fazer interpolação no espaço é pq esta bem treinado


## Denoising Autoencoders (DAE):

pode reconstruir uma entrada limpa apartir de uma versão corrompida com ruido de forma intensional
o modelo recebe a imagem com ruido e passa ela para o espaço latente e tenta reconstuir a imagem se ruido

nao aprende por simalaridade e sim a estrutura geometrica e a topologia onde reside os dados originais (entao tenho q passar para ele aprender a imagem original antes do ruido) oq passamos como x é a com ruido e y é as sem ruido 

o teste passa imagens q ele nunca viu e depois compara
1. imagem de referencia (Limpa)
2. as com defeitos
3. oq ele tentou reconstuir

<mark style="background:#ff4d4f">O interecesse de usar essa esse metodo é a organização dos clusters no espaço latente </mark>

# Embeddings: Notebook 11

Transforma qualquer coisa em um vetor e mapea esses vetores para areas semelhantes dentro de um espaço vetorial

- a linguagem numerica da IA 
traduz significados para numeros
