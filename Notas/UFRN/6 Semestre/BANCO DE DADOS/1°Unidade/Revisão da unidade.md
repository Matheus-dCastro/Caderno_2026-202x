---
aliases:
  - "Revisão da unidade:"
---
### Introdução a banco de dados:

O que é dado: *fatos conhecidos que podem ser registrados e q tem significado.*
	- Registravel
	- Conhecido
	- Significativo

Banco de dados: *coleção de dados relacionais*
	coleção relacionada
	dominio de discurso
	escopo definido

O que é um SGBD:
	Sistema Gerenciador de Bando de Dados (SGBD) 
	Definir: *declar tipos, estruturas, restrições dos dados*
	Construir: *armazenar os dados no meio controlado pelo sistma*
	Manipular: *consultar atualizar inserir e remover registros*
	Compartilhar: *permitir q varios usario acessem ao mesmo tempo*
-> possue: Independencia logica, Independecia fisica, sem isolamento (cada mudança obriga a recompilar)

**Garantias do ACID:**

A Atomicidade Ou todas as operações da transação valem, ou nenhuma vale
C Consistência O banco vai de um estado válido a outro, respeitando as regras
I Isolamento Transações simultâneas não interferem umas nas outras
D Durabilidade O que foi confirmado sobrevive a uma queda do sistema

**No modelo hierarquico:** (1:N) uma relação de pai-filho ou seja um pai pode ter muitos filhos mais um filho so tem um pai
-> ponteiro fisico, gravado no disco
***Vantagens:*** *Mais rapio em (1:N) integrida além do tempo de resposta é estavel*
***Limitações:*** *Mudar o esquema dos dados obriga reescrever o programa, Nao pode ter (M:N) sem q ele acabe dublicando os dados, sem independecia logica nem fisica*

**No modelo de Rede:** A relação é (M:N) na estrutura de um grafo direcional com ponteiros bidirecionais Consegue separa por nivel oq cada user consegue acessar, 
***Vantagens:*** n tem redundancia, acesso é eficas, menos duplicação dos dados.
***Limitações:*** Mais alta complexidade, quase nenhuma indepencia, Mudanças quebram as rotinas 

O grande marco com a chegado do modelo relacional foi quando a idependecia dos dados
*Declarativo, Otimizador (ele escolhe o meio fisico) => O esquema muda sem quebrar quem o busca* 

![[Revisão da unidade-1791247666534.webp]]

Sua principal desvantagem seria escalar horizontal


Ja no NoSQL -> perede a atomacidade e o isolamento de forma total/parcial 

**OLAP:** Colunar, quardando cada coluna de forma continua no disco

*OLTP: transação, OLAP: analise, Data W: O historico do dados*

***Fatos, Dimensões e cubos:***
*Fatos: a medida da receita (o passo a passo)*
*Dimensões: o eixo da analise*
*Cubo: Os fatos organizados*

![[Revisão da unidade-1791248396147.webp]]

os modelos mais antigos n deixaram de ser usados principalmente pelo custo, estabilidade, consequencia de ter q fazer a migração

-> usar um modelo de banco para cada tipo de aplicação,


### Dependência funcional e chaves:

o mesmo x para dois x tem q ter o mesmo valor de y para os dois

-> *Superchave:* atributos q identicam cada tupla
-> *chave candodata:* uma superchave q nada poder ser removido
-> *Atributo principal:* participa de alguma chave candidata
-> *Atributo não principal:* n participa de nenhuma chave candidata

![[Revisão da unidade-1791285718064.webp]]

# Primeira forma normal 1FN:

nessa forma o objetio é evitar q o mesmo dado seja armazenado repetidas vezes, contendo apenas valores *atomicos* (um valor indivisivel) e oq o unico valor em uma tupla seja apenas o unico valor no dominio. => se violar a 1FN n chega nem a ser uma relação.

# Segunda forma normal 2FN:

ja deve está respeitando a 1°forma e n ter dependecia parcial -> todos os atributos q nao fazem parte da chave primario devem depender dela.

# Terceira forma normal 3FN:

ja deve esta na 1° e na 2° nao ter dependencia transitiva -> qualquer atributo q n é chave deve depender da chave primaria
*-> uma variante é a Boyce-Codd: que é quando exite multiplas chavez candidatas q se sobrepoem*

# Quarta forma noemal 4FN:

