# DBSCAN

nesse vai por densidade não apenas pela distancia de um ponto com o outro.
usamos a acurácia para medir a eficiência do modelo.

# Metricas de medida de desempenho

##### Shilhouette Score/plot para visualizar como os bichos se comporta de forma ordenada 
- cluster que minimiza essa distasia quanto menor melhor ja a coesão deve ser menor para melhor agrupar ja q ela mede a distancia entre o clusters vizinho.

##### Davies-Bouldin Index (DBI)



# Notebook 01 - Fundamentos de AMNS ->

### Algebra Linear e Representações de Dados:

Assim como aprendizado de maquina supervisionado ele utiliza algebra linear como base teórica junto com partes de estatisca e probabilidade (k-means e Knn por exemplo são algoritmos que vimos ate agora nas aulas).


Usamos vetores para representar alguns dados e realizamos transformações lineares para poder manipular e tronar os dados mais eficientes. Nesse contexto os vetores e espaços vetorias representam justamente as dimensões (quantidade de colunas ou multivariaveis) => podemos ter n-dimensões.

#### Vetores como Representação de Dados:

-> um vetor é a forma fundamental de representar uma amostra(exemplo, observação) do conjunto de dados.

<mark style="background:#ff4d4f">Features:</mark> São as colunas/atributos do dado basicamente uma ou suas características e a quantidade de features define a dimensionalidade do gráfico.

+> reprezentar dados classificatorios de forma numerica.



# Matrizes:
Representação de varios dados (vetores) em um unico espaço vetorial

- **1D (vetor)**: `v[i]` → acessa o elemento na posição `i`.

- **2D (matriz)**: `A[i, j]` → acessa o elemento na linha `i`, coluna `j`.

- **3D (tensor)**: `T[i, j, k]` → acessa o elemento na posição `(i, j, k)`.

- **nD (tensor de ordem n)**: `X[i1, i2, ..., in]` → acessa o elemento na posição indicada por todos os índices.

<mark style="background:#d4b106">Reduções de matrizes</mark> Mudança de base, soma de matrizes, Media total, Soma/media por coluna/linha axis=0/axis=1

```python


@ # => denota multiplicação matricial


```

# Distancia VS Similaridade:

Distancia é a diferença entre dois vetores (dados)
Similariedade é mede a orientação(angulo) independentemente de sua magnitude

varia de -1 (opostos) 1 (similares) 0 representa ortogonalidade.

## Encontrar grupos: 
Significa basicamente encontrar os clusters estrutura inerente em dados (não rotulados)  separamos com base nas caracteristicas mas n rotulamos com A ou B tipo e sim apenas juntamos parecidos com parecidos

Usamos sempre como base inicial Distancia Euclidiana

# Centroides

É o ponto medio entre todos os pontos de um clusters => media de todas as coordenadas dos pontos cendo meio q uma posição central.

algoritmos simples layzer como o KNN sofre com um conjuto de dados com muitas dimensões 

=> outros senarios em q o KNN sofre são 

- E se um cluster tiver o formato de uma lua ou um anel?

- E se os clusters tiverem densidades diferentes (um muito espalhado e outro muito concentrado)?



# K-means:


Busca minimizar a variancia intra-clusters, conhecido tambem como inercia ou soma dos quadrados => WCSS: within-cluster sum of squares.

#### Passo interativo de otimização: 

Usa a expressão -> Expectation-Maximization (EM)
- 1 distribuição: cada ponto de observação é atribuido a um clusters cujo ira fazer parte do centroide mais proximo => <mark style="background:#affad1">define limites de decisão</mark>
- 2 atualiza: recalcula o centroide e reinicia o processo de distribuir a cada novo/novos pontos adicionados ao cluster

<mark style="background:#d4b106">=> repete isso ate que todos os pontos tenham sido atribuidos ao um cluster (Convergencia)</mark>

Preparação dos dados simliar a como acontece no aprendizado de maquina supervisionado seguindo os mesmo passos focando em tentar reduzir as dimeções para duas para facilitar a analise do algoritmo

==para escolher entre as features==

tecnica é usar o scatter plot onde para cada par de dados é plotado um grafico => para o k-means buscamos aglomerado de ponto visualmente distintos (2 clusters visualmente separados)

# Implementação do k-Means:

O kmeans armazena os hiperparametros, e os centroides sao quase q seus rotulos


```python
self. # serve para receber os paramentros das passado na assinatura da funçao basicamente

```

Sempre começa em um ponto aleatorio de inicio
Atribui cada ponto a um centroide mais proximo
Atualiza o centroide com base na media dos pontos do cluster
Executa o Kmeans => restribui os pontos e os agrupam em clusters por similaridade

e faz o predict de novos dados para os clusters com base nos centroides aprendidos

para o k-means precisamos dizer qual o numero de clusters q ele tem q perdictar mas usando o metodo do cotevelo podemos achar o melhor valor de K dentro dos dados

cada centroide define <mark style="background:#d2cbff">fronteiras</mark> entre as características qualquer ponto q caia na fronteira é atribuido ao centroide 

# 1° forma de aplicar:
## Quantização vetorial
Comprimir imagens=> reduz o numero de cores de uma imagem

<font color="#ff0000">cor = vetor de 3 dimensões RGB => pixel é um vetor de cores</font>

# 2° seguimentação de imagem: 
dividir a imagem em conjutos de pixel

topografia de mapas e analise de imagens de plano baixo


<mark style="background:#fff88f">Registros == Clusters</mark>
Baseado em distancia para fazer o registro de união do clusters (acontece de dois em dois) => processo chamando de Bottom-up
ja o processo oposto que é dividindo/separando de cima para baixo é o top-down


coloca os dados em uma matriz de distancia: D=d(xi,xj)

### Método:

**Interação:** buscamos acada passo o par com menor ditancia e agrupamos eles em um só.
**Atualização:** Recalcula a distancia como o novo ponto => matriz de distancia
**Terminação:** esses passos são repetidos ate que vire somente um cluster 

## Critérios: 
### Como medir essas ligações e distancias

<mark style="background:#40a9ff">single linkage: </mark>é feita a conta pelos pontos mais proximos entre os dois clusters analizados no momento
<mark style="background:#40a9ff">avarange linkage:</mark> media entre todas as distancias entre os pontos dos clusters em analise
<mark style="background:#40a9ff">ward:</mark> soma dos quadrados das distancias entre os centroides dos clusters

**<mark style="background:#9254de">Cada critério de ligação produz diferentes estruturas de cluster:</mark>**

  

<mark style="background:#9254de">- **Single Linkage**: Tende a criar clusters elongados e pode sofrer do "efeito corrente" (chaining effect).</mark>

<mark style="background:#9254de">- **Complete Linkage**: Produz clusters mais compactos e esféricos.</mark>

<mark style="background:#9254de">- **Average Linkage**: Um meio-termo entre single e complete.</mark>

<mark style="background:#9254de">- **Ward Linkage**: Minimiza a variância intra-cluster, similar ao objetivo do K-Means.</mark>


