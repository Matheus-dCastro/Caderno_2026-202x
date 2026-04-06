[[Aprendizado de Maquina Supervisionado]]
#5 semestre
## Supervisionado Vs Não-Supervisionado

-> supervisionado ja temos as características <mark style="background:#fff88f">rotuladas</mark> informações previas das variáveis
-> NÃO-supervisionado não temos essas características <mark style="background:#fff88f">rotuladas </mark>

## AED (Analise Exploratória de Dados)

analise de uma fonte de dados
check list de informações para analisar levando sempre em consideração seu contexto

encontrar padrões, relações e tendencias e suas incosistencias entre os dados nos dados

### Tipos de Graficos

Dados <mark style="background:#9254de">Catergoricos</mark>: Barra e pizza
Dados  <mark style="background:#9254de">Numericos</mark>: Histograma e Linhas

 Medidas de centralidade e ou de dispersão

Centralidade: media, mediana e moda -> valor tipico ou central
dispersão:  desvio padrão, variancia e amplitude(intervalo) -> variedade do conjunto de dados

# Passo a passo de EAD

passo base: analise descritiva dos dados (frequencia, tendencia central, dispersao e distribuiçao)

Tipos de dados:
-> <mark style="background:#ff4d4f">univariados:</mark> apenas um atributo
-> <mark style="background:#ff4d4f">multivariados:</mark> dois ou mais atributos para compor o dado


Percentil: é o numero de partes em porcentagem o numero indicado pelo percentil

![[Pasted image 20260404103930.png]] 

<- menores dados ========= maiores dados ->

devem esta ordenados de forma crescente 


Caso do valor da posição não for inteira é feita a interpolação linear

![[Pasted image 20260404105623.png]]


### Desvio padrão:
1° media
2° desvio => pega cada valor e subtrai da media
3° variância => soma todos os desvios ao quadrado  e divide pela quantidade de elementos
4° desvio padrão => é a raiz quadrada da variância

### Desvio médio absoluto => AAD

dispersão dos dados em relação a media mede a variabilidade doa variáveis

<mark style="background:#d4b106">mesmo que a variância so que não leva os valores ao quadrado</mark>

# <mark style="background:#40a9ff">Para pode medir mais de uma variavel (Multivariavel) => usamos a COVARIANCIA</mark>

para que as variaveis sejam independentes o grau de cov é zero
![[Pasted image 20260404145703.png]]


## Pre-processamento de dados

=> Redução de gastos e mais precisão no treinamento e na analise de padros de dados

    -> Filtros: 
        analisar informações que estão faltando 
        quais variáveis são pertinentes para analise (finalidade)
    -> Agrupar dados: expecificar os dados

 - 1 eliminar dados que não agregam informações tão relevantes para analise
 - 2 apenas pegar os mais relevantes para analise dos dados


```

.isnull() // => retorna quais colunas de dados tem elementos faltantes
.dropna(axis=0) //=> elimina as linhas que estao com os paramentros faltantes 
.dropna(axis=1) //=> elimina as colunas que estao com os paramentros faltantes 
.dropna(how='all') //=> elimina a linha se apenas se todos os parametros dele estiver faltando
.sample(n=) //=> n é o valor de elementos q seram imprimidos na tabela

```





## Integraçao de dados:

=> problema de indentificaçao de entediade (Reorganizar uma das bases de dados para que fiquem corelacionadas)

 - 1 organizar por indices
 ```
 
 SimpleImputer => serve para colocar nos valores q estão faltando um x valor apartir da estratagia q passada nele
  
 ```

 ## Dados desbalanceados => podem levar aos dados estarem invesados o que causa ao modelos de AM uma baixa capacidade de <mark style="background:#40a9ff">GENERALIZAÇÃO</mark>





## Dados inconsistentes
dados mal colocados ou dados incoerentes com analise logica

# <mark style="background:#ff4d4f"> => tanto para integrar dados quanto para inconsistência de dados</mark>


![[Pasted image 20260404161402.png]]

## Dados Redundantes
dados repetidos

## Dados com ruídos
dados que apresentam falhas nas medições =>
		- filtragem
		- Suavização
		- remover outlines


## Transformação de dados

mudança de escalas

![[Pasted image 20260404161836.png]]


Box-cox para indicar qual a melhor forma de transforma (priorizando a acurácia e a fidelidade dos dados)

para AM podemos usar basicamente StandardScaler

### Padronizar VS Normalizar

focam em redimensionar os dados para redução de custos 3

=> Normalização leva os dados a valores entre 0 e 1
=> Padronização leva os dados dos valores da media vai a 0 e o DP vai a 1 mas o restante não fica limitada a nenhum range

<mark style="background:#affad1">padronizar</mark> quando os dados seguem uma distribuição gaussiana para quando quero a PCA e quando a muitos outlines

<mark style="background:#fdbfff">normalizar</mark> quando os dados não seguem uma distribuição não gaussiana o algorítimo de analise requer q os dados fiquem em uma escala entre 0 e 1 evitar se ainda tiver outlines nos dados

# Reduzir dados

esse processo ganha eficiencia mais pode perder informaçoes mesmo com o metodo PCA que metiga essa perca pode aver perda das informaçoes originais

 mantem a variancia no maximo possivel mas mantem apenas os atributos mais relevantes os componentes principais sao os pontos com maxima variancia em espaço reduzido


# Regressão <mark style="background:#9254de">Linear</mark> VS <mark style="background:#9254de">Logística</mark> 


