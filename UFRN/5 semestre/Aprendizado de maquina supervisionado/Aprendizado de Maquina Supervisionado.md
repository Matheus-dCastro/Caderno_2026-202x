# Aula 01-

## Analise Exploratoria de dados

- fazer a analise previa dos dados para limpeza e revisao de dados q nao da apra usar

### Exploracao de dados

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

```py

def lerp(a, b, t): # a e b sao ponto e t e o valor para normalizado 
 return a + t * (b - a) # valor de retorno da interpolacao
```

sorted → e usado para ordenar os dados

serve basicamente para criar um numeor entre pontos no valor central uando o percentil uma lista com 5 elemento quero p=75% vai  ser 0.75*(4-1[indexes]) = 0.75*3 = 2.25 [index mas ele n exite] → pego o valor do antecessor a esse valor de index q n existe e o o sucessor dele tambem e termino de calular

Medidas de dispersao:

intervalo: amplitude max(x) - min(x)

variancia: media dos quadrados dos desvios em relacao a media da amostra

desvio padrao: raiz quadrada da variancia
