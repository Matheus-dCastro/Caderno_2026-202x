---
title: "Teorema de Bayes – Wikipédia, a enciclopédia livre"
source: "https://pt.wikipedia.org/wiki/Teorema_de_Bayes"
author:
  - "[[Wikipedia]]"
published:
created: 2026-06-05
description:
tags:
  - "clippings"
---
Em [teoria das probabilidades](https://pt.wikipedia.org/wiki/Teoria_das_probabilidades "Teoria das probabilidades") e [estatística](https://pt.wikipedia.org/wiki/Estat%C3%ADstica "Estatística"), o **teorema de Bayes** (alternativamente, a lei de Bayes ou a regra de Bayes) descreve a probabilidade de um evento, baseado em um conhecimento *[a priori](https://pt.wikipedia.org/wiki/A_priori_e_a_posteriori "A priori e a posteriori")* que pode estar relacionado ao evento. O teorema mostra como alterar as probabilidades *a* *priori* tendo em vista novas evidências para obter probabilidades *[a posteriori](https://pt.wikipedia.org/wiki/A_priori_e_a_posteriori "A priori e a posteriori").*[^1] Por exemplo, o teorema de Bayes pode ser aplicado ao [jogo das três portas](https://pt.wikipedia.org/wiki/Jogo_das_tr%C3%AAs_portas "Jogo das três portas") (também conhecido como problema de Monty Hall). [^2]

Uma das muitas aplicações do teorema de Bayes é a [inferência bayesiana](https://pt.wikipedia.org/wiki/Infer%C3%AAncia_bayesiana "Inferência bayesiana"), uma abordagem particular da [inferência estatística](https://pt.wikipedia.org/wiki/Infer%C3%AAncia_estat%C3%ADstica "Inferência estatística"). Quando aplicado, as probabilidades envolvidas no teorema de Bayes podem ter diferentes interpretações de probabilidade. Com a interpretação bayesiana de probabilidade, o teorema expressa como a probabilidade de um evento (ou o grau de crença na ocorrência de um evento) deve ser alterada após considerar evidências sobre a ocorrência deste evento. A inferência bayesiana é fundamental para a [estatística bayesiana](https://pt.wikipedia.org/wiki/Estat%C3%ADstica_bayesiana "Estatística bayesiana").[^3]

O teorema de Bayes recebe este nome devido ao pastor e [matemático](https://pt.wikipedia.org/wiki/Matem%C3%A1tico "Matemático") inglês [Thomas Bayes](https://pt.wikipedia.org/wiki/Thomas_Bayes "Thomas Bayes") (1701 – 1761), que foi o primeiro a fornecer uma equação que permitiria que novas evidências atualizassem a probabilidade de um evento a partir do conhecimento *a priori* (ou a crença inicial na ocorrência de um evento). O teorema de Bayes foi mais tarde desenvolvido por [Pierre-Simon Laplace](https://pt.wikipedia.org/wiki/Pierre-Simon_Laplace "Pierre-Simon Laplace"), que foi o primeiro a publicar uma formulação moderna em 1812 em seu livro Teoria Analítica de Probabilidade, na tradução do francês. [Harold Jeffreys](https://pt.wikipedia.org/wiki/Harold_Jeffreys "Harold Jeffreys") colocou o [algoritmo](https://pt.wikipedia.org/wiki/Algoritmo "Algoritmo") de Bayes e a formulação de Laplace em uma base axiomática. Jeffreys escreveu que " *o teorema de Bayes* *é para a teoria da probabilidade o que o teorema de Pitágoras é para a geometria".*[^4]

![](https://upload.wikimedia.org/wikipedia/commons/thumb/1/18/Bayes%27_Theorem_MMB_01.jpg/250px-Bayes%27_Theorem_MMB_01.jpg)

Placa de neon, mostrando a expressão do teorema de Bayes.

## História

![](https://upload.wikimedia.org/wikipedia/commons/thumb/f/f5/Bayes%27_Theorem_2D.svg/250px-Bayes%27_Theorem_2D.svg.png)

Visualização do teorema de Bayes.

O teorema de Bayes recebe este nome devido ao pastor e matemático inglês [Thomas Bayes](https://pt.wikipedia.org/wiki/Thomas_Bayes "Thomas Bayes") (1701 – 1761), que estudou como calcular a distribuição para o parâmetro de probabilidade de uma [distribuição binomial](https://pt.wikipedia.org/wiki/Distribui%C3%A7%C3%A3o_binomial "Distribuição binomial") (terminologia moderna). O manuscrito não publicado de Bayes foi editado significativamente por [Richard Price](https://pt.wikipedia.org/wiki/Richard_Price_\(fil%C3%B3sofo\) "Richard Price (filósofo)") antes de ser lido postumamente na [Royal Society](https://pt.wikipedia.org/wiki/Royal_Society "Royal Society"). Price editou o principal trabalho de Bayes *An Essay towards Solving a Problem in the Doctrine of Chances* (1763),[^5] que aparece em *Philosophical Transactions* [^6] e contém o teorema de Bayes. Price escreveu uma introdução para o artigo, que fornece algumas das bases filosóficas da estatística bayesiana. Em 1765, Price foi eleito membro da Royal Society em reconhecimento ao seu trabalho sobre o legado de Bayes.[^7] O matemático francês [Pierre-Simon Laplace](https://pt.wikipedia.org/wiki/Pierre-Simon_Laplace "Pierre-Simon Laplace") reproduziu e estendeu os resultados de Bayes em 1774, aparentemente sem ter conhecimento do trabalho de Bayes.[^8] [^9] [^10] A interpretação bayesiana da probabilidade foi desenvolvida principalmente por Laplace.[^11] Stephen Stigler sugeriu em 1983 que o teorema de Bayes foi descoberto pelo matemático inglês cego [Nicholas Saunderson](https://pt.wikipedia.org/wiki/Nicholas_Saunderson "Nicholas Saunderson") pouco antes de Bayes.[^12] [^13] Entretanto, esta interpretação tem sido contestada.[^14] Martyn Hooper [^15] e Sharon McGrayne [^16] argumentaram que a contribuição de Richard Price foi substancial:

| “ | Por padrões modernos, devemos nos referir à regra Bayes–Price. Price descobriu o trabalho de Bayes, reconheceu sua importância, corrigiu–o, contribuiu para o artigo e encontrou um uso para ele. A convenção moderna de empregar apenas o nome de Bayes é injusta, mas tão arraigada que faz todo o resto não ter quase nenhum sentido.[^16] | ” |
| --- | --- | --- |

## Definição formal

![](https://upload.wikimedia.org/wikipedia/commons/thumb/1/10/Scheme_for_Bayes%27_theorem.png/250px-Scheme_for_Bayes%27_theorem.png)

Visão esquemática do teorema de Bayes, em que {\\displaystyle Bi} é uma partição do espaço de probabilidade {\\displaystyle \\Omega } e {\\displaystyle A} é um evento qualquer.

O teorema de Bayes é um [corolário](https://pt.wikipedia.org/wiki/Corol%C3%A1rio "Corolário") da [lei da probabilidade total](https://pt.wikipedia.org/wiki/Lei_da_probabilidade_total "Lei da probabilidade total"), expresso matematicamente na forma da seguinte equação:

${\displaystyle P(A\mid B)={\frac {P(B\mid A)\,P(A)}{P(B)}}}$,

em que ${\displaystyle A}$ e ${\displaystyle B}$ são eventos e ${\displaystyle P(B)\neq 0}$.[^17] [^18]

O teorema de Bayes também pode ser escrito da seguinte maneira:

${\displaystyle P(A\mid B)\,P(B)=P(A\cap B)=P(B\cap A)=P(B\mid A)\,P(A)=P(A\mid B)\,P(B)}$ [^17] [^19]

- ${\displaystyle P(A)}$ e ${\displaystyle P(B)}$ são as [probabilidades](https://pt.wikipedia.org/wiki/Probabilidade_condicionada "Probabilidade condicionada") *[a priori](https://pt.wikipedia.org/wiki/A_priori "A priori")* de ${\displaystyle A}$ e ${\displaystyle B}$;
- ${\displaystyle P(A\mid B)}$ é a probabilidade *[a posteriori](https://pt.wikipedia.org/wiki/A_posteriori "A posteriori")* ([probabilidade condiciona](https://pt.wikipedia.org/wiki/Probabilidade_condicionada "Probabilidade condicionada") [da](https://pt.wikipedia.org/wiki/Probabilidade_condicionada "Probabilidade condicionada")) de ${\displaystyle A}$ [condicional](https://pt.wikipedia.org/wiki/Probabilidade_condicionada "Probabilidade condicionada") a ${\displaystyle B}$;
- ${\displaystyle P(B\mid A)}$ é a probabilidade *[a posteriori](https://pt.wikipedia.org/wiki/A_posteriori "A posteriori")* ([probabilidade condiciona](https://pt.wikipedia.org/wiki/Probabilidade_condicionada "Probabilidade condicionada") [da](https://pt.wikipedia.org/wiki/Probabilidade_condicionada "Probabilidade condicionada")) de ${\displaystyle B}$ [condicional](https://pt.wikipedia.org/wiki/Probabilidade_condicionada "Probabilidade condicionada") a ${\displaystyle A}$.[^17] [^19]

## Exemplo

![](https://upload.wikimedia.org/wikipedia/commons/thumb/8/88/Bayes_theorem_drugs_example_tree.svg/250px-Bayes_theorem_drugs_example_tree.svg.png)

Diagrama em árvore para o teste de droga, em que U, Ū, + e − são os eventos representando usuário, não usuário, resultado positivo e resultado negativo, respectivamente. As porcentagens entre parêntesis são calculadas.

### Teste de drogas

Seja um teste de drogas 99% sensível e 99% específico. Isto é, o teste produzirá 99% de resultados verdadeiros positivos para usuários de drogas e 99% de resultados verdadeiros negativos para não-usuários de drogas. Suponha que 0,5% das pessoas são usuárias de drogas. Se um indivíduo selecionado aleatoriamente testar positivo, qual a probabilidade de ele ser usuário de drogas? Isto é, qual a probabilidade de não se cometer um [falso positivo](https://pt.wikipedia.org/wiki/Falso_positivo "Falso positivo")?[^20]

${\displaystyle {\begin{aligned}P({\text{usuário}}\mid {\text{+}})&={\frac {P({\text{+}}\mid {\text{usuário}})P({\text{usuário}})}{P(+)}}\\&={\frac {P({\text{+}}\mid {\text{usuário}})P({\text{usuário}})}{P({\text{+}}\mid {\text{usuário}})P({\text{usuário}})+P({\text{+}}\mid {\text{não usuário}})P({\text{não usuário}})}}\\[8pt]&={\frac {0,99\times 0,005}{0,99\times 0,005+0,01\times 0,995}}\\[8pt]&\approx 33,2\%\end{aligned}}}$

Mesmo com a aparente precisão do teste, se um indivíduo testar positivo, é mais provável que ele não seja do que ele seja usuário de drogas. Isto porque o número de não-usuários é muito maior que o número de usuários de drogas. Então, o número de falsos positivos supera o número de positivos verdadeiros. Para usar números concretos, se 1000 indivíduos forem testados, espera–se que 995 não sejam usuários e 5 sejam usuários de drogas. Para os 995 não-usuários de drogas, são esperados ${\displaystyle 0,01\times 995\approx 10}$ falsos positivos. Para os 5 usuários de drogas, são esperados ${\displaystyle 0,99\times 5\approx 5}$ positivos verdadeiros. Isto é, dos 15 resultados positivos, apenas 5 (ou 33%) são genuínos. Isto ilustra a importância da probabilidade condicional e como políticas podem ser equivocadas se as probabilidades condicionais forem negligenciadas.[^21] [^20]

A importância da especificidade pode ser observada calculando–se que, mesmo se a sensibilidade for aumentada para 100% e a especificidade permanecer em 99%, a probabilidade do indivíduo ser um usuário de drogas subirá apenas de 33,2% para 33,4%. Entretanto, se a sensibilidade for mantida em 99% e a especificidade for aumentada para 99,5%, então a probabilidade do indivíduo ser um usuário de droga sobe para cerca de 49,9%.[^20]

## Interpretações

![](https://upload.wikimedia.org/wikipedia/commons/thumb/7/7a/Bayes_theorem_assassin.svg/250px-Bayes_theorem_assassin.svg.png)

Visualização geométrica do teorema de Bayes. Na tabela, os valores 3, 1, 2 e 6 fornecem os pesos relativos de cada caso e condição correspondente. As imagens mostram as células da tabela envolvidas em cada métrica, sendo a probabilidade a fração de cada figura que está sombreada. Isto mostra que: {\\displaystyle P(A\\mid B)\\times P(B)=P(B\\mid A)\\times P(A)}. Isto é: {\\displaystyle P(A\\mid B)={\\frac {P(B\\mid A)\\times P(A)}{P(B)}}}. Um raciocínio semelhante mostra que: {\\displaystyle P({\\bar {A}}\\mid B)={\\frac {P(B\\mid {\\bar {A}})\\times P({\\bar {A}})}{P(B)}}}.

A interpretação do teorema de Bayes depende da interpretação da probabilidade atribuída aos termos. As duas interpretações principais são descritas abaixo.

### Interpretação bayesiana

Na interpretação bayesiana (ou epistemológica), a probabilidade mede o *grau de crença*. O teorema de Bayes liga o grau de crença em uma posição antes e depois de se considerar as evidências. Por exemplo, acredita–se com 50% de certeza que uma moeda tem o dobro de probabilidade de cair cara. Se a moeda for jogada várias vezes, o grau de crença pode aumentar, diminuir ou se manter igual dependendo dos resultados observados (ver [inferência bayesiana](https://pt.wikipedia.org/wiki/Infer%C3%AAncia_bayesiana "Inferência bayesiana")).[^22]

Para proposição ${\displaystyle A}$ e evidência ${\displaystyle B}$:

- ${\displaystyle P(A)}$ (probabilidade *a priori*) é o grau de crença inicial em ${\displaystyle A}$;
- ${\displaystyle P(A\mid B)}$ (probabilidade *a posteriori*) é o grau de crença que representa ${\displaystyle B}$;
- O quociente ${\displaystyle {\frac {P(B\mid A)}{P(B)}}}$ é o suporte que ${\displaystyle B}$ fornece para ${\displaystyle A}$.[^22]

### Interpretação frequencista

![](https://upload.wikimedia.org/wikipedia/commons/thumb/6/61/Bayes_theorem_tree_diagrams.svg/250px-Bayes_theorem_tree_diagrams.svg.png)

Ilustração da interpretação frequentista com o diagrama de árvore. O teorema de Bayes liga as probabilidades condicionais aos seus inversos.

Na [interpretação frequencista](https://pt.wikipedia.org/wiki/Infer%C3%AAncia_frequencista "Inferência frequencista"), a probabilidade mede uma *proporção de resultados*. Por exemplo, suponha-se que uma experiência seja realizada muitas vezes. ${\displaystyle P(A)}$ é a proporção de resultados com propriedade ${\displaystyle A}$ e ${\displaystyle P(B)}$ é a proporção de resultados com propriedade ${\displaystyle B}$. ${\displaystyle P(B\mid A)}$ é a proporção de resultados com propriedade ${\displaystyle B}$, excluindo os resultados sem propriedade ${\displaystyle A}$, e ${\displaystyle P(A\mid B)}$ é a proporção de resultados com propriedade ${\displaystyle A}$, excluindo os resultados sem propriedade ${\displaystyle B}$.[^23]

## Probabilidades condicionais

O papel do teorema de Bayes é melhor visualizado com o diagrama de árvore. Os dois diagramas dividem os mesmos resultados em ${\displaystyle A}$ e em ${\displaystyle B}$ em ordens opostas, para obter as probabilidades inversas. O teorema de Bayes serve como ligação entre estas diferentes partições.[^24]

Por exemplo, um [entomologista](https://pt.wikipedia.org/wiki/Entomologia "Entomologia") vê o que poderia ser uma rara subespécie de besouro devido a um padrão em suas costas. Nas subespécies raras, 98% dos indivíduos tem o padrão. Isto é, ${\displaystyle P({\text{padrão}}\mid {\text{raro}})=98\%}$. Nas subespécies comuns, 5% dos indivíduos tem o padrão. Estas subespécies raras correspondem a apenas 0,1% da população. Então, qual a probabilidade do besouro com padrão ser raro? Em outras palavras, qual o valor de ${\displaystyle P({\text{raro}}\mid {\text{padrão}})}$?[^24]

Da expressão estendida do teorema de Bayes (uma vez que qualquer besouro pode ser apenas raro ou comum), tem–se:

${\displaystyle {\begin{aligned}P({\text{raro}}\mid {\text{padrão}})&={\frac {P({\text{padrão}}\mid {\text{raro}})P({\text{raro}})}{P({\text{padrão}}\mid {\text{raro}})P({\text{raro}})+P({\text{padrão}}\mid {\text{comum}})P({\text{comum}})}}\\[8pt]&={\frac {0,98\times 0,001}{0,98\times 0,001+0,05\times 0,999}}\\[8pt]&\approx 1,9\%\end{aligned}}}$

Isto é, o besouro com um padrão nas costas encontrado pelo entomologista tem probabilidade de 1,9% de ser raro.[^24]

## Formas

### Eventos

#### Forma simples

Para eventos ${\displaystyle A}$ e ${\displaystyle B}$, dado ${\displaystyle P(B)\neq 0}$:

${\displaystyle P(A\mid B)={\frac {P(B\mid A)\,P(A)}{P(B)}}}$.[^25]

Na inferência bayesiana, deseja-se saber o grau de crença em um evento (ou conjunto de eventos) ${\displaystyle A}$, condicionalmente à ocorrência de um evento (ou conjunto de eventos) ${\displaystyle B}$ fixado (quantidade que é conhecida como distribuição *a posteriori*). O teorema de Bayes mostra que a distribuição *a posteriori* é proporcional à probabilidade de ${\displaystyle B}$ dado ${\displaystyle A}$ (que corresponde à [função de verossimilhança](https://pt.wikipedia.org/wiki/Fun%C3%A7%C3%A3o_de_verossimilhan%C3%A7a "Função de verossimilhança") da amostra) vezes a probabilidade de A (chamada de probabilidade *a priori* ou grau de crença antes da coleta de evidências):

${\displaystyle P(A\mid B)\propto P(A)\times P(B\mid A)\ }$ (proporcionalmente sobre ${\displaystyle A}$ para dado ${\displaystyle B}$).[^26] [^25]

#### Forma alternativa

Outra forma do teorema de Bayes que é geralmente encontrada quando são consideradas duas afirmações ou hipóteses concorrentes é:

${\displaystyle P(A\mid B)={\frac {P(B\mid A)\,P(A)}{P(B\mid A)P(A)+P(B\mid A^{c})P(A^{c})}}}$.[^27]

Para proposição ${\displaystyle A}$ e evidência ${\displaystyle B}$:

- ${\displaystyle P(A)}$ (probabilidade *a priori*) é o grau de crença inicial em ${\displaystyle A}$;
- ${\displaystyle P(A^{c})}$ é a probabilidade correspondente do grau de crença inicial contra ${\displaystyle A}$. ${\displaystyle P(A^{c})=1-P(A)}$;
- ${\displaystyle P(B\mid A)}$ (probabilidade condicional ou verossimilhança) é o grau de crença em ${\displaystyle B}$, dado que a proposição ${\displaystyle A}$ é verdadeira;
- ${\displaystyle P(B\mid A^{c})}$ (probabilidade condicional ou verossimilhança) é o grau de crença em ${\displaystyle B}$, dado que a proposição ${\displaystyle A}$ é falsa;
- ${\displaystyle P(A\mid B)}$ (probabilidade *a posteriori*) é a probabilidade para *${\displaystyle A}$*, após considerar ${\displaystyle B}$ para e contra *${\displaystyle A}$*.[^28]

#### Forma estendida

Para alguma partição ${\displaystyle \{A_{j}\}}$ do [espaço amostral](https://pt.wikipedia.org/wiki/Espa%C3%A7o_amostral "Espaço amostral"), muitas vezes o espaço do evento é dado em termos de ${\displaystyle P(A_{j})}$ e ${\displaystyle P(B\mid A_{j})}$. Isto é útil para calcular ${\displaystyle P(B)}$, usando a [lei de probabilidade total](https://pt.wikipedia.org/wiki/Lei_da_probabilidade_total "Lei da probabilidade total"):

${\displaystyle P(B)={\sum _{j}P(B\mid A_{j})P(A_{j})}\Rightarrow P(A_{i}\mid B)={\frac {P(B\mid A_{i})\,P(A_{i})}{\sum \limits _{j}P(B\mid A_{j})\,P(A_{j})}}}$.[^27]

### Variáveis aleatórias

![](https://upload.wikimedia.org/wikipedia/commons/thumb/5/5b/Bayes_continuous_diagram.svg/250px-Bayes_continuous_diagram.svg.png)

Diagrama ilustrando o significado do teorema de Bayes como aplicado a um espaço de evento gerado por variáveis aleatórias contínuas {\\displaystyle X} e {\\displaystyle Y}. Existe uma instância do teorema de Bayes para cada ponto no domínio. Na prática, estas instâncias podem ser parametrizadas escrevendo as densidades de probabilidade específicas como funções de {\\displaystyle x} {\\displaystyle y}.

Seja o espaço amostral ${\displaystyle \Omega }$ gerado por duas variáveis aleatórias ${\displaystyle X}$ e ${\displaystyle Y}$. Em princípio, o teorema de Bayes aplica–se aos eventos ${\displaystyle A=\{X=x\}}$ e ${\displaystyle B=\{Y=y\}}$. Entretanto, os termos se tornam 0 nos pontos em que qualquer variável tem densidade de probabilidade finita. Para continuar útil, o teorema de Bayes pode ser formulado em termos de densidades relevantes.

#### Forma simples

Se ${\displaystyle X}$ é contínua e ${\displaystyle Y}$ é discreta,

${\displaystyle f_{X}(x\mid Y=y)={\frac {P(Y=y\mid X=x)\,f_{X}(x)}{P(Y=y)}}.}$ [^29]

Se ${\displaystyle X}$ é discreta e ${\displaystyle Y}$ é contínua,

${\displaystyle P(X=x\mid Y=y)={\frac {f_{Y}(y\mid X=x)\,P(X=x)}{f_{Y}(y)}}.}$ [^29]

Se ${\displaystyle X}$ e ${\displaystyle Y}$ são contínuas,

${\displaystyle f_{X}(x\mid Y=y)={\frac {f_{Y}(y\mid X=x)\,f_{X}(x)}{f_{Y}(y)}},}$

em ${\displaystyle f_{X}}$ e ${\displaystyle f_{Y}}$ representam as funções de [distribuição de probabilidade](https://pt.wikipedia.org/wiki/Distribui%C3%A7%C3%A3o_de_probabilidade "Distribuição de probabilidade") de ${\displaystyle X}$ e ${\displaystyle Y}$, respectivamente.[^29]

#### Forma estendida

![](https://upload.wikimedia.org/wikipedia/commons/thumb/1/17/Continuous_event_space_specification.svg/250px-Continuous_event_space_specification.svg.png)

Diagrama ilustrando como um espaço de evento gerado por variáveis aleatórias contínuas {\\displaystyle X} e {\\displaystyle Y} geralmente é concebido.

Um espaço de evento contínuo muitas vezes é dado em termos dos termos do numerador. Então, é útil eliminar o denominador usando a lei de probabilidade total. Para ${\displaystyle f_{Y}(y)}$, isto se torna uma integral:

${\displaystyle f_{Y}(y)=\int _{-\infty }^{\infty }f_{Y}(y\mid X=\xi )\,f_{X}(\xi )\,d\xi .}$ [^29]

### Regra de Bayes

A regra da Bayes é o teorema de Bayes na forma de chances:

${\displaystyle O(A_{1}:A_{2}\mid B)=O(A_{1}:A_{2})\cdot \Lambda (A_{1}:A_{2}\mid B)}$,

em que

${\displaystyle \Lambda (A_{1}:A_{2}\mid B)={\frac {P(B\mid A_{1})}{P(B\mid A_{2})}}}$

é chamado de fator Bayes ou razão de verossimilhança. As chances entre os dois eventos é simplesmente a razão entre as probabilidades dos dois eventos.

Então,

${\displaystyle O(A_{1}:A_{2})={\frac {P(A_{1})}{P(A_{2})}},}$

${\displaystyle O(A_{1}:A_{2}\mid B)={\frac {P(A_{1}\mid B)}{P(A_{2}\mid B)}}.}$

Portanto, a regra de Bayes afirma que as chances posteriores são as chances iniciais multiplicadas pelo fator de Bayes. Em outras palavras, as probabilidades *a posteriori* são proporcionais às probabilidades *a priori*.[^30]

## Derivação

### Para eventos

O teorema de Bayes pode ser derivado a partir da definição de probabilidade condicional:

${\displaystyle P(A\mid B)={\frac {P(A\cap B)}{P(B)}},{\text{ se }}P(B)\neq 0,\!}$

${\displaystyle P(B\mid A)={\frac {P(B\cap A)}{P(A)}},{\text{ se }}P(A)\neq 0,\!}$

pois ${\displaystyle P(B\cap A)=P(A\cap B)}$.

Então,

${\displaystyle P(A\cap B)=P(A\mid B)\,P(B)=P(B\mid A)\,P(A)\!}$

Logo, ajustando-se os termos, tem-se:

${\displaystyle P(A\mid B)={\frac {P(B\mid A)\,P(A)}{P(B)}},{\text{ se }}P(B)\neq 0.}$ [^31]

### Para variáveis aleatórias

Para duas [variáveis aleatórias](https://pt.wikipedia.org/wiki/Vari%C3%A1vel_aleat%C3%B3ria "Variável aleatória") contínuas ${\displaystyle X}$ e ${\displaystyle Y}$, o teorema de Bayes pode ser analogamente derivado da definição de probabilidade condicional:${\displaystyle f_{X}(x\mid Y=y)={\frac {f_{X,Y}(x,y)}{f_{Y}(y)}}}$

${\displaystyle f_{Y}(y\mid X=x)={\frac {f_{X,Y}(x,y)}{f_{X}(x)}}}$

${\displaystyle f_{X}(x\mid Y=y)={\frac {f_{Y}(y\mid X=x)\,f_{X}(x)}{f_{Y}(y)}}.}$ [^31]

## Ver também

- [Epistemologia bayesiana](https://pt.wikipedia.org/wiki/Epistemologia_bayesiana "Epistemologia bayesiana")
- [Filtro bayesiano](https://pt.wikipedia.org/wiki/Filtro_bayesiano "Filtro bayesiano")
- [Inferência bayesiana](https://pt.wikipedia.org/wiki/Infer%C3%AAncia_bayesiana "Inferência bayesiana")
- [Limite de Chernoff](https://pt.wikipedia.org/wiki/Limite_de_Chernoff "Limite de Chernoff")

## Referências

## Leitura adicional

- Bruss, F. Thomas (18 de setembro de 2013). « **250 years of "An essay towards solving a problem in the doctrine of chances. By the late Rev. Mr. Bayes, F.R.S. communicated by Mr. Price, in a letter to John Canton, A.M.F.R.S."** ». *Jahresbericht der Deutschen Mathematiker-Vereinigung – Springer Journals*. **115** (3-4): 129-133. [doi](https://pt.wikipedia.org/wiki/Digital_object_identifier "Digital object identifier"):[10.1365/s13291-013-0069-z](https://dx.doi.org/10.1365%2Fs13291-013-0069-z)
- Bussab, Wilton de O.; Morettin, Pedro A. (2010). *Estatística Básica* 6 ed. São Paulo: Saraiva. 540 páginas
- DeDeo, Simon (30 de novembro de 2016). [« **Bayesian Reasoning for Intelligent People** »](http://tuvalu.santafe.edu/~simon/br.pdf) (PDF). Consultado em 8 de junho de 2016
- Farias, Ana Maria Lima de; Laurencel, Luiz da Costa (2006). [«Probabilidade»](http://www.uff.br/ieeanamariafarias/probabilidade). Universidade Federal Fluminense (UFF)
- Gelman, Andrew; Carlin, John B.; Stern, Hal S.; Dunson, David B.; Vehtari, Aki; Rubin, Donald B. (2014). ***Bayesian data analysis*** 3 ed. Boca Raton: Chapman & Hall
- Grinstead, Charles M.; Snell, J. Laurie (2003). [***Introduction to Probability***](https://math.dartmouth.edu/~prob/prob/prob.pdf) (PDF). \[S.l.\]: American Mathematical Society
- Hazewinkel, Michiel (2001). ***Encyclopedia of mathematics***. \[S.l.: s.n.\]
- Laplace, Pierre-Simon (1840). [***Essai philosophique sur les probabilités***](https://fr.wikisource.org/wiki/Essai_philosophique_sur_les_probabilit%C3%A9s) (em francês). Paris: Bachelier
- Laplace, Pierre-Simon (1986). « **Memoir on the probability of the causes of events** ». *Statistical Science*. **1** (3): 364-378. [JSTOR](https://pt.wikipedia.org/wiki/JSTOR "JSTOR") [2245476](https://www.jstor.org/stable/2245476)
- Lee, Peter M (2012). ***Bayesian statistics: an introduction*** 4 ed. \[S.l.\]: John Wiley & Sons. 486 páginas. [ISBN](https://pt.wikipedia.org/wiki/International_Standard_Book_Number "International Standard Book Number") [978-1-118-33257-3](https://pt.wikipedia.org/wiki/Especial:Fontes_de_livros/978-1-118-33257-3 "Especial:Fontes de livros/978-1-118-33257-3")
- Mcgrayne, Sharon B. (2011). ***The Theory That Would Not Die: How Bayes' Rule Cracked the Enigma Code, Hunted Down Russian Submarines, and Emerged Triumphant from Two Centuries of Controversy***. London: Yale University Press. [JSTOR](https://pt.wikipedia.org/wiki/JSTOR "JSTOR") [j.ctt1np76s](https://www.jstor.org/stable/j.ctt1np76s)
- Puga, Jorge L.; Krzywinski, Martin; Altman, Naomi (2015). [« **Points of Significance: Bayes' theorem** »](https://www.nature.com/nmeth/journal/v12/n4/pdf/nmeth.3335.pdf) (PDF). *Nature Methods*. **12** (4): 277-278
- Rosenthal, Jeffrey S. (2005). ***Struck by Lightning: The Curious World of Probabilities*** 1 ed. \[S.l.\]: HarperCollins. [ISBN](https://pt.wikipedia.org/wiki/International_Standard_Book_Number "International Standard Book Number") [978-0309097345](https://pt.wikipedia.org/wiki/Especial:Fontes_de_livros/978-0309097345 "Especial:Fontes de livros/978-0309097345")
- Stigler, Stephen M. (1986). [« **Laplace's 1774 Memoir on Inverse Probability** »](http://projecteuclid.org/download/pdf_1/euclid.ss/1177013620). *Statistical Science*. **1** (3): 359-378
- Stone, James V. (2013). ***Bayes' Rule: A tutorial introduction to Bayesian Analysis*** 1 ed. \[S.l.\]: Sebtel Press. [ISBN](https://pt.wikipedia.org/wiki/International_Standard_Book_Number "International Standard Book Number") [978-0-9563728-4-0](https://pt.wikipedia.org/wiki/Especial:Fontes_de_livros/978-0-9563728-4-0 "Especial:Fontes de livros/978-0-9563728-4-0")

## Ligações externas

- [An Intuitive Explanation of Bayes' Theorem](http://yudkowsky.net/rational/bayes)
- [Bayes Theorem and the Possibility of False Claims](https://web.archive.org/web/20140202131520/http://rldinvestments.com/Articles/BayesTheorem.html)
- [Conditional Probability Explained Visually (Bayes' Theorem)](https://www.youtube.com/watch?v=Zxm4Xxvzohk)
- [Earliest Known Uses of Some of the Words of Mathematics (B)](http://jeff560.tripod.com/b.html)
- [Explaining Bayesian Problems Using Visualizations](https://www.youtube.com/watch?v=D8VZqxcu0I0)
- [Probability and Bayes’ Theorem](http://www.celiagreen.com/charlesmccreery/statistics/bayestutorial.pdf)
- [The Mathematics of Changing Your Mind](https://www.nytimes.com/2011/08/07/books/review/the-theory-that-would-not-die-by-sharon-bertsch-mcgrayne-book-review.html)
- Weisstein, Eric W. [Bayes' Theorem.](http://mathworld.wolfram.com/BayesTheorem.html) From *MathWorld* --A Wolfram Web Resource.

[^1]: [Bussab & Morettin 2010](#CITEREFBussabMorettin2010), p. 121-122.

[^2]: Neto, Joaquim (2010). [«Inferência Bayesiana»](http://www.ufjf.br/joaquim_neto/files/2009/09/IB-Slides-v1.1.pdf) (PDF). Universidade Federal de Juiz de Fora (UFJF). Consultado em 25 de maio de 2017

[^3]: [Bussab & Morettin 2010](#CITEREFBussabMorettin2010), p. 317-318.

[^4]: Jeffreys, Harold (1973). *Scientific Inference* 3rd ed. \[S.l.\]: [Cambridge University Press](https://pt.wikipedia.org/wiki/Cambridge_University_Press "Cambridge University Press"). p. 31. [ISBN](https://pt.wikipedia.org/wiki/International_Standard_Book_Number "International Standard Book Number") [978-0-521-18078-8](https://pt.wikipedia.org/wiki/Especial:Fontes_de_livros/978-0-521-18078-8 "Especial:Fontes de livros/978-0-521-18078-8")

[^5]: Allen, Richard (1999). [*David Hartley on Human Nature*](https://books.google.com/books?id=NCu6HhGlAB8C&pg=PA243). \[S.l.\]: SUNY Press. pp. 243–244. [ISBN](https://pt.wikipedia.org/wiki/International_Standard_Book_Number "International Standard Book Number") [978-0-7914-9451-6](https://pt.wikipedia.org/wiki/Especial:Fontes_de_livros/978-0-7914-9451-6 "Especial:Fontes de livros/978-0-7914-9451-6"). Consultado em 16 de junho de 2013

[^6]: Bayes, Thomas; Price, Richard (1763). [«An Essay towards solving a Problem in the Doctrine of Chance. By the late Rev. Mr. Bayes, communicated by Mr. Price, in a letter to John Canton, A. M. F. R. S.»](https://web.archive.org/web/20110410085940/http://www.stat.ucla.edu/history/essay.pdf) (PDF). *Philosophical Transactions of the Royal Society of London*. **53** (0): 370–418. [doi](https://pt.wikipedia.org/wiki/Digital_object_identifier "Digital object identifier"):[10.1098/rstl.1763.0053](https://dx.doi.org/10.1098%2Frstl.1763.0053). Consultado em 17 de julho de 2017. Arquivado do [original](http://www.stat.ucla.edu/history/essay.pdf) (PDF) em 10 de abril de 2011

[^7]: Price, Richard (1991). [*Price: Political Writings*](https://books.google.com/books?id=xdH-gjy2vzUC&pg=PR23). \[S.l.\]: Cambridge University Press. p. xxiii. [ISBN](https://pt.wikipedia.org/wiki/International_Standard_Book_Number "International Standard Book Number") [978-0-521-40969-8](https://pt.wikipedia.org/wiki/Especial:Fontes_de_livros/978-0-521-40969-8 "Especial:Fontes de livros/978-0-521-40969-8"). Consultado em 16 de junho de 2013

[^8]: Laplace, Pierre-Simon et al. Mémoire sur la probabilité des causes par les évènements. Mémoires présentés par divers savants \[à l’Académie royale des sciences\], Paris, Imprimerie royale, v. 6, p. 621-656, 1774.

[^9]: Laplace, Pierre-Simon. Mémoire sur les approximations des formules qui sont fonctions de tres grands nombres. Œuvres completes X, Paris, p. 209-291, 1785.

[^10]: Daston, Lorraine (1988). [*Classical Probability in the Enlightenment*](https://books.google.com/books?id=oq8XNbKyUewC&pg=PA268). \[S.l.\]: Princeton Univ Press. p. 268. [ISBN](https://pt.wikipedia.org/wiki/International_Standard_Book_Number "International Standard Book Number") [0-691-08497-1](https://pt.wikipedia.org/wiki/Especial:Fontes_de_livros/0-691-08497-1 "Especial:Fontes de livros/0-691-08497-1")

[^11]: Stigler, Stephen M. (1986). *The History of Statistics: The Measurement of Uncertainty before 1900*. Harvard University Press, Chapter 3.

[^12]: Stigler, Stephen M (1983). «Who Discovered Bayes' Theorem?». *The American Statistician*. **37** (4): 290–296. [doi](https://pt.wikipedia.org/wiki/Digital_object_identifier "Digital object identifier"):[10.1080/00031305.1983.10483122](https://dx.doi.org/10.1080%2F00031305.1983.10483122)

[^13]: De Vaux, Richard; Velleman, Paul; Bock, David (2016). *Stats, Data and Models* 4 ed. \[S.l.\]: Pearson. pp. 380–381. [ISBN](https://pt.wikipedia.org/wiki/International_Standard_Book_Number "International Standard Book Number") [978-0-321-98649-8](https://pt.wikipedia.org/wiki/Especial:Fontes_de_livros/978-0-321-98649-8 "Especial:Fontes de livros/978-0-321-98649-8")

[^14]: Edwards, A. W. F. (1986). «Is the Reference in Hartley (1749) to Bayesian Inference?». *The American Statistician*. **40** (2): 109–110. [doi](https://pt.wikipedia.org/wiki/Digital_object_identifier "Digital object identifier"):[10.1080/00031305.1986.10475370](https://dx.doi.org/10.1080%2F00031305.1986.10475370)

[^15]: Hooper, Martyn (2013). «Richard Price, Bayes' theorem, and God». *Significance*. **10** (1): 36–39. [doi](https://pt.wikipedia.org/wiki/Digital_object_identifier "Digital object identifier"):[10.1111/j.1740-9713.2013.00638.x](https://dx.doi.org/10.1111%2Fj.1740-9713.2013.00638.x)

[^16]: [Mcgrayne 2011](#CITEREFMcgrayne2011).

[^17]: Stuart, A.; Ord, K. (1994). *Kendall's Advanced Theory of Statistics: Volume I—Distribution Theory*. \[S.l.\]: Edward Arnold.

[^18]: [Bussab & Morettin 2010](#CITEREFBussabMorettin2010), p. 116.

[^19]: [Bussab & Morettin 2010](#CITEREFBussabMorettin2010), p. 111.

[^20]: Keedwell, Edward; Narayanan, Ajit (2005). *Intelligent Bioinformatics: The Application of Artificial Intelligence Techniques to Bioinformatics Problems*. \[S.l.\]: Joh Wiley and Sons. pp. 108 — 111. 279 páginas

[^21]: Daniel Kahneman (25 de outubro de 2011). [*Thinking, Fast and Slow*](https://books.google.com/books?id=ZuKTvERuPG8C). \[S.l.\]: Macmillan. [ISBN](https://pt.wikipedia.org/wiki/International_Standard_Book_Number "International Standard Book Number") [978-1-4299-6935-2](https://pt.wikipedia.org/wiki/Especial:Fontes_de_livros/978-1-4299-6935-2 "Especial:Fontes de livros/978-1-4299-6935-2"). Consultado em 8 de abril de 2012

[^22]: [«O Teorema de Bayes»](https://edisciplinas.usp.br/pluginfile.php/3110753/mod_resource/content/1/aula2.pdf) (PDF). Universidade de São Paulo (USP). Consultado em 25 de maio de 2017

[^23]: Tripathi, Subhashini Sharma (2016). *Learn Business Analytics in Six Steps Using SAS and R: A Practical, Step—by—Step to Learning Business Analytics*. \[S.l.\]: Apress. p. 132. 218 páginas

[^24]: [Farias & Laurencel 2006](#CITEREFFariasLaurencel2006), p. 49-56.

[^25]: Kim, Nam-Ho; An, Dawn; Choi, Joo-Ho (2017). *Prognostics and Health Management of Engineering Systems: An Introduction*. \[S.l.\]: Springer. p. 93 — 94. 346 páginas

[^26]: [Lee 2012](#CITEREFLee2012), p. capítulo 1.

[^27]: [Farias & Laurencel 2006](#CITEREFFariasLaurencel2006), p. 71-72.

[^28]: Orloff, Jeremy; Bloom, Jonathan (18 de maio de 2014). [«Comparison of frequentist and Bayesian inference»](https://ocw.mit.edu/courses/mathematics/18-05-introduction-to-probability-and-statistics-spring-2014/readings/MIT18_05S14_Reading20.pdf) (PDF). MIT OCW. Consultado em 1 de junho de 2017

[^29]: Castañon, D.; Karl, W. C. (2004). *SC505 Stochastic processes - Class notes*. Boston: \[s.n.\] pp. 27–28

[^30]: [Stone 2013](#CITEREFStone2013), p. 14-15.

[^31]: [Farias & Laurencel 2006](#CITEREFFariasLaurencel2006), p. 41-42.