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

## Benção de nao uniformidade:

muitas vezes os dados estao retrintos a subespaços ou varidade de baixa dimen
-> dimensionalidade intriseca é muito menor q a o proprio espaço

cada ponto é pertencente ao um grupo de vizinhos

## Autovetores e Autovalores 

estudar essa parte de matrizes de novo, livro de algebra e fazer algumas questoes so para relembrar 

-> usa a matriz de covariancia para fazer a redução em auto valores e auto vetores

- **Autovetores**: Representam as direções dos eixos no novo espaço de características. No contexto do PCA, eles são os **componentes principais**. Eles são ortogonais entre si.

- **Autovalores**: Indicam a magnitude da variância dos dados ao longo das direções dos autovetores.
## Eigenfaces com o LFW dataser

visao computacional, reconhecimento facial 
-> trata cada imagem de um rosto como um vetor
-> captura a variançoes mais significativas em um espaço de baixa dimensionalidade
-> representao os ingrediente principais de onde qualquer rosto do dataset pode ser contruido

**PCA em matematicamente:**

indentificar um numero menor de variaveis correlacionadas => capturar padroes
maior variabilidade dos dados agrupando pela sua covariancias entre elas 

<mark style="background:#40a9ff">obteção das variaveis mais importantes</mark> 


