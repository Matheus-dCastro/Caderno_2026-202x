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
		
H(p) => media da informação de eventos

ja baixa dimensionalidade geralmente em 2D e 3D a distrubição segue t de Student com um grau de liberdade => distribuição de cauda longa




tenta otimizar via minimização de<mark style="background:#fff88f"> divergencia de KL</mark>

distrbuição de Kullback-laibler -> pede a quantidade de informação perdida de P para Q durante a redução das dimensões

