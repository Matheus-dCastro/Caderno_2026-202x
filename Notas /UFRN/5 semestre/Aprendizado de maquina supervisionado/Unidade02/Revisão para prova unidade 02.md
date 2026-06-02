# Notebook 06 

-> objetivo é criar um modelo capaz de também generalizar em cima dos dados fornecido e realizar predicts em novos dados.
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

#### <font color="#6425d0"><mark style="background:#d2cbff">🟣 VANTAGEM: **Holdout Estratificado** é unir a velocidade do metodo a uma forma de avaliar mais justa em dataset desbalanceados -> preserva a proporção das classes</mark></font>

#### <font color="#6425d0"><mark style="background:#d2cbff">📍DESVANTAGEM: **Holdout Estratificado** é performance depende de uma unica divisão de dados o que vai gerar uma estimativa com alta variândia -> menos robustes q a validação crusada</mark></font>


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

<font color="#6425d0"><mark style="background:#fdbfff">🟣 **VANTAGEM:** Estivar a escabilidade e a variancia de modelos, ***MUITO BOM PARA DATASETS PEQUENOS*** pela reutilização dos dados => gerar distribuição de metricas, visão geral e mais completa da performance do que um unico split dos dados</mark></font> 


<font color="#6425d0"><mark style="background:#fdbfff">📍 **DESVANTAGENS:** mais custoso computacional pois tem q treinar muitos modelos e sua complexidade conceitual => POR TER REPETIÇÃO ESTA SUJEITO A SER SENSIVEL A OUTLIERS POIS PODEM ESTA SUPER REPRESENTADO EM ALGUMAS AMOSTRAS</mark></font> 



| Tecnica                 | **Quando usar**                            | **Vantagens**                                   | **Desvantagem**                                             |
| :---------------------- | ------------------------------------------ | ----------------------------------------------- | ----------------------------------------------------------- |
| Holdout                 | modelos rapidos ou grande conjutos         | simples e rapido                                | avaliação intavel em conjuntos pequenos                     |
| K-fold Cross Validation | robusta, tuning de modelo (tunar modelo)   | estavel, estatisticametne confiavel             | mais custoso computacionalmente                             |
| Bootstrap               | pequenos conjuntos ou analise de variancai | gerar distribuição de erros (por ter repetição) | mais complexo e pode se tornar sensivel a roidos e outlines |


