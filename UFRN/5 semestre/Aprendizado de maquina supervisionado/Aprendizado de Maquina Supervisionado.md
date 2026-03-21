[Data Review](https://www.youtube.com/@datarvw)

# Aula 01-

## Analise Exploratoria de dados:

- fazer a analise previa dos dados para limpeza e revisao de dados q nao da apra usar

### Exploracao de dados:

Analise descritiva: para uma analise basica afim de estrair 

Frequencia, tendencia central, dispersao e detribuicao

TIPOS:

- dados univariados: apenas um atributo ($x_i$);
- dados multivariados: quando contem mais de um atributo ($x_ij$)

MEDIDAS DE TENDENCIA CENTRAL:

Media, Mediana, Percentil(25%,50%,75%, quadrantes)

Menos e mais sensivel: **nível de risco, confidencialidade e impacto legal** 

para calcular a sensibilidade de um dado: 

Ordenar os dados de forma crecente (facilita para tirar a mediana dessa forma)

calcular o tamanho do percentil usando o len() do dado para divir em 4 partes (100% = recebe 3 cortes de contexto)

Caso da posisao nao for inteira e feita uma interpolacao linear

**Def. interpolcao linear:**

dado dois pontos (coordedandos) (y-y0)/(y1-y0) = (x-x0)/(x1-x0) com n =1  (ambas distancias normalizada)

pode ser usado para : 

- dados ausentes  → preencher laculas de dados
- aumento de dado → redimencionamento de imagens
- ajuste de hiperparametros e otimizacao →
- algotimos especificos
- representacao de baixa dimensao (embeddings)

```jsx

def lerp(a, b, t): // a e b sao ponto e t e o valor para normalizado 
	return a + t * (b - a) // valor de retorno da interpolacao
```

sorted → e usado para ordenar os dados

serve basicamente para criar um numeor entre pontos no valor central uando o percentil uma lista com 5 elemento quero p=75% vai  ser 0.75*(4-1[indexes]) = 0.75*3 = 2.25 [index mas ele n exite] → pego o valor do antecessor a esse valor de index q n existe e o o sucessor dele tambem e termino de calular 

Medidas de dispersao: 

intervalo: amplitude max(x) - min(x)

variancia: media dos quadrados dos desvios em relacao a media da amostra

desvio padrao: raiz quadrada da variancia

# Aula 02 -

## Pre-processamento de dados:

- Faz basicamente o tratamento de dados antes da analize da maquina → melhorar a eficiencia dos modelos em desempenho, perfomace e resultados aumentano a precissao, reduz o tempo de processamento e facilita a indentificacao de padroes relevantes

### Eliminacao manual de atributos:

removemos os atributos q n iram contribuir para analize ou muitos repetidos

### Integracao de dados:

dados basicamente repetidos: diferentes conjuntos de dados conterem atributos distintos referentes as mesma amostras → um mesmo cliente cadatrado em sistemas diferentes. quando esses conjutos de dados compartilhadom as mesmas amostra mas em ordens distintas precisa alinhar a estrutura dos dados para garantir compatibilidade e coerencia correta entre registros antes de torna um unico dataset

### Amostragem de dados:

reduzir o numero de variavies de dados mas tentando mantes a integridade das informacoes a cerca dos dados (para datasets muito grandes) e a amostra precisa representar bem a divercidade do dataset (tem q embaralhar pegar a amostra e depois ordenar para facilitar a anilise) →o valor resultante do valor medio deve ser muito igual ou muito procimo do valor reald do dataset 

### Dados desbalanceados:

quando nao a proporcionalidade entre as amostras do dataset (ter mais questoes de derivadas do q de integrais → aluno melhor em derivar do q integrar)

### Limpeza de dados:

dados ma coletados por erro tecnicos ou por ma preenchimento manual desses dados nesses casos e necessario limpar o dataset ou seja apagar a amostra q esta distoando ou apagar a variavel errada do dado

### Dados incompletos:

para preencher esses dados incompletos podemos 

```markdown
- Remover linha com dados faltantes;
- Definir valores manualmente;
- Preencher com algum valor central da distribuição;
- Utilizar [método de interpolação](https://pt.wikipedia.org/wiki/Interpola%C3%A7%C3%A3o#:~:text=Em%20matem%C3%A1tica%2C%20denomina%2Dse%20interpola%C3%A7%C3%A3o,amostragem%20ou%20de%20um%20experimento.).
```

### Dados incosistentes:

exemplo pessoa com 40 anos e 5kg → limpeza apaga logo

### Dados redundantes:

dados a estao expresando a mesma informacao exemplo imc n precisamos dele na tabela se temos altura e peso podemos conseguir ele logo ele na tabela e redundante

### dados com ruidos:

dados q estao com os valores incorretos ou distorcidas para comprir um proposito ou por erros de medicao isso reflete um outliers 

- tecnica de filtragem
- suavizacao  de dados (smoothing)
- remocao dos autliers

### Transformcao de dados:

transformar dados brutos para melhor anize e reduzir o custo de processamento de analise ou modelagem → tencinca da normalizacao dos dados

### Reducao de dimensoes

PCA→ Analise de componentes principais isso faz com q tenha o maximo de variancia possivel no dado mantendo apenas atributos relevantes para analise usando conceitos da algebra lienar assim achando uma nova mattriz de dados q representa os mesmo dados anteriores so q com uma reducao na dimensao dos dados

- decompisao dos vetores

![image.png](attachment:bbc66ed8-956b-4795-9d7a-66fb82fe81c0:image.png)

X matriz original

U matriz q diz a direcao do dado

Vt matriz transposta

sigma diagonal q contem os valores singulares de X

Esta apenas escalando o vetor n mudando ele

acha os auto valores e auto vetores da matriz de covariancia 

PCA ja e uma funcao do import sklearn

- pega a media e subtrai a media de cada valor jogando os dados para o centro
- fazendo com q foque na variancia dos dados
- como cada variavel se relaciona com cada uma das outras variaveis em forma de matriz
- faz a covariancia → matriz

## Regresao linear e logistica

Regresao linear e Regresao Logistica

- regresao linear → prever numeros (valores continuos)
- regresao logistica → classifica

```markdown
* **Regressão** busca **prever valores numéricos** contínuos.
  - A saída pode assumir **qualquer valor real**.
  - Por exemplo:
    - Prever o **preço de uma casa** em função do tamanho, localização e número de quartos.
    - Estimar o **consumo de energia elétrica** de uma residência ao longo do mês.

* **Classificação** busca **atribuir uma categoria** a uma observação.
  - A saída é **um rótulo discreto** (duas ou mais classes possíveis).
  - Por exemplo:
    - Determinar se um e-mail é **spam ou não spam**.
    - Classificar se um **tumor** é **maligno ou benigno** a partir de características médicas.

```

![image.png](attachment:7c62b90d-d345-4b2a-abf1-3f809adaa916:image.png)

### Modelos fundamentais:

```markdown
### **1.2 Fluxo de trabalho em AM:**
<font size=3>
    
O desenvolvimento de um modelo em AM geralmente segue um **fluxo de etapas**:
1. **Importar e explorar os dados** — entender suas características, distribuições e possíveis problemas.
2. **Pré-processar os dados** — tratar valores ausentes, normalizar/transformar atributos e preparar as variáveis de entrada.
3. **Treinar o modelo** — escolha de um modelo e ajuste dos parâmetros internos a partir dos dados de treino.
4. **Realizar predições** — aplicar o modelo treinado em novos dados.
5. **Avaliar o desempenho** — medir acurácia, erro ou outras métricas adequadas ao problema.
```

# Regrecao linear:

nesse processo a meta e minimazar os erros entres os valores previsto da saida → o erro vem como erro quadratico MSE

### Ajuste do parametro do modelo:

existe diferentes maneiras de ajustar durante o treinamento os parametros: 

- **minimos quadrados ordinarios:**
    
    resilve via algebra linear
    
- **gradiente descente**:
    
    metodo de forma interativa ou seja ajutando os paramentros graduamente para minimizar os erros
    

observaçao: treinar e fitar o modelo sao expressoes equivalentes em aprendizado de maquina os dois termos se referem em ajustar os paramentros internos apartir dos dados do treinamento

→ sera utilizado o sklearn (skikit-learn) como biblioteca padrao para todo o curso

para treino/fitar o modelo sempre é bom ter mais dados de treino do q de teste ex 70/30% 

→ na regreçao linear n é estritamente necessario o passo da normalizacao pq a soluçao analitica encontra os coeficientes de forma exata, idenpendente da escala das variaveis

## Interpolaçao VS Extrapolaçao:

```markdown
 **Interpolação:**
    * Ocorre quando fazemos previsões **dentro do intervalo** dos dados usados no treinamento.
    * A interpolação costuma ser **confiável**, já que o modelo aprendeu padrões nesse intervalo.
    * Por exemplo, se treinamos um modelo com dados de **idades entre 10 e 18 anos** e queremos prever a altura de uma pessoa de **15 anos**, estamos interpolando.

- **Extrapolação:**
    * Ocorre quando fazemos previsões **fora do intervalo** dos dados de treinamento.
    * A extrapolação pode ser **arriscada**, pois o modelo está assumindo que o mesmo padrão linear se mantém fora da faixa observada — o que nem sempre é verdadeiro.
    * Por exemplo, usar o mesmo modelo (treinado com idades entre 10 e 18) para prever a altura de uma pessoa de **30 anos**.

```

## Regressao logistica:

usamos a funçao de Sigmoid → [0,1]

a previsao do modelo e dada pela probabilidade de um coisa pertencer mais a uma classe do q a outra excolhendo assim a maior porcentagem dentre das possibilidades 

isso tanto para classes binarias q classifica de 0 a 1 e para multiclasses q classifica dentro das possibilidades usadno a softmax(entrada)

assim como no anterios a normalizacao dos dados n é obrigatorio mas é altamente recomendado para q tenhamos os melhores desemepenhos

### **1.2 Fluxo de trabalho em AM:**

O desenvolvimento de um modelo em AM geralmente segue um **fluxo de etapas**:

1. **Importar e explorar os dados** — entender suas características, distribuições e possíveis problemas.
2. **Pré-processar os dados** — tratar valores ausentes, normalizar/transformar atributos e preparar as variáveis de entrada.
3. **Treinar o modelo** — escolha de um modelo e ajuste dos parâmetros internos a partir dos dados de treino.
4. **Realizar predições** — aplicar o modelo treinado em novos dados.
5. **Avaliar o desempenho** — medir acurácia, erro ou outras métricas adequadas ao problema.