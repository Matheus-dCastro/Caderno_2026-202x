- Tempo de capacidade cognitiva

### Modelo de Linguagem:
define qual sera o proximo texto mais provavel de ser gerado 
<font color="#ffff00">agente ve o mundo envia para o modelo oq ele viu (texto) e sai do modelo para o agente como texto.</font>

<mark style="background:#fff88f">decondificação autoregressiva</mark>


**token** é a menor unidade de texto que o modelo manipula definida por um vacabulario fixo construido antes de treino => pega o texto cru byte por byte, cada modelo tera seu tokenizador ou seja sempre irar produzir a mesmas seguencia (deterministico)

*cada token é associado a um indece ou seja cada palavra terá um id dentro do "Dicionario"* -> isso cria o vocabulario do angete/modelo

<mark style="background:#9254de">nesse passo ele ainda n determiniu o significado e nem a lingua apenas estas otimizando o texto para poder ser mais eficiente</mark>

### Formas de tokenizar:

<mark style="background:#d2cbff">por caractere</mark> => uma sequncia de simbolos, sequencias longas fazem com q o modelo gaste camadas para poder remontar oq foi mandado para ele <font color="#b2a2c7">(bola => "b" "o" "l" "a")</font>

<mark style="background:#d2cbff">por palavra</mark> => cada palavra vira um token (sequencias curtas, resumoe em um caracter) -> pode gerar falta de palavras e necessita de token especial pois cada palavra nova ou com erro de digitação cai em um UNK (algo como desconhecido)

<mark style="background:#d2cbff">por subword</mark> => quebra em pedaços para evitar o uso de caracteres especiais e otimizar o fluxo e o useo de token subistitutos sendo quase uma junção das duas anteriores <font color="#ffff00">ele pega sempre pelos mais frenquentes e vai quebrando</font> escolha de todos os modelo de linguagem no momento.

Com muitos tokens sao representações numericas das palavras, é preciso passar por um processo de vetorizar nos indeces dessas palavras para n implicar em vies no modelo assim ids maiores tem o mesmo grau de importancia de ids menores.

Artitimetica, soletração contagem custo sao umas das limitações.

<mark style="background:#fff88f">Ideas semelhantes ficam proximas no espaço vetorial.</mark>

### Modelo de linguagem:

*mantem as palavras mais frenquentes inteira e as raras em pedaços reutilizaveis*



Um modelo de lingugaem atribui uma distribuição de probalidade ao proximo token dado o texto anterior;
O modelo gera um token por vez n um contexto interio pela probablidade de ser o fim indeo de k+1 um por vez;


<font color="#92d050">**Byte Pair Encoding:**</font> os bytes sozinhos se unem a um adjacente mais frequente da mensagem. a cada nova fusao é add uma nova entrada ao vacabulario, processa para o tamanho escolhido.

## Oq dificulta quando faz:
- aritimetica -> contas grande se partem e o modelo se perde nos pedaços
- soletração -> contar letras n é uma info q o token expõe
- contagem -> pedir texto com x palavras esbarra no problema de token vs palavra
- custo -> quanto mais token produzidos masi custo 

o vocabulario V e a dimensão d => camada de emberdding é portanto uma consulta por linha sem fazer o uso de um produto matricial.

assim o proximo token é predito atravez das relações de uso durante o treino aproximando contextos similhantes (**vetro**) 
- a similaridade do cossendo é geralmente a medida usada com mais frequência.
- busca por significado, (RAG) consiste em transformar consultas e documentos em vetores seguindo a logica de cima as coisas semelhantes ficam proximas => assim ordenado as cosias.
- dimensoes individuais nao tem interpretacao isolada.

-> os resultados ficam entre -1 e 1 
-> suas normas sao dividas fora oq isola sua direção
-> vetores normalizados <=> produto = cosseno.


- **Indexação:** cada documento vira um vetor cacula uma vez e guarda
- **Consulta:** a pergunta tambem vira um vetor
- **Ordenação:** documentos saim ordenados pela simelaridade da consulta.

#### Posição entra com info add

<mark style="background:#ff4d4f">janela de contexto é o numero maximo de tokens q o modelo pode processar de uma vez</mark>


quando passa ou sera recuperado sob demanda ou irar ser resumido para q a info chege ate o modelo
quanto maior uma janela mais caro sera o procesamento do modelo => sobe o custo de atenção.



#### Ideia de atenção é mandar tudo de uma vez e gerar de forma paralelizada 


<mark style="background:#40a9ff">Codificação:</mark> traduz o texto em ID o unico tipo de entrada acieto pelo modelo
<mark style="background:#40a9ff">Execultar o forward pass</mark>
<mark style="background:#40a9ff">Escolher o ID</mark>
<mark style="background:#40a9ff">Decodificar </mark>



### Bloco do Transformer:

## Parametros do modelo:

ajustar valores durante a fase de treinamento para pode gerar/guiar a resposta do modelo e o que ele esta fazendo

-> Crescimento de conhecimento e oq pode fazer de forma exponencial

# Emergencia: 
é o aparecimento no conjunto de um comportamento que nenhuma das paretes exibe isoladamente.

=> modelos de raciocinio -> problema haha;

## Etapa 02

Criar uma ordenação para o modelo saber quais resposta são melhores para cada caso r1>r2.....



# Aula 03:

O prompt passa a ser parte da etapa de desenvolvimento
system -> exemplos -> historico -> ferramentas -> recuperado -> user
*tudo isso em uma unica sequencia de tokens e o modelo le a sequncia interira*

### mensagem de sistema:
uma mensagem fixa q oq muda geralmente sera apenas o historico da convera
**Delimitadores de prompt para melhores resultados** seja em md ou seja em xml(sendo esse para colocar marcadores e delimitadores de informaçoes das entradas do user)


#### Aprendizado em contexto:

zero-short: apenas a tarefa
one-short: com 1 exemplo
few-short: dois a dezenas de formato incomum ou vacabulario improprio
many-short: formado de forma dinamica

## Cahin-of-thought: pedir por passos a passo ou cadeia de pensamentos

