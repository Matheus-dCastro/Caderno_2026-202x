---
title: "Função de verossimilhança – Wikipédia, a enciclopédia livre"
source: "https://pt.wikipedia.org/wiki/Fun%C3%A7%C3%A3o_de_verossimilhan%C3%A7a"
author:
  - "[[Wikipedia]]"
published: 2014-12-01
created: 2026-06-05
description:
tags:
  - "clippings"
---
![](https://upload.wikimedia.org/wikipedia/commons/thumb/2/20/LikelihoodFunctionAfterHHT.png/500px-LikelihoodFunctionAfterHHT.png)

A função de verossimilhança para estimar a probabilidade de um pouso de uma moeda sem conhecimento prévio de seu lançamento. 1 2

Em [estatística](https://pt.wikipedia.org/wiki/Estat%C3%ADstica "Estatística"), a **função de verossimilhança** ou **função de probabilidade** é uma função dos parâmetros de um modelo estatístico que permite inferir sobre o seu valor a partir de um conjunto de observações.[^3] [^4] Num certo sentido, a probabilidade é uma versão *inversa* da [probabilidade condicionada](https://pt.wikipedia.org/wiki/Probabilidade_condicionada "Probabilidade condicionada").[^5] Conhecendo um parâmetro *B*, a probabilidade condicional de *A* é P(*A* | *B*), mas se o valor de *A* é conhecido, pode-se realizar inferências sobre o valor de *B* graças ao [teorema de Bayes](https://pt.wikipedia.org/wiki/Teorema_de_Bayes "Teorema de Bayes"), segundo o qual:[^6]

${\displaystyle P(B\mid A)={\frac {P(A\mid B)\;P(B)}{P(A)}}.\!}$

Dessa forma, a função de verossimilhança *L* ( b | *A*) é definida como:[^7]

${\displaystyle L(b\mid A)=P(A\mid B=b),\!}$

Se houver um número de amostras aleatórias independentes *x* <sub>1</sub>,..., *x* <sub><i>n</i></sub>, em seguida, o log-probabilidade conjunta será a soma de log-probabilidades individuais, e a derivada desta soma será uma soma de derivadas de cada indivíduo de log-verossimilhança:[^8] [^9] [^10]

${\displaystyle {\frac {\partial \log {\mathcal {L}}(\alpha ,\beta \,|\,x_{1},\ldots ,x_{n})}{\partial \beta }}={\frac {\partial \log {\mathcal {L}}(\alpha ,\beta \,|\,x_{1})}{\partial \beta }}+\cdots +{\frac {\partial \log {\mathcal {L}}(\alpha ,\beta \,|\,x_{n})}{\partial \beta }}={\frac {n\alpha }{\beta }}-\sum _{i=1}^{n}x_{i}.}$

## Referências

[^1]: Pawitan, Yudi (2001). *In All Likelihood: Statistical Modelling and Inference Using Likelihood*. \[S.l.\]: Oxford University Press. [ISBN](https://pt.wikipedia.org/wiki/International_Standard_Book_Number "International Standard Book Number") [0-19-850765-8](https://pt.wikipedia.org/wiki/Especial:Fontes_de_livros/0-19-850765-8 "Especial:Fontes de livros/0-19-850765-8")

[^2]: Wen Hsiang Wei. [«Generalized linear model course notes»](http://web.thu.edu.tw/wenwei/www/glmpdfmargin.htm). Tung Hai University, Taichung, Taiwan. pp. Chapter 5. Consultado em 23 de janeiro de 2007

[^3]: Raue, A; Kreutz, C; Maiwald, T; Bachmann, J; Schilling, M; Klingmüller, U; Timmer, J (2009). [«Structural and practical identifiability analysis of partially observed dynamical models by exploiting the profile likelihood»](https://archive.is/20130113035515/http://bioinformatics.oxfordjournals.org/cgi/content/abstract/btp358?ijkey=iYp4jPP50F5vdX0&keytype=ref). *Bioinformatics*. **25** (15): 1923–9. [PMID](https://pt.wikipedia.org/wiki/PubMed_Identifier "PubMed Identifier") [19505944](https://www.ncbi.nlm.nih.gov/pubmed/19505944). [doi](https://pt.wikipedia.org/wiki/Digital_object_identifier "Digital object identifier"):[10.1093/bioinformatics/btp358](https://dx.doi.org/10.1093%2Fbioinformatics%2Fbtp358). Consultado em 1 de dezembro de 2014. Arquivado do [original](http://bioinformatics.oxfordjournals.org/cgi/content/abstract/btp358?ijkey=iYp4jPP50F5vdX0&keytype=ref) em 13 de janeiro de 2013

[^4]: Vanlier, J; Tiemann, C; Hilbers, P; van Riel, N (2012). [«An integrated strategy for prediction uncertainty analysis»](http://bioinformatics.oxfordjournals.org/content/28/8/1130.long). *Bioinformatics*. **28** (8): 1130–5. [PMID](https://pt.wikipedia.org/wiki/PubMed_Identifier "PubMed Identifier") [22355081](https://www.ncbi.nlm.nih.gov/pubmed/22355081). [doi](https://pt.wikipedia.org/wiki/Digital_object_identifier "Digital object identifier"):[10.1093/bioinformatics/bts088](https://dx.doi.org/10.1093%2Fbioinformatics%2Fbts088)

[^5]: [Stephen M. Stigler](https://pt.wikipedia.org/wiki/Stephen_Stigler?action=edit&redlink=1 "Stephen Stigler (página não existe)"). *The History of Statistics: The Measurement of Uncertainty before 1900*. \[S.l.\]: Harvard University Press. [ISBN](https://pt.wikipedia.org/wiki/International_Standard_Book_Number "International Standard Book Number") [0-674-40340-1](https://pt.wikipedia.org/wiki/Especial:Fontes_de_livros/0-674-40340-1 "Especial:Fontes de livros/0-674-40340-1")

[^6]: [Cox, D. R.](https://pt.wikipedia.org/wiki/David_Cox_\(statistician\)?action=edit&redlink=1 "David Cox (statistician) (página não existe)") (1975). «Partial likelihood». *[Biometrika](https://pt.wikipedia.org/wiki/Biometrika?action=edit&redlink=1 "Biometrika (página não existe)")*. **62** (2): 269–276. [MR](https://pt.wikipedia.org/wiki/Mathematical_Reviews "Mathematical Reviews") [0400509](https://www.ams.org/mathscinet-getitem?mr=0400509). [doi](https://pt.wikipedia.org/wiki/Digital_object_identifier "Digital object identifier"):[10.1093/biomet/62.2.269](https://dx.doi.org/10.1093%2Fbiomet%2F62.2.269)

[^7]: [Fisher, R.A.](https://pt.wikipedia.org/wiki/Ronald_Fisher "Ronald Fisher") (1922). [«On the mathematical foundations of theoretical statistics»](http://digital.library.adelaide.edu.au/dspace/handle/2440/15172). *Philosophical Transactions of the Royal Society A*. **222** (594–604): 309–368. [JFM](https://pt.wikipedia.org/wiki/Jahrbuch_%C3%BCber_die_Fortschritte_der_Mathematik "Jahrbuch über die Fortschritte der Mathematik") [48.1280.02](https://zbmath.org/?format=complete&q=an:48.1280.02). [JSTOR](https://pt.wikipedia.org/wiki/JSTOR "JSTOR") [91208](https://www.jstor.org/stable/91208). [doi](https://pt.wikipedia.org/wiki/Digital_object_identifier "Digital object identifier"):[10.1098/rsta.1922.0009](https://dx.doi.org/10.1098%2Frsta.1922.0009)

[^8]: [Anders Hald](https://pt.wikipedia.org/wiki/Anders_Hald "Anders Hald") (1998). *A History of Mathematical Statistics from 1750 to 1930*. New York: Wiley. [ISBN](https://pt.wikipedia.org/wiki/International_Standard_Book_Number "International Standard Book Number") [0-471-17912-4](https://pt.wikipedia.org/wiki/Especial:Fontes_de_livros/0-471-17912-4 "Especial:Fontes de livros/0-471-17912-4")

[^9]: [Steffen L. Lauritzen](https://pt.wikipedia.org/wiki/Steffen_L._Lauritzen?action=edit&redlink=1 "Steffen L. Lauritzen (página não existe)"), [*Aspects of T. N. Thiele’s Contributions to Statistics*](http://www.stats.ox.ac.uk/~steffen/papers/isi99.ps). *Bulletin of the [International Statistical Institute](https://pt.wikipedia.org/wiki/International_Statistical_Institute?action=edit&redlink=1 "International Statistical Institute (página não existe)")*, 58, 27–30, 1999.

[^10]: [Steffen L. Lauritzen](https://pt.wikipedia.org/wiki/Steffen_L._Lauritzen?action=edit&redlink=1 "Steffen L. Lauritzen (página não existe)") (2002). *Thiele: Pioneer in Statistics*. \[S.l.\]: \[Oxford University Press\]. 288 páginas. [ISBN](https://pt.wikipedia.org/wiki/International_Standard_Book_Number "International Standard Book Number") [978-0-19-850972-1](https://pt.wikipedia.org/wiki/Especial:Fontes_de_livros/978-0-19-850972-1 "Especial:Fontes de livros/978-0-19-850972-1")