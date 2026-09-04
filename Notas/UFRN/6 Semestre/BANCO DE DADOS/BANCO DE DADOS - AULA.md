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


# Slide 02:

Primari key -> PK
Candidate Key -> CK >=> SK>CK>PK
Super key -> SK


