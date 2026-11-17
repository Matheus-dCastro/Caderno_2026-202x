# Guia de Estudos Oficial — 2ª Unidade (IMD3001: Introdução à IA)

Este guia foi elaborado a partir de todos os materiais da disciplina (slides de aulas e notebooks de laboratórios práticos) disponíveis no diretório. Seu propósito é direcionar seus estudos para que você responda com total clareza, rigor conceitual e completude a cada uma das 22 questões da avaliação.

---

## 🗺️ Mapa Geral dos Materiais

```
📁 Materiais 2ª Unidade
├── ⚔️ Módulo 1: Busca Competitiva e Jogos (Questões 1 a 8)
│   ├── Aula 08 - Busca Competitiva (PDF)
│   ├── Aula 09 - Busca Competitiva II (PDF)
│   ├── Laboratório - Busca Competitiva I (.ipynb)
│   └── Laboratório - Busca Competitiva II (.ipynb)
│
├── 🧠 Módulo 2: Agentes Lógicos e Inferência (Questões 9 a 11)
│   ├── Aula 10 - Agentes Lógicos (PDF)
│   └── Laboratório - Agentes Lógicos no Wumpus World (.ipynb)
│
├── 🎲 Módulo 3: Incerteza e Raciocínio Probabilístico (Questões 12 a 17)
│   ├── Aula 11 - Incerteza (PDF)
│   ├── Aula 12 - Naive Bayes (PDF)
│   ├── Laboratório - Agentes Probabilísticos no Wumpus World (.ipynb)
│   └── Laboratório - Classificação com Naive Bayes v3 (.ipynb)
│
└── 🕸️ Módulo 4: Redes Bayesianas e Modelos Temporais (Questões 18 a 22)
    ├── Aula 13 - Redes Bayesianas e Modelos de Markov (PDF)
    ├── Laboratório - Redes Bayesianas (.ipynb)
    └── Laboratório - Cadeia de Markov (.ipynb)
```

---

## ⚔️ Bloco 1: Busca Competitiva e Jogos (Questões 1 a 8)

### Questão 1: Minimax e a Estratégia de "Pior Caso"
* **Onde estudar:**
  * [Aula 08 - Busca Competitiva](file:///home/alomy/Downloads/materiais%202°U/IMD3001_Aula_08_-_Busca_Competitiva%20-%20IMD3001_Aula_08_-_Busca_Competitiva.pdf#page=27): Slides 27 a 42 (Decisões ótimas em jogos, formulação recursiva, nós MAX e MIN).
  * [Lab Busca Competitiva I](file:///home/alomy/Downloads/materiais%202°U/Laboratorio_-_Busca_Competitiva_I.ipynb): Seção *Fundamentação Teórica — Minimax*.
* **Conceitos essenciais que você deve dominar:**
  * Mecânica da árvore de jogo: percorrida em profundidade (DFS) até os nós terminais/folhas, onde a função de utilidade é calculada.
  * O papel do jogador **MAX** (maximizar o payoff/utilidade) e do jogador **MIN** (minimizar o ganho de MAX).
  * Propagação de valores: nós MAX assumem o maior valor entre os filhos (`max`), nós MIN assumem o menor (`min`).
  * A hipótese de **adversário racional perfeito / ótimo**.
* **Roteiro para estruturar sua resposta:**
  1. **Funcionamento:** Explique como o algoritmo percorre a árvore até os estados terminais e propaga os valores de volta até a raiz, alternando turnos entre MAX e MIN.
  2. **Por que "pior caso":** Mostre que MAX não joga contando com a sorte ou com um erro do oponente; pelo contrário, assume que MIN sempre escolherá a jogada mais prejudicial a MAX. MAX adota uma postura conservadora, garantindo a melhor recompensa possível no pior cenário imaginável de retaliação adversária.

---

### Questão 2: O Conceito de "Podar" e o Ganho de Eficiência
* **Onde estudar:**
  * [Aula 08 - Busca Competitiva](file:///home/alomy/Downloads/materiais%202°U/IMD3001_Aula_08_-_Busca_Competitiva%20-%20IMD3001_Aula_08_-_Busca_Competitiva.pdf#page=43): Slides 43 a 55 (Princípio da Poda Alpha-Beta).
  * [Aula 09 - Busca Competitiva II](file:///home/alomy/Downloads/materiais%202°U/IMD3001_Aula_09_-_Busca_Competitiva_II%20-%20IMD3001_Aula_09_-_Busca_Competitiva_II.pdf#page=5): Slides 5 a 14.
* **Conceitos essenciais que você deve dominar:**
  * Definição exata de poda: interrupção do cálculo e descarte de subárvores inteiras cujo valor não tem potencial de mudar a decisão na raiz.
  * Preservação da otimalidade matemática (a poda Alpha-Beta retorna a mesmíssima jogada que o Minimax completo retornaria).
* **Roteiro para estruturar sua resposta:**
  1. **Conceito de poda:** Esclareça que "podar" significa deixar de gerar e examinar nós e ramos filhos a partir do momento em que já se sabe que o jogador naquele nível (ou no nível pai) rejeitará aquele ramo.
  2. **Ganho de eficiência:** Explique que o Minimax clássico visita todos os $O(b^d)$ nós. Com a poda, ramos irrelevantes são ignorados precocemente, reduzindo drasticamente o número de chamadas recursivas, economizando tempo de CPU e uso de memória.

---

### Questão 3: Princípio da Poda Alpha-Beta (Limites $\alpha$ e $\beta$)
* **Onde estudar:**
  * [Aula 08 - Busca Competitiva](file:///home/alomy/Downloads/materiais%202°U/IMD3001_Aula_08_-_Busca_Competitiva%20-%20IMD3001_Aula_08_-_Busca_Competitiva.pdf#page=45): Slides 45 a 53 (passo a passo com o vetor $[\alpha, \beta]$).
  * [Aula 09 - Busca Competitiva II](file:///home/alomy/Downloads/materiais%202°U/IMD3001_Aula_09_-_Busca_Competitiva_II%20-%20IMD3001_Aula_09_-_Busca_Competitiva_II.pdf#page=6): Slides 6 a 13.
* **Conceitos essenciais que você deve dominar:**
  * $\alpha$: a melhor escolha (valor máximo garantido) encontrada até o momento para o jogador MAX ao longo do caminho. Começa em $-\infty$.
  * $\beta$: a melhor escolha (valor mínimo garantido) encontrada até o momento para o jogador MIN. Começa em $+\infty$.
  * Condição fundamental de corte: $\alpha \ge \beta$.
* **Roteiro para estruturar sua resposta:**
  1. **Definição formal:** Defina o papel de $\alpha$ (pertence/atualizado por MAX) e de $\beta$ (pertence/atualizado por MIN).
  2. **Poda Alfa (em nó MIN):** Se um nó MIN avalia um filho e encontra um valor $v \le \alpha$, o nó MIN descarta os demais filhos. Motivo: MAX no nível superior já tem uma opção garantida de valor $\alpha$; como MIN escolherá valores menores ou iguais a $v$, MAX nunca escolherá esse ramo.
  3. **Poda Beta (em nó MAX):** Se um nó MAX encontra um valor $v \ge \beta$, MAX descarta os outros filhos, pois MIN no nível superior já tem uma opção com valor $\beta$ e nunca deixará MAX usufruir de algo maior que isso.

---

### Questão 4: Influência do Move Ordering e Profundidade $2\times$ Maior
* **Onde estudar:**
  * [Aula 09 - Busca Competitiva II](file:///home/alomy/Downloads/materiais%202°U/IMD3001_Aula_09_-_Busca_Competitiva_II%20-%20IMD3001_Aula_09_-_Busca_Competitiva_II.pdf#page=14): Slides 14 e 15 (*Move ordering*, *killer moves* e complexidade assintótica).
* **Conceitos essenciais que você deve dominar:**
  * Complexidade no pior caso de ordenação: $O(b^d)$ (nenhum corte eficiente ocorre; idêntico ao Minimax).
  * Complexidade no melhor caso (ordenação perfeita): $O(b^{d/2})$.
* **Roteiro para estruturar sua resposta:**
  1. **Importância da ordem dos movimentos:** Se os melhores lances forem avaliados primeiro, os valores de $\alpha$ sobem rápido e os de $\beta$ descem rápido, ativando a condição de corte ($\alpha \ge \beta$) imediatamente nos ramos seguintes.
  2. **Demonstração do dobro de profundidade:** Mostre algebricamente que $O(b^{d/2}) = O((\sqrt{b})^d)$. Isso significa que o fator de ramificação efetivo cai para $\sqrt{b}$. Com a mesma quantidade de recursos computacionais necessária para o Minimax atingir profundidade $d$, a Poda Alpha-Beta bem ordenada atinge $2d$. Cite técnicas como *killer moves* e ordenação por capturas/heurísticas.

---

### Questão 5: Limitações do Minimax/Alpha-Beta e a Motivação do MCTS (ex: Go)
* **Onde estudar:**
  * [Aula 09 - Busca Competitiva II](file:///home/alomy/Downloads/materiais%202°U/IMD3001_Aula_09_-_Busca_Competitiva_II%20-%20IMD3001_Aula_09_-_Busca_Competitiva_II.pdf#page=18): Slides 18 a 21.
  * [Lab Busca Competitiva II](file:///home/alomy/Downloads/materiais%202°U/Laboratorio_-_Busca_Competitiva_II.ipynb): Seção *Minimax vs. MCTS*.
* **Conceitos essenciais que você deve dominar:**
  * Fator de ramificação colossal do Go: $b \approx 250 \sim 360$ (contra $b \approx 35$ no xadrez).
  * Ausência de uma função de avaliação heurística estática (EVAL) precisa e viável: no Go, avaliar visualmente quem está ganhando no meio do jogo é extremamente sutil e complexo.
* **Roteiro para estruturar sua resposta:**
  1. **Gargalo combinatório:** Mostre que o espaço de busca do Go torna a busca em profundidade exaustiva inviável mesmo para poucos lances.
  2. **Gargalo heurístico:** Explique que o Alpha-Beta depende de cortar a busca e chamar uma função estática de avaliação; em domínios onde essa função não pode ser modelada manualmente com sucesso, o algoritmo falha.
  3. **Solução do MCTS:** Introduza como o MCTS resolve isso substituindo heurísticas estáticas por simulações estatísticas completas até o fim da partida (método de Monte Carlo).

---

### Questão 6: Os Quatro Estágios do MCTS
* **Onde estudar:**
  * [Aula 09 - Busca Competitiva II](file:///home/alomy/Downloads/materiais%202°U/IMD3001_Aula_09_-_Busca_Competitiva_II%20-%20IMD3001_Aula_09_-_Busca_Competitiva_II.pdf#page=22): Slides 22 a 31 (diagramas de seleção, expansão, simulação e retropropagação).
  * [Lab Busca Competitiva II](file:///home/alomy/Downloads/materiais%202°U/Laboratorio_-_Busca_Competitiva_II.ipynb): Seção *A intuição por trás do MCTS*.
* **Conceitos essenciais que você deve dominar:**
  * Os 4 estágios executados em loop iterativo:
    1. **Seleção (Selection):** Percorre a árvore existente desde a raiz usando uma política de equilíbrio (UCT) até encontrar um nó folha/não expandido.
    2. **Expansão (Expansion):** Adiciona um ou mais nós filhos à árvore representando jogadas ainda não visitadas.
    3. **Simulação (Simulation / Playout / Rollout):** Realiza uma partida rápida a partir do nó novo até o fim do jogo com jogadas aleatórias ou heurísticas leves, descobrindo o vencedor.
    4. **Retropropagação (Backpropagation):** Atualiza as estatísticas ($N$ visitas e $Q$ vitórias) de todos os nós ancestrais do caminho até a raiz.
* **Roteiro para estruturar sua resposta:**
  * Explique cada um dos 4 estágios em sequência lógica e ressalte que esse ciclo faz a árvore expandir assimetricamente, aprofundando-se com mais força onde as chances de vitória são estatisticamente maiores.

---

### Questão 7: Exploração vs. Explotação e o Critério UCT/UCB1
* **Onde estudar:**
  * [Aula 09 - Busca Competitiva II](file:///home/alomy/Downloads/materiais%202°U/IMD3001_Aula_09_-_Busca_Competitiva_II%20-%20IMD3001_Aula_09_-_Busca_Competitiva_II.pdf#page=24): Slides 24 a 26.
  * [Lab Busca Competitiva II](file:///home/alomy/Downloads/materiais%202°U/Laboratorio_-_Busca_Competitiva_II.ipynb): Seção *A fórmula do UCB1*.
* **Conceitos essenciais que você deve dominar:**
  * O dilema: gastar tempo aprofundando movimentos já conhecidamente promissores (*exploitation*) versus experimentar movimentos pouco testados que podem se revelar ainda melhores (*exploration*).
  * A fórmula UCT/UCB1:
    $$UCT(i) = \frac{w_i}{n_i} + c \sqrt{\frac{\ln N}{n_i}}$$
    * $w_i$: número de vitórias do nó filho $i$.
    * $n_i$: número de vezes que o nó $i$ foi visitado.
    * $N$: número total de visitas ao nó pai.
    * $c$: constante de exploração (teoricamente $\sqrt{2}$).
* **Roteiro para estruturar sua resposta:**
  1. **Definição da dualidade:** Explique o risco de explorar demais (perder tempo com lances ruins) ou explorar de menos (ficar preso em ótimos locais e ignorar lances brilhantes).
  2. **Interpretação da fórmula:** Decomponha os dois termos: o primeiro termo (taxa média de vitória) favorece a explotação; o segundo termo (inversamente proporcional a $\sqrt{n_i}$) favorece nós raramente visitados (exploração). Conforme $N$ cresce e $n_i$ permanece estagnado, o segundo termo infla e força o algoritmo a testar a opção negligenciada.

---

### Questão 8: Robustez do MCTS vs. Heurísticas Fixas
* **Onde estudar:**
  * [Aula 09 - Busca Competitiva II](file:///home/alomy/Downloads/materiais%202°U/IMD3001_Aula_09_-_Busca_Competitiva_II%20-%20IMD3001_Aula_09_-_Busca_Competitiva_II.pdf#page=21): Slides 21, 30 e 34.
  * [Lab Busca Competitiva II](file:///home/alomy/Downloads/materiais%202°U/Laboratorio_-_Busca_Competitiva_II.ipynb).
* **Conceitos essenciais que você deve dominar:**
  * Fragilidade da heurística fixa: se o programador codificar pesos errados na função estática ou sofrer com o efeito horizonte, o Minimax propagará esse viés sistematicamente.
  * Natureza assintótica do Monte Carlo: fundamentado na Lei dos Grandes Números.
* **Roteiro para estruturar sua resposta:**
  1. Aponte que funções heurísticas manuais dependem de conhecimento especializado e contêm vieses humanos ou pontos cegos.
  2. Explique que o MCTS estima valores através de resultados reais de simulação até os nós terminais. À medida que o número de iterações aumenta, os erros aleatórios se cancelam e as estimativas convergem para as probabilidades reais de vitória, sem depender de uma avaliação intermediária artificial.

---

## 🧠 Bloco 2: Agentes Lógicos e Inferência (Questões 9 a 11)

### Questão 9: Agente Lógico vs. Agente Baseado em Busca
* **Onde estudar:**
  * [Aula 10 - Agentes Lógicos](file:///home/alomy/Downloads/materiais%202°U/IMD3001_Aula_10_-_Agentes_Logicos%20-%20IMD3001_Aula_10_-_Agentes_Logicos.pdf#page=3): Slides 3 a 11 (Representação atômica vs. estruturada/declarativa, `TELL` e `ASK`).
  * [Lab Agentes Lógicos Wumpus](file:///home/alomy/Downloads/materiais%202°U/Laboratorio_Agentes_Logicos_Wumpus.ipynb): Introdução e formulação da Base de Conhecimento (KB).
* **Conceitos essenciais que você deve dominar:**
  * **Agente baseado em busca:** Representação **atômica** (o estado é uma caixa-preta indivisível; ex: coordenadas no mapa); decide suas ações procurando um caminho explícito de transições até um estado-meta.
  * **Agente lógico:** Representação **declarativa/estruturada**; mantém uma Base de Conhecimento (KB) com sentenças formais e decide deduzindo novas informações a partir de fatos e regras de inferência.
* **Roteiro para estruturar sua resposta:**
  1. Contraste a representação do estado e a tomada de decisão de ambos os modelos.
  2. Destaque em que tipo de problema a lógica se destaca: ambientes com **observabilidade parcial** e informação implícita (como o Mundo do Wumpus), onde o agente não enxerga os perigos diretamente (poços e monstros), mas precisa inferir suas localizações de forma conclusiva cruzando regras físicas com percepções locais de brisa ou fedor.

---

### Questão 10: Lógica Proposicional como Ponto de Partida na IA
* **Onde estudar:**
  * [Aula 10 - Agentes Lógicos](file:///home/alomy/Downloads/materiais%202°U/IMD3001_Aula_10_-_Agentes_Logicos%20-%20IMD3001_Aula_10_-_Agentes_Logicos.pdf#page=12): Slides 12 a 25 (Sintaxe, operadores, semântica, tabelas-verdade e acarretamento $/ \models$).
  * [Lab Agentes Lógicos Wumpus](file:///home/alomy/Downloads/materiais%202°U/Laboratorio_Agentes_Logicos_Wumpus.ipynb).
* **Conceitos essenciais que você deve dominar:**
  * Sintaxe precisa e sem ambiguidade (símbolos e operadores booleanos $\neg, \wedge, \vee, \Rightarrow, \Leftrightarrow$).
  * Semântica composicional (o valor de verdade de uma fórmula composta depende puramente dos valores de suas subfórmulas).
  * Acarretamento lógico (*entailment* $\alpha \models \beta$): em todo modelo onde $\alpha$ é verdadeiro, $\beta$ também é obrigatoriamente verdadeiro.
* **Roteiro para estruturar sua resposta:**
  1. Explique por que é o ponto de partida: fornece uma representação matemática formal e desprovida das ambiguidades da linguagem natural.
  2. Demonstre como viabiliza a inferência válida: por meio da semântica de modelos e regras de dedução formais, um computador pode verificar se uma conclusão é necessariamente verdadeira em todos os mundos possíveis sem depender de intuição ou suposição subjetiva.

---

### Questão 11: CNF, Regra de Resolução e Prova por Refutação
* **Onde estudar:**
  * [Aula 10 - Agentes Lógicos](file:///home/alomy/Downloads/materiais%202°U/IMD3001_Aula_10_-_Agentes_Logicos%20-%20IMD3001_Aula_10_-_Agentes_Logicos.pdf#page=46): Slides 46 a 50 (CNF, resolução proposicional, contradição e insatisfatibilidade).
  * [Lab Agentes Lógicos Wumpus](file:///home/alomy/Downloads/materiais%202°U/Laboratorio_Agentes_Logicos_Wumpus.ipynb): Seção de *Resolução e Dedução*.
* **Conceitos essenciais que você deve dominar:**
  * **Forma Normal Conjuntiva (CNF):** Sentenças lógicas padronizadas como uma conjunção ($\wedge$) de cláusulas, onde cada cláusula é uma disjunção ($\vee$) de literais (ex: $(A \vee B) \wedge (\neg B \vee C)$).
  * **Regra de Resolução:** Regra de inferência sintática que resolve cláusulas contendo literais complementares: $(A \vee B)$ e $(\neg B \vee C) \vdash (A \vee C)$.
  * **Prova por Refutação (Reductio ad Absurdum):** Para provar que $KB \models \alpha$, adiciona-se $\neg \alpha$ à $KB$ e demonstra-se que $(KB \wedge \neg \alpha)$ é insatisfatível (deriva a cláusula vazia $\square$).
* **Roteiro para estruturar sua resposta:**
  * Conecte os 3 elementos em um fluxo encadeado:
    1. A Resolução é um algoritmo puramente sintático e mecânico, mas exige que as fórmulas estejam no formato uniforme de **CNF**.
    2. A Regra de Resolução opera sobre as cláusulas em CNF cancelando literais opostos.
    3. Conclua explicando como a Prova por Refutação aplica esse mecanismo: se assumir que $\alpha$ é falso levar à derivação de uma contradição lógica irremediável ($\square$), prova-se com certeza matemática que $\alpha$ decorre necessariamente de $KB$.

---

## 🎲 Bloco 3: Incerteza e Raciocínio Probabilístico (Questões 12 a 17)

### Questão 12: O Problema da Qualificação Lógica e a Teoria da Probabilidade
* **Onde estudar:**
  * [Aula 11 - Incerteza](file:///home/alomy/Downloads/materiais%202°U/IMD3001_Aula_11_-_Incerteza%20-%20IMD3001_Aula_11_-_Incerteza.pdf#page=3): Slides 3 a 14.
  * [Aula 12 - Naive Bayes](file:///home/alomy/Downloads/materiais%202°U/Aula%2012%20-%20Naive%20Bayes.pdf#page=2): Slide 2.
* **Conceitos essenciais que você deve dominar:**
  * **Problema da Qualificação:** A impossibilidade prática de enumerar todas as pré-condições e exceções imagináveis para que uma regra lógica estrita seja 100% verdadeira no mundo real (ex: "Se virar a chave, o carro liga" requer qualificar bateria carregada, cabos intactos, combustível não adulterado, ausência de curto-circuito, etc.).
  * Preguiça e ignorância teórica do agente.
* **Roteiro para estruturar sua resposta:**
  1. **Definição:** Apresente o Problema da Qualificação e mostre que a lógica clássica falha porque exige certezas absolutas em regras com infinitas exceções.
  2. **Como a probabilidade resolve:** Explique que a Teoria da Probabilidade resume todas as contingências desconhecidas ou raras em um **grau numérico de crença** (ex: "o carro liga com probabilidade 0,98"). Isso permite que o agente aja racionalmente mesmo com conhecimento imperfeito e incompleto.

---

### Questão 13: Probabilidades Incondicionais vs. Condicionais e Atualização de Crenças
* **Onde estudar:**
  * [Aula 11 - Incerteza](file:///home/alomy/Downloads/materiais%202°U/IMD3001_Aula_11_-_Incerteza%20-%20IMD3001_Aula_11_-_Incerteza.pdf#page=23): Slides 23 a 27.
  * [Lab Wumpus Probabilístico](file:///home/alomy/Downloads/materiais%202°U/Laboratorio_Agentes_Probabilisticos_Wumpus.ipynb): Seção 2 (*Probabilidade condicional e atualização*).
* **Conceitos essenciais que você deve dominar:**
  * **Probabilidade Incondicional (A Priori):** $P(A)$ — crença antes da chegada de novas observações empíricas.
  * **Probabilidade Condicional (A Posteriori):** $P(A \mid B)$ — crença recalculada na presença da evidência $B$.
* **Roteiro para estruturar sua resposta:**
  1. Defina conceitualmente cada uma das probabilidades.
  2. Apresente um exemplo prático: no Mundo do Wumpus, a probabilidade a priori de haver um poço na sala [1,2] é de 20% ($P(P_{1,2}) = 0{,}20$). Porém, se o agente se move para a sala [1,1] e percebe uma brisa ($B_{1,1}$), a probabilidade a posteriori $P(P_{1,2} \mid B_{1,1})$ sobe consideravelmente, atualizando a crença do agente.

---

### Questão 14: A Regra do Produto e a Relação Causa-Efeito
* **Onde estudar:**
  * [Aula 11 - Incerteza](file:///home/alomy/Downloads/materiais%202°U/IMD3001_Aula_11_-_Incerteza%20-%20IMD3001_Aula_11_-_Incerteza.pdf#page=28): Slides 28 a 39.
  * [Aula 12 - Naive Bayes](file:///home/alomy/Downloads/materiais%202°U/Aula%2012%20-%20Naive%20Bayes.pdf#page=6): Slides 6 a 9.
* **Conceitos essenciais que você deve dominar:**
  * Fórmula da Regra do Produto:
    $$P(A \wedge B) = P(A \mid B) \cdot P(B) = P(B \mid A) \cdot P(A)$$
  * Relação causal vs. raciocínio conjunto.
* **Roteiro para estruturar sua resposta:**
  1. **Significado:** Explique que a probabilidade de dois eventos acontecerem conjuntamente é a probabilidade de um deles ocorrer vezes a probabilidade do outro ocorrer sabendo que o primeiro ocorreu.
  2. **Fundamento causa-efeito:** O conhecimento de domínio que possuímos geralmente flui na direção causal física ($P(\text{Efeito} \mid \text{Causa})$). A regra do produto permite decompor eventos complexos e fornece a igualdade algébrica essencial que gera o Teorema de Bayes, permitindo que a IA faça o caminho inverso (diagnóstico).

---

### Questão 15: Os Quatro Termos do Teorema de Bayes
* **Onde estudar:**
  * [Aula 12 - Naive Bayes](file:///home/alomy/Downloads/materiais%202°U/Aula%2012%20-%20Naive%20Bayes.pdf#page=10): Slides 10 a 12 (*Os quatro termos da Regra de Bayes* e *Causal vs. Diagnóstico*).
  * [Aula 11 - Incerteza](file:///home/alomy/Downloads/materiais%202°U/IMD3001_Aula_11_-_Incerteza%20-%20IMD3001_Aula_11_-_Incerteza.pdf#page=40): Slides 40 a 45.
* **Conceitos essenciais que você deve dominar:**
  * A fórmula fundamental:
    $$P(\text{Causa} \mid \text{Evidência}) = \frac{P(\text{Evidência} \mid \text{Causa}) \cdot P(\text{Causa})}{P(\text{Evidência})}$$
* **Roteiro para estruturar sua resposta:**
  * Descreva detalhadamente o significado de cada um dos quatro termos:
    1. **A Posteriori ($P(\text{Causa} \mid \text{Evidência})$):** A crença atualizada sobre a causa após observar a evidência empírica (o diagnóstico desejado).
    2. **Verossimilhança / Likelihood ($P(\text{Evidência} \mid \text{Causa})$):** Quão compatível é a evidência com a causa (direção causal estável dada pela física/biologia).
    3. **A Priori / Prior ($P(\text{Causa})$):** A probabilidade de ocorrência intrínseca da causa antes de qualquer exame ou observação.
    4. **Evidência / Marginal ($P(\text{Evidência})$):** A probabilidade global de observar o sintoma, atuando como constante normalizadora.

---

### Questão 16: O Impacto da Probabilidade A Priori (O Exemplo da Meningite)
* **Onde estudar:**
  * [Aula 11 - Incerteza](file:///home/alomy/Downloads/materiais%202°U/IMD3001_Aula_11_-_Incerteza%20-%20IMD3001_Aula_11_-_Incerteza.pdf#page=43): Slides 43 e 44.
  * [Aula 12 - Naive Bayes](file:///home/alomy/Downloads/materiais%202°U/Aula%2012%20-%20Naive%20Bayes.pdf#page=14): Slides 14 a 26 e Slide 32.
* **Conceitos essenciais que você deve dominar:**
  * Parâmetros do problema clássico:
    * Prevalência a priori: $P(m) = \frac{1}{50.000} = 0{,}00002$.
    * Verossimilhança (sintoma causal): $P(r \mid m) = 0{,}70$ (70% dos infectados têm torcicolo/pescoço rígido).
    * Evidência na população: $P(r) = 0{,}01$ (1% das pessoas têm torcicolo).
  * Equação resolvida:
    $$P(m \mid r) = \frac{P(r \mid m) \cdot P(m)}{P(r)} = \frac{0{,}70 \times 0{,}00002}{0{,}01} = 0{,}0014 = 0{,}14\%$$
* **Roteiro para estruturar sua resposta:**
  1. Mostre os cálculos numéricos exatos.
  2. Explique a intuição do resultado: embora a verossimilhança seja alta (70%), a meningite é tão rara que o número absoluto de pessoas com torcicolo causado por tensão muscular supera em centenas de vezes o número de casos causados por meningite. A probabilidade *a priori* exerce um peso regulador fundamental que impede falsos diagnósticos.

---

### Questão 17: O Classificador Naive Bayes e a Hipótese de Independência
* **Onde estudar:**
  * [Aula 12 - Naive Bayes](file:///home/alomy/Downloads/materiais%202°U/Aula%2012%20-%20Naive%20Bayes.pdf#page=5): Slides 5, 33 a 43 e 58.
  * [Lab Naive Bayes v3](file:///home/alomy/Downloads/materiais%202°U/Laboratorio_-_Naive_Bayes_v3.ipynb).
* **Conceitos essenciais que você deve dominar:**
  * Premissa "ingênua": os atributos $X_1, \dots, X_n$ são **mutuamente independentes condicionais à classe $Y$**:
    $$P(X_1, \dots, X_n \mid Y) = \prod_{i=1}^n P(X_i \mid Y)$$
* **Roteiro para estruturar sua resposta:**
  1. **Por que é ingênuo:** Porque no mundo real os atributos raramente são descorrelacionados, mas o algoritmo trata a ocorrência de cada feature como um evento isolado.
  2. **Onde funciona muito bem:** Em tarefas de classificação de texto (como filtros de spam) ou diagnóstico médico com muitas variáveis esparsas, onde o objetivo principal é ordenar e ranquear a classe mais plausível, mesmo que o valor de probabilidade final seja superconfiante.
  3. **Onde é irrealista:** Quando a ordem e a combinação das palavras alteram totalmente o significado. Use o exemplo dos slides com a resenha "não recomendo": as palavras "não" e "recomendo" dependem intimamente uma da outra; se analisadas de forma independente, a palavra "recomendo" induz o classificador a prever erroneamente um sentimento positivo.

---

## 🕸️ Bloco 4: Redes Bayesianas e Modelos Temporais (Questões 18 a 22)

### Questão 18: Redes Bayesianas, DAG, CPTs e Comparação de Parâmetros (O Alarme)
* **Onde estudar:**
  * [Aula 13 - Redes Bayesianas e Markov](file:///home/alomy/Downloads/materiais%202°U/Aula%2013%20-%20Redes%20Bayesianas%20e%20Modelos%20de%20Markov.pdf#page=12): Slides 12 e 18 a 20.
  * [Lab Redes Bayesianas](file:///home/alomy/Downloads/materiais%202°U/Laboratorio_-_Redes_Bayesianas.ipynb): Seção *Redes Bayesianas — CPTs*.
* **Conceitos essenciais que você deve dominar:**
  * **DAG:** Grafo direcionado acíclico onde nós são variáveis e setas indicam influência direta.
  * **CPT:** Tabela local que quantifica $P(X_i \mid \text{Pais}(X_i))$ para cada nó.
  * Comparativo no domínio do Alarme de Pearl (5 variáveis booleanas: Roubo $R$, Terremoto $T$, Alarme $A$, JoãoLiga $J$, MariaLiga $M$):
    * **Distribuição Conjunta Completa:** $2^5 - 1 = 31$ probabilidades independentes.
    * **Rede Bayesiana:**
      * $R$ (0 pais): 1 parâmetro
      * $T$ (0 pais): 1 parâmetro
      * $A$ (pais $R, T$): $2^2 = 4$ parâmetros
      * $J$ (pai $A$): $2^1 = 2$ parâmetros
      * $M$ (pai $A$): $2^1 = 2$ parâmetros
      * **Total:** $1 + 1 + 4 + 2 + 2 = 10$ parâmetros!
* **Roteiro para estruturar sua resposta:**
  1. Explique a função do DAG e das CPTs na representação formal de dependências.
  2. Apresente os cálculos comparativos do Alarme (31 vs. 10).
  3. Explique por que a representação é compacta: ela explora o fato de que a maioria das variáveis só é influenciada diretamente por um pequeno número de causas locais, evitando a necessidade de especificar todas as combinações globais.

---

### Questão 19: Regra da Fatoração e a Ordem de Construção da Rede
* **Onde estudar:**
  * [Aula 13 - Redes Bayesianas e Markov](file:///home/alomy/Downloads/materiais%202°U/Aula%2013%20-%20Redes%20Bayesianas%20e%20Modelos%20de%20Markov.pdf#page=21): Slides 21 a 26.
* **Conceitos essenciais que você deve dominar:**
  * Regra da Cadeia Geral:
    $$P(X_1, \dots, X_n) = \prod_{i=1}^n P(X_i \mid X_{i-1}, \dots, X_1)$$
  * Regra da Fatoração da Rede Bayesiana:
    $$P(X_1, \dots, X_n) = \prod_{i=1}^n P(X_i \mid \text{Pais}(X_i))$$
  * Topologia e ordenação: ordem causal natural vs. ordem diagnóstica inversa.
* **Roteiro para estruturar sua resposta:**
  1. Mostre como a fatoração simplifica a regra da cadeia aproveitando a propriedade de que cada nó é condicionalmente independente dos seus não-descendentes dados seus pais imediatos.
  2. Explique o efeito da ordem de inserção das variáveis: quando construímos a rede no sentido **causal** (Causas $\rightarrow$ Efeitos), a rede fica esparsa (poucas setas e CPTs pequenas). Se inserirmos os efeitos antes das causas (ordem **diagnóstica**), somos forçados a criar arestas artificiais entre efeitos para representar dependências implícitas, tornando o grafo quase completo, aumentando o número de parâmetros e inviabilizando a inferência rápida.

---

### Questão 20: Inferência em Redes Bayesianas (Variáveis, Causa vs. Efeito e Crença)
* **Onde estudar:**
  * [Aula 13 - Redes Bayesianas e Markov](file:///home/alomy/Downloads/materiais%202°U/Aula%2013%20-%20Redes%20Bayesianas%20e%20Modelos%20de%20Markov.pdf#page=30): Slides 30 a 35.
  * [Lab Redes Bayesianas](file:///home/alomy/Downloads/materiais%202°U/Laboratorio_-_Redes_Bayesianas.ipynb).
* **Conceitos essenciais que você deve dominar:**
  * Classificação das variáveis no cálculo de inferência:
    * **Consulta ($X$):** variável que se quer saber.
    * **Evidência ($E$):** variáveis cujos valores foram observados no mundo.
    * **Ocultas / Latentes ($Y$):** variáveis do sistema que não são observadas nem consultadas (devem ser somadas/marginalizadas).
  * Inferência causal (direta nas CPTs) vs. diagnóstica (requer inversão bayesiana).
* **Roteiro para estruturar sua resposta:**
  1. Defina os três tipos de variáveis e explique a operação de marginalização sobre as variáveis ocultas.
  2. Explique a assimetria: calcular $P(\text{Efeito} \mid \text{Causa})$ é preditivo e vem diretamente das CPTs; calcular $P(\text{Causa} \mid \text{Efeito})$ é diagnóstico e exige somar sobre todos os caminhos alternativos que poderiam ter produzido aquele efeito.
  3. Dê o exemplo numérico do Alarme: $P(r) = 0{,}001$ ($0{,}1\%$). Ao observar que o alarme tocou ($a$), a probabilidade sobe para $P(r \mid a) \approx 37\%$. A evidência multiplicou a crença em centenas de vezes, mas o roubo **ainda não é a explicação mais provável** (em cerca de $63\%$ das vezes o alarme tocou por falha ou pequeno abalo sísmico).

---

### Questão 21: A Hipótese de Markov e Processos Temporais
* **Onde estudar:**
  * [Aula 13 - Redes Bayesianas e Markov](file:///home/alomy/Downloads/materiais%202°U/Aula%2013%20-%20Redes%20Bayesianas%20e%20Modelos%20de%20Markov.pdf#page=50): Slides 50 a 58.
  * [Lab Cadeia de Markov](file:///home/alomy/Downloads/materiais%202°U/Laboratorio_-_Cadeia_de_Markov.ipynb).
* **Conceitos essenciais que você deve dominar:**
  * Enunciado formal da **Hipótese de Markov de 1ª ordem:**
    $$P(S_t \mid S_{t-1}, S_{t-2}, \dots, S_0) = P(S_t \mid S_{t-1})$$
    *(O estado futuro depende exclusivamente do estado presente, sendo condicionalmente independente de todo o passado).*
* **Roteiro para estruturar sua resposta:**
  1. Enuncie formalmente a hipótese e explique a simplificação: em vez de a CPT do tempo $t$ depender de todos os passos anteriores $t-1, \dots, 0$, ela possui apenas um pai ($t-1$), mantendo a matriz de transição constante e compacta.
  2. Explique por que é escolha de modelagem e não do mundo: sistemas reais carregam memória física e inércia de longo prazo. Nós assumimos a hipótese para tornar a computação viável.
  3. Dê um exemplo de inadequação: prever a meteorologia de amanhã considerando unicamente se choveu hoje, ignorando o avanço de uma massa de ar frio que vem se deslocando há vários dias.
  4. Indique ajustes: transformar em uma cadeia de **ordem superior** ($P(S_t \mid S_{t-1}, S_{t-2})$) ou incorporar as variáveis históricas dentro do próprio vetor de estado atual (ex: incluir tendência barométrica e umidade no estado de hoje).

---

### Questão 22: Cadeia de Markov vs. HMM (Hidden Markov Model) e o Guarda-Chuva
* **Onde estudar:**
  * [Aula 13 - Redes Bayesianas e Markov](file:///home/alomy/Downloads/materiais%202°U/Aula%2013%20-%20Redes%20Bayesianas%20e%20Modelos%20de%20Markov.pdf#page=60): Slides 60 a 64 (*Os componentes de um HMM*, *Filtragem: prever, atualizar e normalizar*, e o *Problema do guarda-chuva*).
  * [Lab Cadeia de Markov](file:///home/alomy/Downloads/materiais%202°U/Laboratorio_-_Cadeia_de_Markov.ipynb).
* **Conceitos essenciais que você deve dominar:**
  * Diferença estrutural:
    * **Cadeia de Markov:** os estados do sistema são abertos e observáveis diretamente.
    * **HMM:** o verdadeiro estado do processo ($S_t$) é **oculto/latente**; o agente só percebe sinais ou evidências ($E_t$) gerados por esse estado.
  * Os 4 componentes do HMM:
    1. Conjunto de Estados Ocultos ($S$).
    2. Distribuição Inicial ($P(S_0)$).
    3. Matriz de Transição ($P(S_t \mid S_{t-1})$).
    4. Matriz de Emissão / Modelo de Sensor ($P(E_t \mid S_t)$).
  * O ciclo de **Filtragem** ($P(S_t \mid e_{1:t})$):
    1. **Prever:** propaga a crença anterior via matriz de transição.
    2. **Atualizar:** multiplica pela probabilidade da evidência de hoje via matriz de emissão.
    3. **Normalizar:** divide pela soma para recalibrar as probabilidades para 1.
* **Roteiro para estruturar sua resposta:**
  1. Estabeleça a comparação estrutural e enumere os 4 componentes essenciais.
  2. Descreva o algoritmo de filtragem em suas 3 etapas lógicas.
  3. Explique o caso do guarda-chuva: o guarda-chuva é um sensor ruidoso e imperfeito. Existe uma chance de alguém portar guarda-chuva mesmo sem chuva ($P(\text{guarda-chuva} \mid \text{sem chuva}) = 0{,}20$). Além disso, a dinâmica climática de transição influencia a previsão. Portanto, ver o diretor entrar com o guarda-chuva faz a crença de chuva subir de 50% para 81,8% no primeiro dia, mas **nunca confere 100% de certeza**.

---
*Bons estudos! Utilize este roteiro em conjunto com os slides e notebooks para redigir respostas ricas, precisas e bem fundamentadas.*
