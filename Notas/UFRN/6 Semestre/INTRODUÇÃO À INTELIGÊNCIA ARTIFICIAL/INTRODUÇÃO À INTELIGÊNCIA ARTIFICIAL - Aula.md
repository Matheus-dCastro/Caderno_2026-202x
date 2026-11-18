# Aula 03 - Agentes:

Ambiente >- sensor -< action -> ambiente

Quando um comportamento n te um clasuara de parada => Clasura erradica (**Irracional**)
*<font color="#ffc000">Medida de desempenho</font>*

### Principios da Racionalidade em IA:

- media de desempenho que define o criterio de sucesso
- o conhecimento previo que o agente tem do ambiente
- as ações q o agente pode executar
- a sequência de percepções do agente ate o instante atual

Mapiar o ambiente e seus limites
-> regras n gatante q crie racionalidade;

#### Racionalidade != Onisciência

maximizar o desempenho não garante soluções otimas(oni)

### Modelagem de agentes racionais

parece com levantamento de requisitos de engenharia de software;
<mark style="background:#affad1">Medida de desempenho (P), Ambiente (E), Atuadores (A), Sensores (S)</mark>

#### Tipos de ambiente:
- Totalmente observavel vs parcialmente
- Agente unico vs multiagente
- deterministico vs estocastico
- episodico vs senquêncial

### Estrutura do Agente:

agente = arquitetura + programa (modelo)


# Aula 04 -

### T#eoria dos grafos:
tarefas de busca espacionalmente definida

-> Representação do ambiente: espaço de estados, agentes baseados em objetos

cidade = vertices
estradas = arestas

#### Estrura de Agente:

#### Arvores de Busca:

**Tipos de busca:** largura, profundidade, 

# Aula 05 Resolução de problemas com metodos de buscas:

o algotmo da estrela pode ser interpretado como uma versão com um plus do da busca gulosa
um no ja fechado pode ser reusado a depender do estado atual
<mark style="background:#9254de">euristica dimisivel </mark>

# Aula 07: Busca em Ambientes Complexos parte 02:

Não possue o ambiente mapeado -> n tem conhecimento sobre todos os dados ja q parte dele é inserido em tempo real por ex
*nem sempre excolher de forma imediatista* 
-> dar pesos para aumentar a probalidade q estão se saindo melhor no momento porem ainda é feita uma escolha aleatoria

*algoritmos evolutivos e geneticos* 
-> segue a mesma ideia da genetica tentando pegar os melhores projenitores de cada rodada dos algoritmos.


# Aula 08: Laboratorio pratico

# Estudo dirigido e Revisão para prova:

-> campo da ciência do desing de agentes
=> **Fromas reflexo de um *Agente*** 
		- Reflexo **Simples**
		- Reflexo **baseado em modelo**
		- Reflexo **Objeto**
		- Reflexo **Utilidade**

podemos ter algumas abordagens:
*Não informada:* explora sem ter conhecimento previo
*Informada:* Utiliza conhecimento previo (heuristica)
*Local e de otimização:* funciona como um algoritomo de busca em profundidade ou em largura
*Adversarial:* seta o objetivo no player e faz o npc se mexer atraz do player

Filosofia: Conceitos como a mente como máquina, conhecimento e ação. 

Matemática: Lógica formal, teoria da probabilidade, algoritmos, computabilidade e intratabilidade (problemas NP-completos). 

Economia: Teoria da decisão, teoria da utilidade, teoria dos jogos, otimização de operações e o conceito de satisficing (encontrar soluções "boas o suficiente"). 

Neurociência: Entendimento do cérebro, neurônios e processamento de informações. 

Psicologia: Estudo do pensamento e comportamento humanos, cognição e processamento de informações. 

Engenharia da Computação: Desenvolvimento de hardware (computadores digitais, paralelismo massivo) e software (sistemas operacionais, linguagens de programação) que tornam a IA possível 

Teoria de Controle e Cibernética: Foco em sistemas auto-reguláveis e otimização de funções de custo


#### Tipos de agentes:

**Completamente** tem todas as infos acessiveis
**Parcialmente** tem partes das infos n acessiveis
**Discreto** o estado e as ações são finitas
**Contínuo** o estado e as ações são infinitas (só aumentam com o passar do tempo)
**Episodico** suas ações n dependem do estado anterior
**Sequencial** as ações influênciam tanto o ambiente quando as proximas escolhas
**Estatico** o ambiente n muda com o tempo 
**Dinamico** o ambiente muda com o tempo

![[INTRODUÇÃO À INTELIGÊNCIA ARTIFICIAL - Aula-1790106483587.webp]]

**Agente baseado em tabela** ele monta uma tabela com todas as ações possivesi para todas as sequências perceptivesi possivel.

**Agente reativo simples** 


# Busca Adversarial e MCTS

# Aula 10:

mundo wumpus: => agente de busca, agnete baseado emconhecimento analisar um ambiente pre definido ou estocastico (muda) casos de games para fazer a ia trabalhar em um ambiente

o cicio tell -> adk -> tell

# Aula do dia 19/10
#### Agentes logicos wumpus *laboratorio*:

-- implementação de como saber se esta safe ou n aquela casa e como ele interagi com o mundo
-- Agente logicos sao conservadores, mas seguros para manter em mundos estocasticos

# Aula do dia 21/10:

algoritmo baseados em temora "bayes" quase dado o conhecido qual a chance daquele conjunto eu obeter x


# Aula do dia 26/10:
### Laboratorio_Agentes_Probabilisticos_Wumpus:
usando o teomrema de bayes fazemo o "radar" das probabilidades de movimentação do agente levando em conta a diposição do tabuleiro e o quanto é corajoso para dar um salto de fé. 

quanto mais baixa a recompesa vai ser mais conservador quanto maior ele vai ser arriscar mais


# Aula do dia 28/10:

a priori 1 em 50.000
causa 70%
evidencia 1% tem por causa da minigite

$\frac{0.7 * \frac{1}{50.000}}{0.01}$ => 0.0014



# Aula do dia 16/11:

Cadeia de markov
ambientes e algoritmos probabilisticos



# Estudo dirigido:

***Busca Local por feixe*** 
	Manter k estados em paralelo (quantos candidatos são mantidos por etapa) -> representa a *largura* do feixe ou seja quantas soluções ficam na memoria 

Começa inicalizando k estados aleatorios e cada passo gera todos os sucessores de todos os k, pega os melhores k passo repetido ate achar a otima solução ou acabar o numero de tentativas.

no reinicio ele busca fazer de forma independetes cada reinicio

qual a vantagem disso computacionalmente -> redução da complexidade de busca 
ja a sua versao estocastica prisa pela escolha do sucesso a partir dos melhores K produz uma convergencia entre as soluçoes chegando na solução "otima"

quando add a probabilidade podemos assim explocar caminho q seriam menos favoraveis

***Algoritmos evolutivos e geneticos:*** 
	Usa o mesmo presuposto da evoluçao q eles vao acasalando e se melhorando geneticamente acada nova interação 
	Uma população de candidatos que **evolui coletivamente** 
	-> usa como base a busca local estocastica
	cada algoritmo é representado como uma string (booleana) 
		- mede a qualidade => fitness
		- seleciona o mais apto
		- recombina as infos dos mais aptos e geram um filho => crossover
		- matação introduzindo aleatoriamente mudanças para manter a diversidade
		- forma a proxima geração de soluções
	**população, cromossomo, gene**
	- *Gene:* unidade basica de informação
	- *Cromossomo: (individuo)* formado por varios genes -> formam uma solução
	- *População:* conjuto de cromossomos para uma soluçao

pode ser representada de forma binairia, numerica, sim

***Minimax:***
	utiliza da função de utilidade payoff mede a satisfação ou ganho apos uma escolha -> nivel de felicidade => estado terminal


![[INTRODUÇÃO À INTELIGÊNCIA ARTIFICIAL - Aula-1794928998114.webp]]


***Busca competitiva ou adversarial:*** 
-> busca usando multiplos agentes (o agente n está sozinho no ambiente) => agentes com objetivos opostos
nesse modelo o ambiente passa a revidar apartir das açoes do agente jogos nesse escopo sao baesado pricipalmente em turnos e levam em consideraçao economia, nao-deterministico ou aleatorio e modelagem explicita 

ainda sobre o mimmax ele foca no presuposto de nao ter prejuizo como foco principal
toda a arvore sempre apresenta mais de uma soluçaão final para ambiente porem isso so depende dos agentes q estao se enfretando

*Descisoes otimas nos jogos:* 
-> no jogo da velha max foca em ganhar ja min foca em minimizar o valor de estado para n perder
ou seja max planeja oq vai fazer contando com as açõe de min ja min foca apenas em n ter prejuizo

***Poda alpha-beta:*** o processo de poda foca em otimizar e evitar uma busca muito exaustiva de maneira a encontrar decisoes sem explorar d+ cada no
- ignora grandes partes da arvores q n estao influenciando na descisao final do agente
- $\alpha$ => valor maximo 
- $\beta$ => valor minimo
A busca irá realizar as podas com base nos limiter definodos por essas duas variaveis.

*Eficiencia da poda e ordenação de movimentos:*

sua eficiencia esta sempre ligada a como os movimentos sucessores da poda estao sendo examinados 
se sempre conseguimos explorar sempre os melhores movimentos logo a poda sempre será mais eficiente -> precisa de experiencia previa ou seja killer moves +> permitindo assim q busque quase q o dobro da profundidade no mesmo periodo de tempo 

*heuristica de profundidade limitada:* 

Define um limite o quanto pode explora no lugar de cortar os ramos +> bastante utel em xadrez por exemplo
usamos um teste de corte: sendo isso q descide quando parar a exploração.
+=> Problemas **Quiescencia e Efeito Horizonte**


***Busca em arvore Monte carlo:***





1. **Descreva o funcionamento do algoritmo Minimax e explique por que ele é considerado uma estratégia de “pior caso”.**

*Resposta:* No algortmo MinMax ele tem o presuposto  que o jogador vai sempre tomar a melhor descição que destruao ou seja ele é um algortimo de pior caso uma vez que ele simula o pior cenairo apartir das ações externas q podem ser colocadas sobre ele, e ele tenta evitar esse pior cenario tentando maximizar seus ganhos a longo prazo ou minimizar seus prejuizos

2. **A Poda Alpha-Beta é uma otimização do Minimax. Em termos conceituais, o que significa “podar” um ramo da árvore e como essa técnica melhora a eficiência da busca?**

*Resposta:* Como o MinMax olha jogadas a frente e montando e esperando sempre que o oponente quer destrui-lo ele acaba espandido tambem possibilidades de nos q nunca vao acontecer a pode serve justamente para evitar que fique como possibilidades q n vao acontecer na memoria do algoritomo fazendo ele parar de espandir aquile no ignorando grandes partes da arvores q n estao influenciando na descisao final do agente, otimizando e evitando uma busca muito exaustiva de maneira a encontrar decisoes sem explorar d+ cada no.
- $\alpha$ => valor maximo 
- $\beta$ => valor minimo
A busca irá realizar as podas com base nos limiter definodos por essas duas variaveis.

3. **Explique o princípio da Poda Alpha-Beta, detalhando como os limites α e β são utilizados para cortar a busca quando o valor de um nó é conhecido por ser pior do que o limite estabelecido pelo jogador em um nível superior.**

*Resposta:* Como dito acima n precisa gastar tempo explorando um ramo do jogo se ja sabe q n vai acontecer ja q a descisao do oponte n leva para aquilo ou seja e já descobriu que o oponente tem como forçar uma situação pior do que uma alternativa que você já tem garantida assim o algoritmo mantem dois valores 
- $\alpha$ => valor maximo -> ja garantido
- $\beta$ => valor minimo -> ja garantido

Tendo duas situações onde a direta leva a 5 e a esquera a 3 sendo $\alpha$ = 5 e $\beta$ = 3 logo como temos que $\alpha$ como maior ja de forma garantido essa descisao n precisamos explorar o caminho q seria cirado por $\beta$ ja q ele n traz uma recompesa maior para o agente logo podamos $\beta$.

4. **Demonstre como a qualidade da ordenação dos movimentos (move ordering) influencia drasticamente a eficiência, explicando que o Alpha-Beta com ordenação perfeita pode resolver uma árvore aproximadamente duas vezes mais profunda que o Minimax.**

*Resposta:* como a eficiencia da poda esta ligado diretamente ao numero e a ordem dos movimentos em q sao feitos uma vez q sempre exploramos os melhores movimentos primeiros tornamos a poda mais eficiente ja q podemos definir os melhores movimento por experiencias previas ou seja os killer moves sendo esses os q demonstram os melhores rendimetos em minmax dessa forma como minimizamos o numero de passos para os melhores caminhos inciais quase q dobramos o numero da profundidade e cai a complexidade de tempo.


5. **Quais são as limitações do algoritmo Minimax e da poda Alpha-Beta que motivam o uso de Monte Carlo Tree Search (MCTS) em jogos mais complexos como Go?**

*Resposta:* um dos problemas do minmax é tentar ler de forma larga o tabuleiro varrendo quase todas possiveis jogas mesmo com a poda seja perfeita o torna o processamento mais lento do que apenas inferir a proxima jogado pelo valor atual de ação estado como é no monte carlo simulando a proxima jogada n perdendo tempo tento prever ou inferir as coisas se torna mais eficiente e depois retropropaga os resultado.

6. **Explique os quatro estágios do MCTS (Seleção, Expansão, Simulação e Retropropagação) e como eles contribuem para a melhoria progressiva da árvore de busca.**

*Resposta:* ele seleciona um valor de estado ação para realizar depois expande quais as suas proximas possibilidades simula as jogas futuras apartir dos passos de espasao toma a descisao e depois retropropaga o numero de vezes q o no foi usado e o numero de vitorias q ele consegiu por meio daquele valor de estado ação e  toma a descisao no tabuleiro n simulado e sim no real 


7. **O MCTS utiliza um equilíbrio entre exploração e explotação (exploration vs. exploitation). Explique essa dualidade e como o critério UCT (Upper Confidence Bounds for Trees) lida com esse equilíbrio.**

*Resposta:* a explotaçao e a parte gananciosa q visa continuar expandido os ramos q ja provaram ter uma alta taxa de vitorio para aquele jogo ja e exploração é a parte curiosa do algoritmo q visa visitar ramos q foram pouco vistos ou poucos testados depois da simulação em caso do agente ter um lado desse com mais vies do q o outro a variedade dos caminhos q ele pode tormar ou q ele pode acabar mudando de rota seriam baixos alem de q caso ele so seja curioso ele so vai ficar abrindo novas possibilidades e ja se ele for muito ganancioso sera miope so vendo um unico caminho o UCT entra nesse equilibrio como uma politica de seleção q considera a frenquencia de vitorias de cada no visitado oq equilibra o agente ser ganancioso e ser curioso.

8. **Por que o MCTS é considerado mais robusto a erros em comparação a algoritmos baseados em heurísticas fixas?**

*Resposta:* ele é mais robusto a erros justamente pode tambem ser curioso e explorar novos caminhos e simular esses caminhos retropropagando essa politica aprendendo muito mais rapido e com mais variacia nos dados e pela parte gulosa ele maximiza o melhor caminho depois de te-lo visitado na simulação. Ja os de forma Heuristicas fixas ele sao formulas fechadas ou seja elas carregam um vies e os erros de quem define essas formulas como no caso do efeito horizonte 


9. **Explique a diferença entre um agente lógico e um agente baseado em busca, destacando como cada um representa o conhecimento e toma decisões. Em que tipo de problema o raciocínio lógico se mostra mais vantajoso?**

*Resposta:* um agente baseado em busca explora as possibilidade e determina qual será a melhor sempre pela situação atual do tabuleiro ja um agente logico ele toma as usa descisoes por meio de uma base de conhecimento ou seja ele precisa pre conhecer o ambiente antes de tomar uma escolha

10. **Por que a Lógica Proposicional é considerada o ponto de partida para o raciocínio em Inteligência Artificial? Explique como ela fornece uma estrutura formal para que agentes possam inferir conclusões válidas.**

*Resposta:* a logica proposional por pode atribuir valor logico ou seja verdadeiro e falso a senteçãs é base desse tipo de agente afinal ele precisa conhcer o ambiente em q ele esta trabalhando e depos de analisar ele toma descisoes logica ou seja verdadeiro q irei para essa casa ou falso n irei para essa casa e ligado com o processo de inferencia ele pode atribuir ou indentificar/deduzir novas informações antes de realizar sua ação ou seja deduzir aspectos n observaveis.


11. **A inferência automática em agentes lógicos depende de representar o conhecimento em uma forma adequada ao processamento mecânico. Explique como a Forma Normal Conjuntiva (CNF), a Regra de Resolução e o método de Prova por Refutação se relacionam dentro desse processo.**

*Resposta:*  
	- Forma normal conjuntiva: como muitas vezes o computador n lida muito bem com senteças muito complexas para facilitar esse processo a base de conhecimento do agente e é convetido de uma forma taltologica mais simples para q o pc possa interpretar de forma mais simples 
	- Prova por refuação: é nada mais q o processo de provar a verdade para chegar justamente q aquela senteça é falsa
	- regra de resolução: como agora temos a cnf para poder quebrar a sentaça de forma mais simples e a prova por refutaçao para facilita logicas mais dificies. A regra de resolução vai buscando procurando duas clausulas (afirmações opostas) cancelando esses pontos e junta oq sobra dessa sentenças em uma nova reaplicando essa logica varias vezes criando novas senteças por meio das antigas.


12. **Explique o que é o Problema da Qualificação Lógica e por que ele limita o raciocínio puramente dedutivo em agentes de IA. Como a Teoria da Probabilidade resolve essa limitação e permite que agentes tomem decisões racionais em ambientes incertos e incompletos?**

*Resposta:* a limitação de um raciocionio puramente dedutivo é q para refletir o mundo real por esse modo é preciso add varias exeçoes para q realmente represente esse mundo ou seja so lida bem com verdades absolutas e n sabe lidar com quase sempre ou meias verdades, ja o processo de solução de probabilidade resolve isso colocando um grau de crença medindo o quando aquilo ele tem certeza sobre aquilo q esta inferindo.

13. **Diferencie Probabilidades Incondicionais (a Priori) e Condicionais (a Posteriori), explicando o papel de cada uma na atualização de crenças de um agente probabilístico. Dê um exemplo prático em que uma evidência nova altera a crença inicial do agente.**

*Resposta:* quando se fala de apriori é o chute inicial antes de olhar para o ambiente ou seja a probabilidade generica de algo acontecer quando ainda esta miupe e a posteriori é a condiçao seria qual a chance de acontecer, dado oq foi visto agora. O papel dessa duas é justamente para raciocinar sob incertezas saindo de uma probabilidade base e a medida q captura as informaçoes sobre o ambiente atualiza a creça do agente.

14. **Explique o significado da Regra do Produto P(A ∧ B) = P(A | B) ⋅ P(B) e descreva como ela fundamenta a relação entre causa e efeito em inferência probabilística. Por que essa relação é essencial para a dedução racional de agentes inteligentes?**
P(A ∧ B) = P(A | B) ⋅ P(B) 
*Resposta:* agente probabilisticos q geralemente iream usar o teorema de bayses nesse estariamos falando de uma estatistica baysiana nesse caso da formula P(A ∧ B) = P(A | B) ⋅ P(B)  temos q P(A ∧ B) como essa probobalidade n é calculada de forma isolada entre os dois conjunto e sim dado q o evento a priori aconteceu e q causou um efeito qual é a probablidade do efeito acontecer por essa causa dessa forma é possivel decompor ambientes complexos de maneira menos custosa para os agentes abstraindo eles em ambientes calculaveis.


15. **O Teorema de Bayes usa quatro termos principais: A Priori, Verossimilhança, Evidência e A Posteriori. O que representa cada um deles no raciocínio de um agente que tenta descobrir uma causa a partir de uma evidência?**

*Resposta:* 

o termo a priori *P(A)* é o conhecimento previo q o agente possui sobre o problema, ou seja a causa
o termo da verossimilhança *P(B|A)* é dado a causa qual a chance de ter esse efeito
o termo da evidencia *P(B)* é a chance do evento acontecer ou seja o efeito
o termo da posteriori *P(A|B)* causa|efeito dado esse efeito qual a chance de ser dessa causa

a formula de bayes em agentes probabilisitco ajuda a decompor ambientes complexos no qual o agente n tem toda a informação sobre o amebite de forma com que se torne calculavel apartir dos efeitos de valor de confiaça (verossimilhaça) e o seu conhecimento previo antes de realizar o proximo movimento, ou seja ele sabe qual o estado ele esta(efeito) qual a açao (causa) q o levo a isso e se repetir ou realizar outra açao e dessa forma a cada passo decompor o tabuleiro e inferir valos sobre cada passo


16. **Por que a Probabilidade A Priori pode ter um grande impacto no resultado final do Teorema de Bayes? Use o exemplo da meningite para explicar por que uma doença rara continua tendo baixa probabilidade, mesmo quando o sintoma é muito característico.**

*Resposta:* O componente apriori atua como se fosse um peso de vies sobre a descição do agente, pois ele atua refletindo a realizade do ambiente em q o a gente se encontra oq faz o agente n tomar suas escolhas apenas na força bruta do tentar e erro ou seja ele passa a n so depender do valor da verossimilhaça.

17. **Descreva o princípio do Classificador Naive Bayes e explique por que ele é chamado de “ingênuo”. Em que tipo de problema essa suposição de independência condicional se mostra eficiente, e em que situações ela pode ser irrealista?**

*Resposta:* inicialmente sabemos q o naive bayes usa o teorema de bayes como base para classifcar as coisa ou seja, ela apenas atua em usar classificar entre as features da informação a mais provavel qual grupo aquela informação mais se ecaixa ou seja classificando ela em grupos ele se torna ingenou pq ele faz uma suposição matematica independeica condicional entre os atributos atuais ou seja q todas as caracteristicas sao independentes entre as classes entao ele simplesmente multiplica a probablidade individual de cada um oq evita sobreposiçao 

18. **Explique o que é uma Rede Bayesiana, descrevendo o papel do grafo acíclico dirigido (DAG) e das tabelas de probabilidade condicional (CPTs). Por que essa representação é mais compacta que a distribuição conjunta completa? Use o exemplo do alarme para comparar o número de parâmetros necessários em cada caso.**

*Resposta:* esse metodo combina teoria dos grafos com teoria probabilistica ou seja qual a probabilidade de entrar naquele oq permite q um agente pense sobre as incertezas de forma eficente a dag é a estrutura qualitativa da rede e cada no e a representação das variaveis aleatorias do ambiente as arestas sao os pontos de dependecia causa efeito ja a cpt é a parte quantitativa do algoritmo, o impoacto dos pais sobre os filhos ex um n tem pai logo é armazenado apenas a info apriori

19. **Explique a regra da fatoração P(X₁, …, Xₙ) = Πᵢ P(Xᵢ | Pais(Xᵢ)) e mostre como ela decorre da regra da cadeia e das independências condicionais representadas no grafo. Por que a ordem em que as variáveis são consideradas na construção da rede (causal ou diagnóstica) afeta a topologia resultante e o custo da inferência?**

*Resposta:* 

- Regra da fatoração: a probabilidade conjunta completa de uma rede pode ser feita multiplicando as probabilidades condicionais locais
- Derivação via regra da cadeia e independencia condicional: tem como vies q cada no condicionalmente independete de todos os seus nao-descendentes ou seja todo aqueles q n sao pais de um no podem ser removidos
- Impacto da ordem na topologia e no custo: a ordem como a insercao e feita autera drastivamente a estrutura da rede
	- Ordem caual: é feito antes das causas dos efeitos
	- Ordem diagnostica: sao feitos os efeitos antes ads causas

20. **Explique o que significa realizar inferência em uma Rede Bayesiana, distinguindo as variáveis de consulta, de evidência e ocultas. Por que calcular a probabilidade de uma causa dado um efeito exige um raciocínio diferente de calcular a probabilidade de um efeito dada uma causa? Ilustre com um exemplo de sua escolha em que uma evidência aumenta a crença numa causa sem torná-la a explicação mais provável.**

*Resposta:* a inferencia nessa rede significa calcular a distrubuição de probabilidades a posteriori sobre o conjuto de variaveis.
- efeito casual vs raciocinio diagnostico:
	a probabilidade de um efeito dada a causa oq é difeitente de causa dado um efeito oq define a direçao do grafo
		-- efeito dada a causa é o raciocinio preditivo segue a direçao das setas da dag (pais para o filho) 
		-- causa dado o efeito é o raciocinio diagnostico ou seja vai no sentido oposto da dag seguindo dos filhos para os pais

- exemplo: alarme residencial onde a um roubo ou terremoto oq pode diparar o alarme
	antes da evidencia: chance da casa esta sendo rouba 
	apos a evidencia: o alarme dispara essa evidencia faz a chance de ser assalto crescer mas se ela n for a causa com grande probabilidade ainda n pode ser oq realmente causou pode ser um terremoto supomos q a priori seja 1% depois da evidencia subiu para ser assalto 40% ainda existe 60% de n ser assalto e sim um terremoto ja q a probabilidade apriori era extremamente baixo.

21. **Enuncie a hipótese de Markov e explique o que ela simplifica na modelagem de processos que evoluem no tempo. Por que ela é uma escolha de modelagem, e não uma propriedade do mundo? Dê um exemplo em que ela seria inadequada e indique como o modelo poderia ser ajustado.**

*Resposta:* 