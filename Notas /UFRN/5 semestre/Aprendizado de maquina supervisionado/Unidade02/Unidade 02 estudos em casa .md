# Amostragem e divisão dos dados: Notebook 06

### Holdout e amostragem aleatória: 


basicamente dividir os dados em 

<mark style="background:#40a9ff">- treinamento: ~ 60% - 80% => questões de exercício</mark>
<mark style="background:#40a9ff">- teste: ~ 10% - 30% => questões para saber quais pontos precisa melhorar antes de prova </mark>
<mark style="background:#40a9ff">- validação: ~ 20% - 30% => questões de prova</mark>

<font color="#ffff00">basta fazer o split dos dados duas vezes</font>  => primeiros nos x e y dos dados depois no x e y dividido.

-> quando temos um desbalanceamento (comum n vida real) de classes é necessário realizar o processo de divisão estratificado.

um divisão puramente aleatória cria situações enganosas dos dados e suas saídas analisadas => modelo simplesmente chuta para classe majoritária para todas as previsões => acurácia alta.

**Divisão estratificada:** é dividido de uma forma que mantem as proporções entre as classes.


``` python
train_test_split(x,y,test_size=0.3, random_state=42, stratify=y) # +> deve ir para varivale alvo da operação ou seja o eixo y
# use mean() para verificar as proporções entre as classes
```

Treina com os dados treino, valida com os dados de validação pelo predict depois testa com os dados de test faz a concatenate dos dados de x_train e x_val o mesmo para os dados de y ai sim que testa o modelo com o x_test


sua vantagem é ser veloz e trazer uma avaliação mais justa em dados desbalanceados -> mantem as proporções das classes.
sua desvantagem é a performances ainda depende de uma unida divisão dos dados o que pode gerar uma estimativa com alta variância -> menos robusta que a validação cruzada.

### Validação cruzada k-fold (cross-validation):

<mark style="background:#d4b106">É a técnica mais robusta e estatisticamente confiável para estimar o desempenho dos modelos => perfeito para modelos pequenos (~1000 amostras)</mark>

dividimos em:

- k partes (k-folds)
- modelos treinados com k-1 partes restantes
- repete k vezes com cada fold servindo como validação uma vez cada parte
- seu desempenho final é a media dos k tests
 
ele pega um parte dos dados para ser o test esse teste n sera usar para o train com isso ele passa faz com essa cofig. uma vez depois faz o mesmo mas mudado qual parte esta sendo usada para test e guardar os valores de acc para fazer uma media 
ate q todos todos os blocos pelo menos uma unica vez tenham sido usados como dados de test

<font color="#ff0000">o mais comum é dividir em 10-folds </font>

quando faz a media mesmo q tenha uma config. que venha a favorecer os dados e tornar ele enviesado vai ser minimizado pela media

#### Formas:

**Forma explicita:** usa o objeto kfold -> indicado para ter mais controle do processo de split dos dados
**Forma implícita:** usa a função cross_val_score -> para implementações simples e enxutas

### Sem fazer a afinação:

quando não é necessário ou o dataset muito pequeno (10² amostras)

**não é necessário quando:** (cross-validation) quando o foco principal é a **validação do modelo** e não a otimização de desempenho, ou quando o ganho esperado não justifica o alto custo computacional. quando sao dados baseados em parametros modelos com default bem otimizados ou quando é muiyo pequeno

kf retorna os indices dos dados de train, val, test, com base no array do eixo X 

podemos resumir esses passos sem o uso de afinação de hiperparametros de duas formas:

modelo -> socores = cross_val_score(tudo normal aqui)

ou 

kf = KFold(numero_de_split, shuffle, seed)
score = cross(no lugar de cv passse o kf)

## Com afinação de hiperparametros e dataset ~1000 amostras

quando o dataset tem ordem de 10³ para se fazer divisões entre train, val, test

segue o processo de fazer o teste de acc para cada k no range q eu definir
tira a media entre os valores da acc

### Para dados desbalanceados: 

quando estamos classificando dados desbalanceados -> cross faz a amostragem estratificada sozinha porem para realizar uma estratificação explicita => StratifiedKFold 

-> preciso passar uma lista para armazenar os valores de erro do kfold => skf.split(x,y)

<mark style="background:#40a9ff">Vantagem:</mark> ser robusta -> treina em todas as partes dos dados resultado das metricas muito mais estavel, holdout

![[Unidade 02 estudos em casa -1778005075943.webp|862x417]]


~100 => grande chance de causar ouverfit
~1000 => deixa ele se virar para achar o melhor valor aqui dos hiperparametros

## Bootstrap:
Sorteio de bolas

se basea em reamostragem com reposição parece com o k-fold o mesmo indexe pode aparecer mais de uma vez +> lembre do sorteio das bolas
=> vai avaliar a variancia e a estabilidade do modelo

- n amostras
- gerar B -> conjuntos de dados (bootstrap samples) cada um com n amostras shuffleardas sem repetição entre as amostras
- cada B conjuntos:
	- treina o modelo
	- testa o desempenho em outro conjunto B -> out-of-bag (OOB) -> dados n escolhidos podem ser usados para testar o modelo

em **Classificações** com dados desbalanceados para fazer a estratificação:

- faz o sorteio de cada coisa em sua propria classe ou seja cada atributo tera seu proprio sorteio depois junta todo mundo e temos o conjunto B pegando ed forma igual todos os dados mesmo q desbalanceados

<mark style="background:#40a9ff">Vantagem:</mark> estimar => escabilidade e variancia do des Desvantagens |

| ---------------- | ----------------------empenho de um modelo, melhor para datasets pequenos (reutilização dos dados) 
<mark style="background:#40a9ff">Desvantagem:</mark> grande custo computacional para funcionar por "treinar mais de um modelo" sensivel a ruido 

![[Unidade 02 estudos em casa -1778006697203.webp]]



# Fluxo de trabalho automático: Notebook 07

## Pré-processamento com dados heterogêneos:

<mark style="background:#fff88f">-> todos os modelos de aprendizado exigem q os dados sejam  numéricos</mark> e para garantir uma boa perfomance é de costume usar a tecnicas de tranfomação

=> Padronizaçõa -> scaling: colocando todas as variaves numericas na mesma escala usamos aqui ate agora o StandardScaler
=> Codificação -> encoding: transforma variavez categoricas em representações numericas ainda n é o conceito de LLM usamos nesse caso OneHotEncoder

##### Agora para ocorrer a transformação das colunas de forma correta iremos usar
+> ColumnTransformer: nesse caso aplicasse pipelines para fazer as transformações em diferentes colunas de diferentes tipos em um unico dataset tudo ao mesmo tempo em um unico passo


<mark style="background:#40a9ff">Geralmente para a variavel y se ela for categorica se usa o labelencoder para transfromar em probabilidades as suas saidas alvo. </mark>

ja os atributos de X passamos em valores categorico no onehotencoder como metodo de transformcação dentro do columntranformer

columnTransfromer (metodo de transformação (dos ções), categorias)

prepocessa os dados de x_train e x_test para ficarem na mesm base das cosias

-> agora com todos os dados transformados e colocados em types em q so modelos conseguem trabalhar ai sim posso treinar o modelo e realizar os predicts

## Organizando o fluxo de trabalho:

Pipeline => permite que possamos acorrentar varios passos em um fluxo mais limpo e com menos linhas durante o pre-processamento colocando todos em um unico objeto para modelos

- se comporta comp um estimador: tem os metodos de fit, predict, score
- tornando ele mais simples, seguro e profissional

=> um piperline é uma lista de passos onde cada passao é uma tupla com: 
nome do passo, objetivo de estimar

nosso preprocessador => metodo de transformação ou metodos
classifier => algum modelo de classificação logistica entre os dados

steps=[] agumento onde irmemos passar esses dois objetos para serem preprocessado os dados

podemos fintar o pipe como se fosse um modelo de classifier usando os dados sem modificações de preprocessamentos feitos de forma manual

o y ainda precisa ser passado de forma manula pq:

> **Observação:** Repare abaixo que os dados `X_train` não estão pré-processados, mas os dados `y_train_encoded` estão! Isso acontece porque o `Pipeline` age como uma "esteira de produção" apenas para as features (`X`). A variável alvo (`y`) **não é transformada pelos passos do Pipeline**; ela é passada diretamente ao modelo no final da esteira para guiar o treinamento.

para realizar o predict basta passar o x_test q o pipeline:
	-> chama o transfrom()
	-> passa para o modelo
	-> chama o predict

## Busca automatica de hiperparametros:

-> GridSearchCV
	- Grid Search: faz uma grade realmente um grid de possiveis valores para os hiperparâmetros de test => treia e valida para cada possivel combinação.
-> CV (cross-validation)
	- não faz apenas train/test. ele faz a validação dos dados de forma cruzada no numeor de k-folds que passamos para os dados => tornando a estimativa de cada combinação muito mais robusta e confinável.

=> basicamente ele informa qual a melhor combinação entre os hiperparametros e seu score medio obitivo durante a validação cruzada.

valor de chave padrão para passar para o grid: 




passo o pipe dentro do grid como o parametro estimator

## **Resumo:**

Nesta aula, aprendemos a construir fluxos de trabalho robustos, profissionais e otimizados com ferramentas essenciais do Scikit-Learn.

* Começamos tratando dados heterogêneos de forma segura com o `ColumnTransformer`.

* Em seguida, encapsulamos nosso fluxo de pré-processamento e modelagem em um único objeto com o `Pipeline`, tornando nosso código mais limpo e seguro.

* Finalmente, aprendemos a otimizar os hiperparâmetros do nosso `Pipeline` de forma automática, usando a busca exaustiva do `GridSearchCV` e a busca eficiente do `RandomizedSearchCV`.

  

A combinação dessas ferramentas (`ColumnTransformer` -> `Pipeline` -> `*SearchCV`) é um dos padrões mais poderosos e utilizados na prática para desenvolver modelos de aprendizado de máquina de alta qualidade.


# Avaliação de modelos preditivos: Notebook 08


## Métricas para classificação:

em modelos preditivos precisamos analizar como esta o desempenho dos modelos 

### Acuracia:\

proporcao de previsoes corretas sobre o total => pode ser enganosa em datasets desebalanceados


### Matriz de confusao:

mostra quantas previsoes o modelo acertou ou errou, dividido em categorias

aprendemos nao somente quando o modelo erra mas como o modelo erra

verdadeiro possitivo (VP) | falso negativo (FP)

falso positivo (FP) | verdadeiro negativo (VN)


VP -> o modelo previu positivo e estava certo
VN -> o mdelo previu negativo e estava certo
FP -> o modelo previu positivo mas estava errado
FN -> o modelo previu negativo mas estava errado

diagonal principal vai ser o verdadeiros diagonal secundaria vai ser o falsos 

## Precisao, Revocação e F1-score:
bom especialmente em problemas com classes desbalanceadas.
#### Precisão: 
seu maior valor é quando não tem falsos positivos ou seja FP = 0 todas sao realmente positivas 

#### Sensibilidade/ Revocação:
entre as instancias realmente positivas quantas foram realmente corretas, quando falso negativos = 0 ou seja o modelo previu corretamente todas as intacias q sao realmente positivas seja positivo ou negativo

#### F1-Score:
media harmonica entre precisao e revocação 
> Essas métricas são fundamentais em aplicações como **diagnóstico médico** ou **detecção de fraudes**, onde errar positivamente ou negativamente tem consequências muito diferentes.

**Exemplo:** Imagine um teste com 5 pacientes, onde 2 estão doentes (`Real = [1, 1, 0, 0, 0]`).

  

* **Modelo A (Cauteloso):** `Predito = [1, 0, 0, 0, 0]`

* **Precisão:** 100% (1/1)

* **Revocação:** 50% (1/2)

* **F1-Score:** 67% ( $2 \cdot \frac{1 \cdot 0.5}{1 + 0.5}$ )
* **Modelo B (Sensível):** `Predito = [1, 1, 1, 0, 0]`

* **Precisão:** 67% (2/3)

* **Revocação:** 100% (2/2)

* **F1-Score:** 80% ( $2 \cdot \frac{0.67 \cdot 1}{0.67 + 1}$ )

  

> **Qual modelo é melhor?** Depende do objetivo. Para um exame de triagem, o **Modelo B** é superior (maior Revocação). Para confirmar um tratamento arriscado, o **Modelo A** é mais seguro (maior Precisão). O **F1-Score**, buscando um equilíbrio, aponta o Modelo B como mais balanceado no geral para este caso específico.

#### Analise ROC:

<mark style="background:#d2cbff">limiar de decisão</mark> 

A **Curva ROC**: receiver operating characteristic qual bem um modelo separa as classes independente da decisão q ele escolheu, mostra o trade-off

-> encontrar positivos 
-> custos (alarme falsos)

![[Unidade 02 estudos em casa -1778792204103.webp]]

quanto mais perto a curva ou o ponto for do céu melhor o modelo esta treinado

## Métricas de regressão:
prevemos valores **continuos** quanto proximo o valor previsto estao dos valores reais

#### Erro médio absoluto (MAE):
==_Machine Learning_ que mede a magnitude média dos erros em um conjunto de previsões, sem considerar se são para mais ou para menos==. Ele é expresso na mesma unidade dos dados originais, O MAE calcula a distância absoluta entre os valores reais e os valores previstos, ignorando os sinais negativos.

#### Erro quadratico medio (MSE) e raiz (RMSE):
colocam mais peso aos grandes erros -> ja q o erro esta ao quadratico (usa a mesma formula do MAE so q $^2$) o outro faz so tirar essa raiz 

usa o RMSE para caso deseje trabalhar com a mesma unidade de medida de y

#### Coeficiente de detrminção $R^2$:

indica quanto da variabilidade dos dados é explicada pelo modelo => <font color="#de7802">**quantos os valores previstos se ajustam aos valores reais**</font>

$$

R^2 = 1 - \frac{\sum (y_i - \hat{y}_i)^2}{\sum (y_i - \bar{y})^2} \, ,

$$

onde $\bar y$ é a média de $y_i$. Podemos interpretar o coeficiente como,

  

| Valor de $R^2$ | Interpretação |

|--------------------|-------------------------------------------------------------------------------------------------|

| $R^2 = 1$ | Previsões perfeitas. O modelo explica 100% da variabilidade dos dados. |

| $0 < R^2 < 1$ | O modelo explica parte da variabilidade dos dados. Quanto mais próximo de 1, melhor. |

| $R^2 = 0$ | O modelo não explica nenhuma variabilidade. É tão bom quanto prever a média. |

| $R^2 < 0$ | O modelo é pior do que prever sempre a média. Indica má adequação. |


## Como escolher:

A métrica ideal depende do **contexto**:

* Use **MAE** para interpretar erros em unidades reais;

* **MSE/RMSE** se erros grandes forem mais graves;

* **$R^2$** para uma visão geral da performance do modelo.

## Métodos Probabilísticos: Notebook 09

Utilizam teorias probabilísticas para modelar incertezas, inferir padrões e tomar decisões.
Na modelagem estatistica, os dados sao interpretados como amostras provenientes de distribuiçṍes de probabilidade

### Teorema de Bayes:

probabilidade a priori e a probabilidade posteriore levando em conta a verossimilhança 

![[Unidade 02 estudos em casa -1779051913393.webp]]


<mark style="background:#fff88f">O teorema calcula a probabilidade de ter dado q o evento anterior ja aconteceu</mark>
#### Classificador naive bayes:

bem eficais quando a grande volumes de dados com altas dimensionalidades
NAO é utilizado em tarefaz de regressão pois seu objetivo é apontar para a classe mais provavel de y de acordo com a entrada x

## Matemaica e algoritmo:

fase de treinamento:

calcula a probabilidade apriori de de um classe com base na frequencia de todas as classes no dataset
calcula a verosimilhança:
	categoricos: conta a frequencia a cada classe
	continuos estima-se a media e a variancia para cada atributo da classe

fase de predict:

calcula a probabilidade de cada classe daquela mostra pertencer a cada uma de forma individual
escolhe com o maior valor dentre os resultados

## Multinomial NB:

=> Contagem ou frequencias -> como dados de texto ou tabelas de contagem de genes 
=> verossimilhança: palavra x esta em uma classe y (probabilidade)

ex: spam, classificação de textos em categorias.

## Bernoulli NB:

=> atributos binarios (zeros e uns) tem ou não tem carateristicas
=> verossimilhança: um atributo x esta presente em uma amostra y

ex: Classifica texto é a apenas a presença de palavras chaves nao sua frequencia

## Categorical NB

=> categoricos e discretos
=> verossimilhança: a probabilidade de uma atributo x ter uma categoria y dado uma classe i

ex: classificar coisas comestives ou nao por suas outras caracteristicas fisicas

#### **2.3.4 Resumo:**


| Modelo Scikit-learn | Tipo de Atributo Ideal | Exemplo de Uso |

| :--- | :--- | :--- |

| **`GaussianNB`** | Contínuo (decimal, float) | Medidas de sensores, dados biométricos |

| **`MultinomialNB`** | Contagem/Frequência (inteiro) | Contagem de palavras em textos |

| **`BernoulliNB`** | Binário (0 ou 1) | Presença/Ausência de uma palavra |

| **`CategoricalNB`** | Categórico (discreto) | Cor, tipo, região |



# Metodos baseados em arvores: Notebook 10


podem ser usados tanto para problemas de classificacao e regressao dividindo recusivamente os dados em subconjutos criando hierarquia semelhante a uma arvore (lembre de EDB2).

São focados em deixar os dados em uma linguagem de facil entendimento para o ser humano.
## Arvore de decisão e regressão:

divide recursivamente os atributos entrada em regioes baseados em tecnicas de if else -> foco em maximizar criterios ou minimizar erros.

=> arvore de classificação (arvores de decisão): árvore divide o espaço de atributos focando em maximizar a separação entres as classes.
=> arvore de regressão: árvore tenta dividir os dados de forma a minimizar o erro quadratico dentro dos nós folhas.

critecio de divisao > criteiro de parda => fim dos dados entrada/alcansou o criterio de parada 

## Critério de pureza/ pureza de nós:

Usa como base a entropia (0 para pureza perfeita e 1 par impureza maxima) para determinar o quanto é desorganizado algo

<mark style="background:#40a9ff">-> A arvore busca a pergunta q sempre melhor divide e organiza os dados tentando deixar o mais puro possivel </mark>
<mark style="background:#fff88f">=> nós puros são aqueles que todos os dados nele pertencem a mesma classe +> nós folhas 100% pertencentes aquela classe</mark>

mede-se a impureza ou seja a entropia dos nós -> métricas:
	- Índece Gini (Gini Impurity) esse indeci mede probabilidade de um elemento acabar sendo classificado incorretamente se for classificado aletatoriamente pela distribuição das classes
- G(n) = 0 <font color="#6425d0">pureza perfeita</font> 
- G(n) = 0.5 <font color="#6425d0">impureza maxima para 2 classes</font> 

==+> o criterio de divisão foca em ter o maximo de ganho possiviel de informação== 

  

>O algoritmo é **_greedy_ (ganancioso)**: em cada nó, ele irá testar *todos os atributos* e *todos os limiares (valores de corte do atributo) possíveis* para encontrar a divisão (atributo + limiar) que **maximiza o Ganho de Informação**.

#### Ja para regressão temos o uso do MSE pois o foco é dividir com q deixe os valores y nos nós filhos o mais proximos possivel uns dos outros

## Estrategias de poda:

foca em reduzir a complexidade da arvore e evitar ter overfitting, 
=> **Pre-poda:** corta a arvore antes q ela cresça d+ (muito complexa)
	limitar a profundidade maxima da arvore
	definir um numero minimo de amostras em um no para permitir divisão
	estabelecer um limite de ganho de informações (se n melhora um x valor minimo, pare)

=> **Pós-poda:** deixa o algoritmo construir tudo e depois remove aquilo q n server ou n ajudam na interpretação


**Vantagens:**

- Simples de entender e interpretar (pode ser visualizado como um fluxograma);

- Lida bem com dados categóricos e contínuos;

- Não exige normalização dos dados.

**Desvantagens:**

- Tendência a *overfitting* (árvores muito profundas);

- Pequenas variações nos dados podem causar grandes mudanças na árvore.


## Modelo Random forest:

<mark style="background:#ff4d4f">Arvores de decisão sofre de alta variância risco de tornar instavel e tendecioso ao tentar se ajustar excessivamente a tudo</mark> como resposta treinamos varias arvores e depois fazendo uma votação entre a centena de arvores treinadas.

#### Método ensemble;

random forest combina duas tecnicas poderosas para mitigar o overfitting

- Boostrap: combinação com repetição e permite q os dados n usado sejam colocados em uma sacola para serem usados para retreino ou test
- Aleatoriedade de atributos: para q uma classe dominante n se sobresaia em vantagem das demais, cria um subconjuto aleatorio de atributos para q isso seja mitigado assim o algoritmo leve em consideração apenas as categorias do subconjunto de dados
>O resultado é uma "floresta" de árvores *decorrelacionadas*. Cada uma é uma especialista fraca por si só, mas juntas, através da votação, elas formam um dos modelos mais robustos e eficazes do machine learning.

utiliza a moda de cada arvore durante a **previsao** -> classificação
utiliza a media de cada arvore durante a **previsao** -> Regressão

### - Out-Of-Bag OOB:

por ter reposição a arvore so é treinada em media com ~65% os ~35% q n foram para arvore especifica viram OOB
esse OOB e usado para test das demais arvores q nao viram aquela amostra mas tem um conhecimento previo das demais arvores.


> **Observação:** Você notará que a acurácia do *Random Forest* é geralmente igual ou (em datasets mais complexos) significativamente melhor que a da árvore única. Mais importante, o modelo é muito mais estável. A métrica de OOB nos dá uma estimativa muito confiável de como o modelo se sairá em dados novos.


>**Observação:** Ao contrário da visualização de uma árvore, que é instável, este gráfico é robusto. Ele nos diz quais features o modelo em geral considera mais preditivas.

- **Vantagens:**

- **Alta acurácia**, especialmente em comparação com uma única árvore.

- **Robustez a _overfitting_**, graças à aleatoriedade e ao agrupamento de várias árvores.

- **Capacidade de lidar com dados de alta dimensionalidade e correlação entre variáveis.**

- Funciona bem com **valores ausentes** e **variáveis categóricas**.

- **Desvantagens:**

- Pode ser **mais lento** para prever, especialmente com muitas árvores.

- Menos interpretável do que uma única árvore de decisão.

## Modelo Gradiente boosting:

tambem e ensemble chamdo de boosting no lugar de ser democracia paralela como no random  funciona como um linha de montagem sequencial

especialistas:

1 fica bom em 1 de 3 
o 2 aprena so os uma das coisas q o 1 e ruim ou errou
e o  3 aprende oq o 2 ficou ruim

ai quando junta tudo cada um esta bom em algo e temos um modelo robusto quando juntamos todos

> Ao contrário do *Random Forest*, que usa árvores profundas para reduzir a variância, o *Gradient Boosting* usa árvores muito **rasas** (chamadas de *"weak learners"*, ou aprendizes fracos, muitas vezes com `max_depth` de 3 a 8). Ele começa com um modelo de alto viés (muito simples) e, sequencialmente, reduz esse viés a cada etapa.


### otimizado por gradiente:

usa um afuncao onde m1 = m0 - 1 para um ajustar no q o anterior era ruim


> **O objetivo** é encontrar a melhor árvore nova $h_m(x)$ que, quando adicionada ao modelo, mais reduz a **função de perda** (métrica que avalia a predição com dados de teste). A matemática nos diz que a direção de "redução mais rápida" da perda é o **gradiente negativo** da função de perda.


> O gradiente é um operador que **aponta** a direção e magnitude da taxa de variação de uma função.


precisao 01 => ingenua
-> calcule o residuos: gradiente negativo da funsao de perca 
-> treine um aprendiz fraco apartir do passo ingeno
-> atulize o model: add essa previsao nova a arvore geral e refaça para um novo mestre e aprendiz

> O *Gradient Boosting* é a base para os algoritmos mais famosos como **XGBoost**, **LightGBM** e **CatBoost**, que são implementações altamente otimizadas deste mesmo conceito.

- **Vantagens:**

* **Alta Acurácia:** Frequentemente supera o Random Forest.

* **Flexibilidade:** Pode otimizar qualquer função de perda diferenciável (MSE, MAE, Log-Loss, etc.).

- **Desvantagens:**

* **Mais Sensível a Hiperparâmetros:** O `learning_rate` e o `n_estimators` têm uma relação delicada. Um `learning_rate` muito alto pode causar overfitting.

* **Treinamento Lento:** O processo é **sequencial**, não pode ser facilmente paralelizado (cada árvore depende da anterior). O Random Forest treina muito mais rápido.