---
aliase:
---
Sistema de Banco de dados:
	programas de aplicação
Software de SGBD:
	software para processar consultas/programas
	-> software para acessar dados armazenados

*<font color="#ff0000">Metada dados:</font>* dados sobre os dados amarzenados +> a definição de como vou organizar as informações


=> outra forma de como estruturar um banco q seja a depender do caso melhor q um banco de dados relacional

## Sistema Hierárquico e de rede — a era dos ponteiros:

os dois são lentos para fazer buscas pois fazem elemento a elemento ja q todo mundo ta ligado
o mais lento para gerir sem principalmente o de rede por ter q fazer action duplicadas para cada tipo de relações
mas n tem redundancia

# NoSQL: Escala horizontal e esquema flexivel

Boa parte dos banco n relacionais se adequam ao modelo do sql 

Um banco trasicional -> foca no 1 a 1 
um banco analitico -> uma operação para todos de uma vez só

# Revisao da unidade 01

#### Dados: 
É um fato conhecido que pode ou q foi registrado quem tem um significado impirico.
#### Banco de dados:
É uma coleção de dados que estão relacionados de alguma forma
- **Coleção Relacionada:** os dados se referem uns nos outros
- **Dominio de discuros:** é a parte do mundo q ele representa
- **Escopo definido:** A motivação e para quem ele serve
#### SGBD:
É o que faz o gerenciamento do banco conjunto de tools -> é o<font color="#ffff00"> software </font>

=> Um sistema de DB é o sgbd junto com o banco + as demais ferramentas de manipulação

1. Definir
2. Contruir
3. Manipular
4. Compartilhar

Metada dados => dados sobre os dados
Catalogo => SGBD guarda a descrição do bando (estrutura e suas limitações)
com isso um banco de dados SGBD n serve somente para uma aplicação mas sim para varias

#### Isolamento:

o sistema não sofre quando a mudaças na estrutura dos dados o SGBD continua provendo as informações mesmo com mudanças para os sistemas que o conultam.

-> quando n existe o isolamento fisico ou dos dados toda mudaça obriga o sistema a recompilar tudo

**Controle de concorrência:** mesmo que dois user alterem o mesmo registro exatamente no mesmo instante n deve 
produzir uma incosistencia.

- Concorrencia: Varios acessos ao mesmo tempo 
- Transação: Conjunto de ações tratadas como uma coisa só
- ACID: as 4 garantias que a transação garante

#### ACID:

- ***A***: **A**tomacidade -> Ou todas as operações são validas ou nenhuma é valida
- ***C***: **C**oncorrência -> Vai de estados valido a outro estado sempre respeitando as regras
- ***I***: **I**solamento -> Operações simultanias não interferem uma nas outras
- ***D***: **D**urabilidade -> Tudo q foi confirmado sobrivivera a uma queda do sistema

# Hierárquico e rede - a era dos ponteiros:

-> Nesse os modelos sao ligados por ponteiro fisico no disco oq nos consede
- Uma *estrutura* de <u>arvore</u> => nós são resgistros, arestas sao os caminhos ate os dados
- A *relação* => 1:N estritra -> um filho para um so pai
- E a *ligação* => por meio de um ponteiro fisico q esta gravado no disco

### Como se consulta - DL/1:

vai a raiz q satisfaça a codinção
caminha do pai para o filho
retorna o caminho hierarquico da raiz a folha

### Modelo de rede:

Grafo de uma direção com ponteiro q vai nas duas 
pode fazer consultas M:N sem duplicidade

**Forma de consulta:** 
coloca no registro q quer
do membro atual para o seu proprietario
vasculha na lista de membros de um set
associa membro a um conjunto


**OLTP:** TRANSAÇÃO ->  *Muita* escrita de poucas linhas 
**OLAP:** ANALISE -> *Poucas leituras de muitas linhas*
**DATA WAREHOUSE** -> HISTORICO - repositorio separado da produção

![[BANCO DE DADOS - AULA-1788902728492.webp]]

![[BANCO DE DADOS - AULA-1788902832791.webp]]

# Slide 02:

Primari key -> PK
Candidate Key -> CK >=> SK>CK>PK
Super key -> SK

**Superchave:** pares de valores q identifica as tuplas.
**Chave Candita:** o mesmo q uma super mas nada nela pode ser removida.
**Atributo principal:** está dentro de alguma chave candidta
**Atributo não principal:** não faz parte de nenhuma chave candidata 

![[BANCO DE DADOS - AULA-1789076075472.webp]]

### 1FN: Só valores atômicos

Apneas valores atomico =>

**Proibido:** Celula com lista, tuplas ou tabela dentro
-> **Consequência:** se violada nem chega a ser uma relação.

### 2NF: Nada depende de metade da chave

### 5NF: 

Dependecias de junção cria uma tabela para junta as coisas q foram decompostas

=> a volta para tabela *original* n é possivel

tabela original separa em sub-tabelas menores(projeção)
depois une novamente em uma nova tabela q **não** é a original criando novas linhas na tabela agregando novas infos

### Modelo ER e construção de um ERD:

Como será a modelagem tanto conceitual quando funcional.

# Aula do dia 22.09

Diagrama de modelagem de e relacionamento em banco de dados -> os desenhos vao cair na prova 


# Aula do dia 15/10

contener usando docker de como configura o e usar o postegress como banco de dados

# Aula do dia 20/10:

union, intersect e except



# Revisão da 2°U

Agregação, ACID, Operaçoes sobre tabelas, Consultas

### Aula 08: 

Está usando via Docker para deixando o ambenti replicavel

Cliente -> atributos de informação; 
	   -> PK: CPF unica por entidade
	   -> FK: Fazem um pedido ser a ponte entre varias tabelas(cliente <-> pedidos<->loja<->funcionario<-> pagamento <-> item <-> produto <-> estoque <-> categoria)
	- nesse diagrama basta seguir as setas entre as tabelas para poder fazer montar as tabelas e como as entidades se relacionam

**Tipos de dados que mais vamos usar**

esses tipos montam as tabelas ou seja atribui valores de tipagens a variaveis

**Como criar a tabela:**

### Aula 09:

Inserir, alterar e remover linhas em tabelas relacionais

**Select:** escolhe linhas
**Where:** filtra nas linhas sobre condições booleanas
**Order by e Limit:** uma relação n tem ordem

***WHERE:*** 
usa operadores de = <> <> = para int
and or not
between
in
like ilike
is null

**Count:** depende de como usado pode contar nulls(linhas) nao conta nulls(colunas) count(Distinct) conta todos os valores diferentes e ignora os nulls


### Aula 10:

**Inner join:** cruzamento mais rigoroso (JOIN) exige o par perfeito, so faz a junção se em duas tabelas existir um correspondente perfeito

**Left join:** Cruza de forma boazinha, com quem esta a esquerda, caso n tenha um par perfeito ele simplesmente preenche com nulls, 

**self join:** junçao com ela mesma, tem q passar apelidos para as tabelas.

**WHERE, HAVING e as três contagens:**

where: filtra linhas antes de agrupar, filtra linhas idividuais junta tudo porem é cego para medidas, 
having: filtra grupos depois de agrupar, filtra por grupos bom para juntar as coisas quando sao valores numericos
count: aquele esquema de como ele faz a contagem depende do q vc passa como argumento.

**UNION, INTERSECT e EXCEPT**

**Union:** uniao junta tudo e remove as repetidas
**Intersct:** devolve todo q tem em comum entre as duas tabelas
**Select:** serve para lista coisas entre duas tabelas
**Exept:** devolve oq esta fora da interseção
**From** pega todos e subtrai apartir de um filto os id q satisfaz esse filtro subtrativo

### Aula 11:

Um select dentro do outro: 
	ele primeiro resolve a busca interna para depois resolver a busca do select externo assim q resolve esse passos de dentro pra fora retorna a lista do elementos q se encaixaram la

CTEs subconsultas organizadas:
	**With e With recursive:** fazem o mesmo parecem com um select e fazem de cima para baixo

Funções de procedures:
	funçoes sao como em outras linguagens ja as procedures elas sao destinadas a exec brutas grandes regras de negocio no banco de dados

**Views:** 
	- Comum: guarda apenas o codigo n os dados q o codigo retorna, resolve o reuso ja q a outras coisas como join entre tabelas ficam deterministicas mas n ficam percistentes em disco apenas no momento de run
	- materalizada: aqui fazemos o mesmo passo da comum porem gravamos essas coisas em disco porem ela n atualiza junto com as outras tabelas sempre precisa recriala

**Gatilhos:** 
	- São regras q o proprio bando dispara sozinho ele define quando chamar ou realizar alguma função quando é necessario
	- Estrutura ECA: eventi codição ação
		- **Evento:** insert update delete
		- **Condição:** passo opcional when como e se o gatilho deve agir
		- **Ação:** sempre sera uma function escrita no banco para realizar uma ação
	quando se cria um triger ja se define quando ele vai agir antes depois ou no lugar de algo quando é exec um chamado alguma função no banco de dados