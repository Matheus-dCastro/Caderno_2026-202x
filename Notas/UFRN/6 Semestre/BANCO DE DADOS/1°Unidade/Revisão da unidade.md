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

