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



# Fluxo de trabalho automatico: Notebook 07

