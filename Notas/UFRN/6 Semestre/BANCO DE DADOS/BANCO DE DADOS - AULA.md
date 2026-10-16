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
