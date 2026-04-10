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



# Exercícios:




