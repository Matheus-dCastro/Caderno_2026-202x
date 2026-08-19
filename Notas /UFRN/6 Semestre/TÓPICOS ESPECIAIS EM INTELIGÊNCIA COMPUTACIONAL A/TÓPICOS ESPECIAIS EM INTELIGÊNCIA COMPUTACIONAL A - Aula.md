- Tempo de capacidade cognitiva

### Modelo de Linguagem:

<mark style="background:#fff88f">decondificação autoregressiva</mark>


**token** é a menor unidade de texto que o modelo manipula definida por um vacabulario fixo construido antes de treino => pega o texto cru byte por byte, cada modelo tera seu tokenizador ou seja sempre irar produzir a mesmas seguencia (deterministico)

*cada token é associado a um indece ou seja cada palavra terá um id dentro do "Dicionario"* -> isso cria o vocabulario do angete/modelo

<mark style="background:#9254de">nesse passo ele ainda n determiniu o significado e nem a lingua apenas estas otimizando o texto para poder ser mais eficiente</mark>

### Formas de tokenizar:

por caractere => cada letra ja é basicamente o proprio token
por palavra => cada palavra vira um token (resumoe em um caracter) -> pode gerar falta de palavras e necessita de token especial
por subword => quebra em pedaços para evitar e otimizar o fluxo e o useo de token subistitutos (especiais: quando n aquele coisa cadastrada) sendo quase uma junção das duas anteriores <font color="#ffff00">ele pega sempre pelos mais frenquentes e vai quebrando</font>

passamor por um processo de vetorizar nos indeces para n implicar em vies no modelo

Artitimetica, soletração contagem custo sao umas das limitações.

<mark style="background:#fff88f">Ideas semelhantes ficam proximas no espaço vetorial.</mark>

### Modelo de linguagem:

Um modelo de lingugaem atribui uma distribuição de probalidade ao proximo token dado o texto anterior;
O modelo gera um token por vez n um contexto interio pela probablidade de ser o fim indeo de k+1 um por vez;

#### Ideia de atenção é mandar tudo de uma vez e gerar de forma paralelizada 

### Bloco do Transformer:

## Parametros do modelo:

ajustar valores durante a fase de treinamento para pode gerar/guiar a resposta do modelo e o que ele esta fazendo

-> Crescimento de conhecimento e oq pode fazer de forma exponencial

# Emergencia: 
é o aparecimento no conjunto de um comportamento que nenhuma das paretes exibe isoladamente.

=> modelos de raciocinio -> problema haha;

## Etapa 02

Criar uma ordenação para o modelo saber quais resposta são melhores para cada caso r1>r2.....



# Aula 04:

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