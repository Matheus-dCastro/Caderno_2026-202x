[[Revisão para prova Unidade 01]]
[[Aprendizado de Maquina Supervisionado Draw]] [[Aprendizado de Maquina Supervisionado Aulas]]


# Notebook 01:

![[Revisão para prova Unidade 01#Supervisionado Vs Não-Supervisionado]]

o supevisionado ele foca basicamente em categorizar os dados ja o nao supervisionado ele foca em principalmente e prever um numero ele n retorna tipo ou rotulos para um conjunto de dados

![[Revisão para prova Unidade 01#AED (Analise Exploratória de Dados)]]

nessa etapa podemos separa os dados em
categorigos e numeros

onde os categoricos costumalmente sao melhor visualizados em barra ou pizza ja o numericos pontos ou linhas

as medidas de tendencia central q geralmente usamos para essa analise de componente princial sera:
	media, moda, mediana
ja para componentes de dispersao temos: DP, variancia, aplitude(escopo onde se contem os dados)

![[Revisão para prova Unidade 01#Passo a passo de EAD]]

=> a <font color="#ffff00">covariancia</font> em analises de dados assim como em probabilidades serve para medir o nivel de ligacao das variavies onde quanto mais proxima de zero indica q elas tem uma baixa correlacao para variar e nao sao boas canditas para se trabalhar juntas na analise <mark style="background:#ff4d4f">(ESSE E O PROCESSO DE AAD)</mark>


![[Revisão para prova Unidade 01#exemplo do uso de cov]]

# A etapa de pre-processamento de dados:

esta etapa e se nao a mais importate de toda a analise onde precisamos entender o contexto em que eles foram criados antes de tudo

- reduz custos
- mais preciso e generalista

passamos inicialmente pela <mark style="background:#b1ffff">filtragem</mark> nessa etapa removemos dados q nao contribuiem para analise, dados repetidos e dados e quais dessas variais sao mais importantes para o plot

![[Revisão para prova Unidade 01#Comando py]]

esses comandos podem ser usado para fazer uma limpeza dos dados focando em deixar o dataset mais eficiente para o proposito da analise q queremos fazer

ja o processo de <mark style="background:#b1ffff">Integrar</mark> os dados e o processo de restruturar como esta disposta a informacao para que podemos crusar os dados com outro dataset se for preciso

=> dados desbalanceados podem levar a inviesamento e baixo poder de generalizacao 

quando temos <font color="#ffffff"><mark style="background:#b1ffff">inconsistência</mark></font>  sao dados em q foram colocado por erros ou incoerentes com a realidade conhecida sobre o dataset analisado

e temos tambem dados <mark style="background:#b1ffff">redundantes</mark> q sao dados repetidos ou q a informacao q eles trazem pode ser obtido apartir de outros dados

Dados com <mark style="background:#b1ffff">ruidos</mark> sao dados q podem ser q foram catalogados errado ou seja falha na medicao dos daods ou em processo de teste colocado esse ruido para testar o train do modelo 

O efeito de <mark style="background:#b1ffff">padronizar</mark> leva a media a zero e a dp a 1 bem usado para poder catalogar grupos dependendo do algoritmo ou quando temos a presensa de muitos outlines dentro dos dados ja a <mark style="background:#b1ffff">normalizacao</mark> leva os dados geralmente a um intervalo por padrao de 0 a 1 isso reduz custos computacionais dos dados deve evitar fazer ela antes de remover esse outlines 


![[Revisão para prova Unidade 01#Padronizar VS Normalizar]]![[Revisão para prova Unidade 01#exemplo do uso da norm e padro]]
