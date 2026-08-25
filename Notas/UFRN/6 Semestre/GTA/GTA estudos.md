# Fase 0:

focada na sintaxe e nos fundamentos dos paradgmas da linguagem, 

### Como detectar dados com a linguaguem:

==val:== apenas leitura => como uma constante valor n muda (usar val por padrao)
==var:== valor mutavel

-> os tipos base o kotlin seta sozinho

when: quando()

``` kotlin

Val x // leitura
var x // imutavel


```

feito para elimianar as faltas de nullpointeception
para uma variavel pode aceiatar null deve passar ?

``` kotlin

val x: Int = 4
val z = x?:0 // se o x fosse nulo ele iria receber 0 se o x n for nulo vai ser o valor do proprio

```

nesse caso ? serve para perguntar o valo da esquerda é nulo se sim faça o da frente

when é como se o switch