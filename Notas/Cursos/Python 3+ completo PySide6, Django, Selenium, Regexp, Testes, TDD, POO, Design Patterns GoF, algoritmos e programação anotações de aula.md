---
aliases:
  - "Python 3+ completo: PySide6"
  - Django
  - Selenium
  - Regexp
  - Testes
  - TDD
  - POO
  - Design Patterns GoF
  - algoritmos e programação anotações de aula
---
 [Udemy Curos de Python 3+ completo: PySide6, Django, Selenium, Regexp, Testes, TDD, POO, Design Patterns GoF, algoritmos e programação](https://www.udemy.com/course/python-3-do-zero-ao-avancado/learn/lecture/34639820#overview)

# Modulo 01

apenas conhecimentos iniciais de sintaxe e alguns importes das funções

# Modulo 02

**Funções:** replica de coisas 


``` python

def # comando para criar uma função/logica de implementação

```

<mark style="background:#40a9ff">podemos receber argumentos por padrão as funções em py retornam None</mark>

###### Argumentos nomeados VS Não nomeados

	perimite q eu defina oq quero definir independente da posição


### Escopo de Função:


```python

global # => serve para mexer em varias de fora de funçoes caso exista a mesma nomeclatura da função 

```

*args =>  serve para passar muito paramentros e posso simplesmente passar um fazer um tratamento da entrada para pegar caminhos
vars() => variaveis locais em forma de dicionario  atributos -> manipulacao
dir() => apenas os nomes -> depuracao

Functions de primeira classe recebe outros args e ou retorna outras function



para unir set |
para intercesao &
para diferenca - apenas presentes no set da esquerda
para diferenca simetrica ^ itens q n estão em ambos

Quando usar o tipo set:

=> contagem de tipos de letras, ou para tipos de entradas únicas 

lambda para fazer ordenasao no sort
sort(key=lambda item: item["oq quero ordenar na lista"])

copia profunda => para copia independente  e copia rasa => para copia como referencia imutável

lambda basicamente é uma função master q vai fazer oq eu passar na linha ou tentar fazer oq eu passar na linha coisa rápido e facio

## Empacotamento e Desempacotamento:


```python

*args para não nomeados e **kwargs para nomeados 

```



## List comprehension:

-> pode relaizar mapeamento de dados dentro diretamente em uma list 
basicamente fazer mapeamento de chaves e filtros
=> filtros: basicamente if e elif para fazer filtros durante as coisas vem depois do for

# Python - programação orientado a objeto

rich.readthedocs.io

**Abstração:** focar no que precisa ser feito

**Encapsulamento:** 
basicamente passar __ antes do q eu quero esconder basicamente isso para infos sensiveis metodos @protect e nome.setter

**Herança:** Ajuda na reutilização de codigo, Organização em hieraquia, manutenção, Extensibilidade, Suporte a polimorfismo
-> Caracteristicas herdadas de classes 
-> Comportamentos
-> ele pode mudar os compostamentos e caracteristicas novas

**Polimorfismo:** 
reme a heranca mais podendo mexer em tudo e n precisa passar o super ja q as caracteristicas do objeto n mudam apenas seus comportamentos mesmo nome de function diferente comportamento

Generator mais eficiente q a lista de forma um por um mas n permite pular para o meio fim como é na lista -> nao tem index