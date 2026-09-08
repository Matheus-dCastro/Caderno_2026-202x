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
- 