# Notebook 06 

-> objetivo é criar um modelo capaz de também generalizar em cima dos dados fornecido e realizar predicts em novos dados
### 1. Holdout e Amostragem Aleatória:

<mark style="background:#d3f8b6">- treinamento: ~ 60% - 80% => questões de exercício</mark>
<mark style="background:#d3f8b6">- teste: ~ 10% - 30% => questões para saber quais pontos precisa melhorar antes de prova </mark>
<mark style="background:#d3f8b6">- validação: ~ 20% - 30% => questões de prova</mark>

<mark style="background:#ff4d4f">Esse aqui é o metodo que divide o dado em 3 partes (divide o test em duas partes)</mark>

para quando as classes do nosso dado não esta distribuída deforma balanceado aplicamos o stratify= na variável alvo -> y
=> faz com que se eu tiver z% de uma determinada amostra quando realizar o split de train e test terá z% em train e z% em test

### 1.2 Afinação de hiperparâmetros com dados de validação:

Dividir os dados da melhor forma sem aplicar vies -> dados de test "peso nos dados" utilizar dados de validação.
-> treina varias versões nos dados de treino
-> usa parte dos dados de test para avalizar como esta essas varias versões desse modelo
+> realizar a concatenação dos dados de train e validação
-> dados de test ficam intocáveis ate realizar o test final

> - Treinamento: 70% questões de lista
> - Validação: 20% questões de revisão
> - test: 10% questões de prova da unidade

<font color="#000000">#### <font color="#000000"><mark style="background:#d2cbff">🟣 VANTAGEM: **Holdout Estratificado** é unir a velocidade do metodo a uma forma de avaliar mais justa em dataset desbalanceados -> preserva a proporção das classes</mark></font></font>

<font color="#000000">#### <font color="#000000"><mark style="background:#d2cbff">📍DESVANTAGEM: **Holdout Estratificado** é performance depende de uma unica divisão de dados o que vai gerar uma estimativa com alta variândia -> menos robustes q a validação crusada</mark></font></font>


### 2. Validação Cruzada K-fold (Cross-Validation):

	=== COMUM DIVIDIR EM 10 FOLDS


= melhor técnica para modelos pequenos;
= Mais robusta e estatisticamente confiável para estimar o desempenho de modelos

-> as partes em que o dataset é dividido é chamado de fold => k: partes
					 - k-folds
-> o modelo é treinado sempre com k - 1 partes dos k-folds sempre deixando uma das pates para ser o test daquela rodada de train

-> faz isso k vezes para cobrir o maior numero de possibilidades do dataset
<mark style="background:#d4b106">**-> o desempenho final é a media dos de todos os k-test**</mark>

➡ existe duas formas dentro do scikit-learn
	- **forma explicita**: passando o objeto kfold => para ter mais controle do processo interativo e das divisoes dos dados
	- **forma implicita:** usando a função cross_val_score => para simplicidade e enxuta
==a escolha não define se vamos afinar ou não os hiperparametros==

### 2.1 Sem afinação dos hiperparâmetros no dataset ~100 amostras:

-> **Não é necessário quando:** quando o foco principal é a validação do modelo e não a otimização de desempenho ou quando o ganho esperado não justica o custo de operação (Notebook 12) ou em datasets muito pequenos.

![[Revisão para prova unidade 02-1780360210103.webp]]

metricas com MSE q tem seu melhor valor proximo de zero será multiplicado por -1 para achar o maior/melhor a ser escolhido na cross_val_score.

### 2.2 Com afinação de hiperparâmetros dataset ~1000 amostras:

> para datasets com ~100 e **Precisa afinar** seguir o passo da seção anterior e usar o objeto para ter esse controle


-> passa o k em um for com o tamanho q quer dividir 
- retira a media do scores

### 2.3 Conjunto de dados desbalanceados:

-> cross_val_score ja realiza a amostragem de forma estratificada mas para ter controle => StratifiedKfold

### 3 Bootstrap:

Basado em reamostragem com reposição
= avalia a estabilidade e a variancia do modelo
= bom para quando temos poucos dados

temos um dataset com *n* amostras
criamos *B* conjutos chamados bootstrap samples com *n* amostras cada => por ter repetição pode ter dados q nunca foram para o conjuto *B*

- treina o modelo com o conjuto *B* da vez 
- avalia o desempenho com os dados OOB (out-off-bag) os dados q não foram escolhidos na hora de montar o conjunto *B* 
- apos realizar *B* interações tira a media e o desvio padrão dos das performances do modelo

<font color="#000000"><mark style="background:#fdbfff">🟣 **VANTAGEM:** Estivar a escabilidade e a variancia de modelos, ***MUITO BOM PARA DATASETS PEQUENOS*** pela reutilização dos dados => gerar distribuição de metricas, visão geral e mais completa da performance do que um unico split dos dados</mark></font> 


<font color="#000000"><mark style="background:#fdbfff">📍 **DESVANTAGENS:** mais custoso computacional pois tem q treinar muitos modelos e sua complexidade conceitual => POR TER REPETIÇÃO ESTA SUJEITO A SER SENSIVEL A OUTLIERS POIS PODEM ESTA SUPER REPRESENTADO EM ALGUMAS AMOSTRAS</mark></font> 



| Tecnica                 | **Quando usar**                            | **Vantagens**                                   | **Desvantagem**                                             |
| :---------------------- | ------------------------------------------ | ----------------------------------------------- | ----------------------------------------------------------- |
| Holdout                 | modelos rapidos ou grande conjutos         | simples e rapido                                | avaliação intavel em conjuntos pequenos                     |
| K-fold Cross Validation | robusta, tuning de modelo (tunar modelo)   | estavel, estatisticametne confiavel             | mais custoso computacionalmente                             |
| Bootstrap               | pequenos conjuntos ou analise de variancai | gerar distribuição de erros (por ter repetição) | mais complexo e pode se tornar sensivel a roidos e outlines |

# Fluxo de trabalho automático : Notebook 07

fluxo de trabalho de ponta a ponta de forma rigorosa usando o scikit-learn.

### 1. Pré-processamento com dados heterogêneos:

todos os modelos exigem que suas entradas sejam numericas e nao categoricas.
e geralmente aplicamos padronização(scaling) padronizar a escala dos dados bom principalmente para modelos baseados em distancia
codificação(encoding) transformar features categoricas em features numericas

para aplicar tais tranformações de forma correta usamos o columntranformer
assim podemos ou

separar todas as features em uma lista de string e passar essa variavel no columntransformer tanto para features numericas ou categoricas

ou quando separamos o x e o y passamos ele dentro do columntransformer se todos forem do mesmo tipo


### 2. Organizando o fluxo de trabalho

<mark style="background:#40a9ff">+> Uso do pipeline: </mark> serve para acorrentar varios passos q antes teriam q ser passado um por um na fazer de pre e processamento do modelo

-> podemos simplesmente usar como se fosse um unico modelo.

> o pipeline serve para pre-processar o x_train o y_train_encoded ja passa pre-processado para o guiar o modelo no treinamento

pasta usar pipe.predict para realizar o modelo com os dados de test
### 3. Busca automática de hiperparâmetros: 

Para realizar esses ajuste fino nos dados de treinamento usamos o GridSearchCV (uma grade de busca usando o cross validation).

para realizar a busca dos hiperparametros basta usar o fit junto da variavel objeto q definimos o grid e usa-lo para realizar previsões.



unimos os dois processos para encurtar oq precisamos realizar durante a fase de treinamento e previsao de uma forma unificada usando 

<mark style="background:#d4b106">pre-processando o pipe => treinando e ajudando os hiperparametros no grid => realizando o predict no grid</mark>

> o metodo do o gridCV é extremamente custoso computacionalmente para muitos hiperparametros 

RandomizeSearchCV: criado para resolver esse problema do custo do grid, 
definimos um valor fixo de interações e apartir disso ele intera na amostra aleatoriamente sobre uma combinaçaõ de hiperparametros que especificamos
=> isso nos da controle sobre o custo q teremos computacionalmente n_iter=z e a ferramenta fara o melhor possivel nesse espaço.

### **Resumo:**

Nesta aula, aprendemos a construir fluxos de trabalho robustos, profissionais e otimizados com ferramentas essenciais do Scikit-Learn.


* Começamos tratando dados heterogêneos de forma segura com o `ColumnTransformer`.


* Em seguida, encapsulamos nosso fluxo de pré-processamento e modelagem em um único objeto com o `Pipeline`, tornando nosso código mais limpo e seguro.


* Finalmente, aprendemos a otimizar os hiperparâmetros do nosso `Pipeline` de forma automática, usando a busca exaustiva do `GridSearchCV` e a busca eficiente do `RandomizedSearchCV`.

  

**A combinação dessas ferramentas** 

<mark style="background:#9254de">(`ColumnTransformer` -> `Pipeline` -> `*SearchCV`)</mark>

é um dos padrões mais poderosos e utilizados na prática para desenvolver modelos de aprendizado de máquina de alta qualidade.


# Avaliação de Modelos Preditivos: Notebook 08

Como avaliar se um modelo esta desempenhando legal sobre dados n visto e sua capaciade de generalizar de forma eficiente


### 1. Metricas para classificação:

As metricas mais comuns de classificação de modelos.

#### 1.1 acurácia:

- proporção da avaliação correta sobre o total de amostras


```handdrawn-ink
{
	"versionAtEmbed": "0.3.4",
	"filepath": "Ink/Drawing/2026.6.4 - 18.45pm.drawing",
	"width": 860,
	"aspectRatio": 1.7515274949083504
}
```
para cenarios a onde temos classes que estão desbalanceadas a acuracia pode ser enganosa.


#### 1.2 Matriz de Confusã:

como se fosse uma tabela verdade, 

 1 and 1 = 1 => verdadeiro positivo -> VP
 0 and 0 = 1 => verdadeiro negativo -> VN
 1 and 0 = 0 => falso positivo -> FP
 0 and 1 = 0 => falso negativo -> FN

 > positivo e negativo sao as classes de um dataset e podem ser outras nomeclaturas e a matriz pode ser generalizada para mais de duas classes classes contando q siga a mesma logica do and nas operações do plot
 

#### 1.3 Precisão, Revocação e F1-Score:


- Precisão **<mark style="background:#40a9ff">**PRECISION:**</mark> numero q mede das q foram prevista como positivas quantas são realmente positivas
- 
<mark style="background:#fff88f">De todas as previsões que o modelo disse que eram positivas, quantas estavam realmente corretas?</mark>

O quão efetivo eu sou, quanto o modelo estava  certo

```handdrawn-ink
{
	"versionAtEmbed": "0.3.4",
	"filepath": "Ink/Drawing/2026.6.4 - 19.01pm.drawing",
	"width": 808,
	"aspectRatio": 3.467811158798283
}
```

o maximo valor (1) so pode ser alcançado quando o valor de FP == 0 ou seja o modelo n errou nenhuma das previsões q ele realizou. 

> uma alta previsão é importante para filtros de spam para n classificar um email importante comom spam -> <mark style="background:#fdbfff">um falso positivo é caro</mark>


- Sensibilidade/Revocação <mark style="background:#40a9ff">**RECALL**</mark> entre as instacias realmente positivas quantas foram previstas corretamente

<mark style="background:#fff88f">De todos os casos que eram realmente positivos no mundo real, quantos o modelo conseguiu encontrar/capturar?</mark>

de todas as vezes q vc tenteu quantos resultados positivos tinha
```handdrawn-ink
{
	"versionAtEmbed": "0.3.4",
	"filepath": "Ink/Drawing/2026.6.4 - 20.48pm.drawing",
	"width": 740,
	"aspectRatio": 3.318385650224215
}
```

o quanto o modelo cassificou corretamente

```ad-warning


A diferença entre precision e recall é

=> Precision o quanto o modelo previu 

=> Recall o quanto a classe real é oq o modelo falou ou seja a proporção de positivos identificados corretamente

```


 
 
 
 
 - F1-Score: é a media harmonica entre a precisão e a revocação



```handdrawn-ink
{
	"versionAtEmbed": "0.3.4",
	"filepath": "Ink/Drawing/2026.6.4 - 21.40pm.drawing",
	"width": 904,
	"aspectRatio": 2.4498644986449865
}
```


> fundamentais em aplicações de diagnosticos medicos ou detecção de fraudes
> => ONDE ERRAR POSITIVAMENTE OU NEGATIVAMENTE TEM CONSEQUENCIAS BEM DIFERENTES E AS VEZES PROPOSITOS DIFENTES




#### 1.4 Analise ROC: 

utiliza como base um limiar de descição 


- Limiar de decisão: geralmente 0.5 para modelos que entregam probabilidades assim convertemos essa probabilidade em uma classe real

-> Curva ROC serve para representar graficamente esse limar o quão bem um modelo separa as classes {TRADEOFF => troca} os custos dos beneficios entroca dos custos de onos variando esse limiar em [0;1]

**Eixo x** temos o TFP == taxa de falsos positivos


```handdrawn-ink
{
	"versionAtEmbed": "0.3.4",
	"filepath": "Ink/Drawing/2026.6.5 - 9.27am.drawing",
	"width": 566,
	"aspectRatio": 2.3583333333333334
}
```

ta medindo o quanto o modelo previu errado os negativos reais e os colocou como positivos

**Eixo y** temos a TVP == taxa de revocação


```handdrawn-ink
{
	"versionAtEmbed": "0.3.4",
	"filepath": "Ink/Drawing/2026.6.5 - 9.30am.drawing",
	"width": 666,
	"aspectRatio": 2.1414790996784565
}
```

Passamos a ter o recall 

- AUC = 1.o classificador perfeito
- AUC = 0.5 classificador aleatorio, linha diagonal => um modelo bom deve esta o mais longe possivel dessa linha e tendendo a parte superior da diagonal principal.
- AUC < 0.5 classificador é o pior que uma classificação aleatoria


![[Revisão para prova unidade 02-1780662871831.webp]]


olhamos o pico dela ou seja a curva do cutuvelo da curva


### 2. Metricas para regressão:

previsao de valores continuos não a probabilidade de uma amostra pertencer a um classe medindo assim o quão proximo as previsões estao dos valores reais

#### 2.1 Erro medio absoluto (MAE):


```handdrawn-ink
{
	"versionAtEmbed": "0.3.4",
	"filepath": "Ink/Drawing/2026.6.5 - 9.42am.drawing",
	"width": 742,
	"aspectRatio": 2.401294498381877
}
```
#### 2.2 Erro quadratico medio (MSE) e raiz de (RMSE):

ambas tem a mesma finalidade de dar peso ao erro mas uma esta ao quadrado e a outra esta na mesma unidade de medida do y<sup>i</sup>

#### 2.3 R² coeficiente de determinação:

o quão bem a variabilidade dos dados é explicada pelo modelo ou seja o quanto o modelo preve bem os valores e eles conseguem se ajustar aos valores reais.

![[Revisão para prova unidade 02-1780663698820.webp]]

## COMO ESCOLHER A METRICA

- usar a MAE para interpretar erros nas unidades reais
- MSE/RMSE se erros muitos grandes sao mais graves
- R² para uma ter visão geral da performace de modelos de regressão


# Metodos probabilisticos: Notebook 09

<mark style="background:#ff4d4f">modelar incertezas, inferir padroes e tomar decisões</mark>
-> assumem q dados sao gerados por algum processo aleatorio e tentam modelar de forma explicita as distribuiçoes de probabilidade

=> amostras preveniesntes de distribuições de probabilidade

### 1. O teorema de Bayes: 

se basea na probabilidade de uma hipotese com base nas evidencias 

-> Probabilidade apiori
-> Probabilidade posteriori 


ele olha para todos os caso q deu como positivo

### 2. o classificador Naive Bayes:

ele é ingeno todas as variaveis preditoras sao independentes entre si (um não influencia o outro)

> a probabilidade de y é o produto das probabilidades individuais

usado por sua simplicidade e seu bom desempenho em tarefas de classificação
calcula com base na frequencia dos atributos

> [!attention]
> bom para grandes volumes de dados com alta dimensionalidade

#### 2.1 Matematica e algoritmo:

é calculado a probabilidade maxima entre as classes de y usando o conceito de idependecia entre as variaveis

-> fase de treinamento:
	1. calcula a prioridade a priori de todas as classes de y com base nas frequencias das classes do conjunto de dados
	2. calcula a verossimilhança  para acada x dado cada classe de y:
		- para atributos categoricos: frequencia de cada classe
		- para atributos continuos: distribuição normal (NB Gaussiana) estima a media e a variancia para cada atributo em cada classe
	3. faze de predição 
		1. nova amostra: probabilidade de cada classe usando a faze de train
		2. escolhe a classe com maior probabilidade pelo rotulo


#### 2.3.1 Multinomial NB: 
-> contagem ou frequancia de dados de texto ou tabelas de contagem de genes

=> filtros de spam, classificação de artigos e tipos de texto
#### 2.3.2 Bernoullin NB:
-> valores binarios ou seja sim ou nao verdadeiro ou falso 0 e 1
-> verossimilhança: probabilidade de um atributo esta presente em uma amostra

=> foco em texto em q quer saber a presença da palabra chave e nao sua frequencia


#### 2.3.3 Categorical NB:
-> atributos categoricos e discretos (nao necessarimante da forma binaria)
-> verossimilhança: um atributo esta em uma categoria dentro de uma classe

=> classificar algo com base em atributos

![[Revisão para prova unidade 02-1780676182740.webp]]


# Metodos baseados em arvores:

## 1. Arvores de decisão e regressão:

dividir os dados de entrada em regioes baseado em if else pode ser para maximizar algum criterio ou minimizar o erro

arvores de decisao => classificação busca maximizar em como separa as classes
arvores de regressão => regressão tenta minimizar o erro o erro quadratico de cada folha


#### 1.1 Pureza de nós:

a arvore busca a melhor pergunta e divide e organiza os dados de forma q os grupos resultantes sejam os mais puros possiveis

=> um no é realmente puro se todos os dados nele pertencem realmente a mesma classe

