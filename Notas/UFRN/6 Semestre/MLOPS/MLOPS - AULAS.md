**Andrew Ng** 

Conhecer mais a teoria mesmo q o cosifo seja perqueno
ambiente -> sensores -> modelo -> A alguma coisa ai

metodos e ordem de como fazer o processo de MLOPS

Escopo e desing <=> preparar dados <=> preparar modelo <=> implantação e monitoramento (Funciona como umm circulo nao como uma progreção)

so deve ser avitado voltar para escopo e desing (evitar ao maximo)

<mark style="background:#40a9ff">Projetando projetos de ML</mark>

remover os metada dados e marcas dagua dos documentos.


# Aula 02:

predição é local a explicação é global

### Quando faz sentido usar ML?


/foto do slide

**Coisas de processo criativo**

# Aula 03:

weapons of math destruction 
Drift de modelo

# Aula 04:

**Formatos de dados:**  json, csv, parquet(baseado em colunas binario)
podemos modelar inicalmente assim como modelamos em banco de dados (diagrama de entidades e relacionamento)

Data warehouse => apenas para dados processados
Data lakes => para dados brutos em grande escala (pode tudo)
***HDFS***

Broker para gerenciar a fila de dados: Filas para processamento assincrono. (event-drive)

***ETL(Extract, Transform, Load)*** é como cozinhas as coisas na cozinha e so levar o prato para o caba comer 


*AutoML e Auto-sklearn*

# Aula 05:
**Workflow:** apenas a sequência de tarefaças
**Pipeline:** é o Workflow q processa dados A para B
-> o agendamento é via *CRON*

***Apache AriFlow*** -> apenas Tarefaças sequênciais não tem tarefaças ciclicas. 
- de forma direcional. 
- *dag*: Organiza e define o floxo de trabalho de um pipeline.

# Revisão da Unidade 01:

**Escopo e desing:** escalerecer o problema e planejar solução
**Preparação dos dados:** definir e coletar dados, rotular e organizar, definir e transformar as features
**Modelagem de ML:** treinar e avaliar, selecionar e otimizar
**Implantação:** implantar e monitorar (testes), // (produção), avaliar e refletir o impacto

-> A estrutura deve compor os dados da melhor maneira para n tornar a analise e o uso deles caotica
Dados -> coleta -> armazenameto (a forma aqui é crucial no futuro) -> processamento -> analise -> Dados (eles refinados e trazendo novas informações)

Dados de usarios => todos os formatos (texto, imagem, video) q eles mesmos inserem
Dados de sistemas => logs ou e resultados de modelos (erros em apps)
Base de dados => Dados de invetario (loja)
Dados de terceiros => Dados adquiridos de outra fonte sem ser fonte primaria (fontes de outra empresa)

Os principais desafios nesse nesse processo de preparar os dados se encontram em:
- estrutura dos dados -> json (flexivel e legivel), csv (como um exel), parquet (binario porem eficiente mesmo q n seja legivel)
		- Relacional -> esquemas fixos diagramas
		- nao relacional -> documentos linhas/coluna/grafos => modelagem Hierarquica
		- Modelo de dados é a logica, banco de dados é a implementação fisica
				- csv, bancos relacionais, NoSQL
				- *Data Warehouse* dados ja processados (relatorios ja fechads)
				- *Data Lakes* para dados ainda n processados (brutos) grande escala
- erros de formatação
- volume
- privacidade
- esquema dos dados
