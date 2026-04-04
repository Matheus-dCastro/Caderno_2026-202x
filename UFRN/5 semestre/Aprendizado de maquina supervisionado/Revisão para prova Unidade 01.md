[[Aprendizado de Maquina Supervisionado]]

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