
![[Lista 01 da Unidade 01-1788650199295.webp|1770]]

#### *a) Contexto e escopo*
domínio: clínica especializada em acompanhamento nutricional e prescrição dietética individualizada.

**Atores e usos do sistema:**

  - Nutricionista: Realiza a anamnese clínica, registra métricas antropométricas (peso, dobras, circunferências) nas consultas, analisa laudos de exames laboratoriais, consulta a tabela de alimentos e prescreve planos alimentares estruturados por refeições.
  
  - Paciente: acessa o sistema para visualizar seu histórico de consultas, checar prescrições e cardápios vigentes, acompanhar a evolução de medidas e consultar orientações gerais passadas pelo profissional.
  
  - Atendente: gerencia a agenda da clínica, marcando novas consultas e retornos para os nutricionistas, alterando o status dos agendamentos (confirmado, realizado, cancelado).

**Recorte e delimitação:**

1. **o que entra no banco:**
					 Gestão de cadastros e acessos de pacientes e nutricionistas.
					 Controle de agendamentos e status de fluxo de atendimento.
					 Registro de dados clínicos perenes (anamnese) e séries temporais de evolução física (consultas e avaliações).
					 Repositório de metadados de exames laboratoriais.
					 Tabela de composição nutricional dos alimentos (taco/macronutrientes).
					 Prescrição dietética completa (plano alimentar, divisão de refeições e itens/alimentos associados com quantidades).

2. **O que fica de fora e justificativa:**
						Processamento de pagamentos, faturamento e emissão de notas fiscais: o foco da modelagem é estritamente clínico e operacional.
						Módulos fiscais de pagamento possuem regras contábeis complexas e auditoria própria, devendo operar como microsserviços apartados ou integrações externas.
						Armazenamento binário de arquivos físicos de exames: arquivos como pdfs e imagens pesadas degradam o desempenho do banco relacional.
						Armazena-se apenas a uri (arquivo_url).

#### *b) Metadados e relações:*
no link se encontra o codigo no github que foi usar para modelar as relações acima:
https://github.com/Matheus-dCastro/BANCO-DE-DADOS/tree/73ccf71e6a8acfc3180b3270d4f07b6a02b06258/Projeto%20lista%2001
nele pode ser observado como foi feito cada tipos de ligação e seus tipos.


**Resumo das Cardinalidades:**
	
pacientes (1) —— (N) agendamentos

nutricionistas (1) —— (N) agendamentos

pacientes (1) —— (1) anamneses

pacientes (1) —— (N) consultas_avaliacoes

nutricionistas (1) —— (N) consultas_avaliacoes

agendamentos (1) —— (0..1) consultas_avaliacoes

pacientes (1) —— (N) exames_laboratoriais

consultas_avaliacoes (1) —— (N) exames_laboratoriais

pacientes (1) —— (N) planos_alimentares

nutricionistas (1) —— (N) planos_alimentares

consultas_avaliacoes (1) —— (N) planos_alimentares

planos_alimentares (1) —— (N) refeicoes

refeicoes (1) —— (N) itens_refeicao

alimentos (1) —— (N) itens_refeicao (Relação N:N entre refeicoes e alimentos resolvida pela tabela associativa itens_refeicao)

#### *c) Lógica das relações: *

- agendamentos -> pacientes e agendamentos -> nutricionistas (1:N):
    
    - Cada sessão agendada precisa associar quem será atendido ao profissional que realizará o serviço.
    - As chaves estrangeiras paciente_id e nutricionista_id ficam em agendamentos porque um agendamento pertence a exatamente um paciente e a um nutricionista, enquanto tanto os nutricionistas quantos os pacientes podem participam de vários agendamentos ao longo do tempo.
        
- anamneses -> pacientes (1:1):
    
    - A anamnese agrupa condições crônicas, intolerâncias e histórico alimentar basal, constituindo um perfil clínico perene do paciente. 
    - Paciente_id fica em anamneses com restrição de unicidade (UNIQUE) porque assim somente aquele pasciente terá aquele historico. O paciente existe independentemente da anamnese (na criação inicial da conta), mas a anamnese só faz sentido quanso existe um paciente específico.
        
- consultas_avaliacoes -> pacientes e consultas_avaliacoes -> nutricionistas(1:N):
    
    - Para registrar a evolução das medidas medicas so pasiemte (peso, dobras, composição corporal) em série temporal e rastrear qual profissional realizou a avaliação física.
    - Paciente_id e nutricionista_id ficam do lado de consultas_avaliacoes (lado N), pois uma consulta específica é um evento pontual que pertence a um único paciente e a um único nutricionista, enquanto ambos participam de múltiplas consultas em uma clínica.
        
- consultas_avaliacoes -> agendamentos (1:1 opcional):
    
    - Permite vincular a execução clínica ao horário que foi previamente reservado na recepção ou pelo site.
    - agendamento_id reside em consultas_avaliacoes como UNIQUE e anulável, pois nem todo agendamento resulta em consulta (pode ser cancelado ou haver falta), e um agendamento dá origem a no máximo uma avaliação clínica.
        
- exames_laboratoriais -> pacientes (1:N) e exames_laboratoriais -> consultas_avaliacoes (1:N opcional):
    
    - Para rastreia laudos e exames de sangue/urina pertencentes ao paciente, permitindo opcionalmente vinculá-los à consulta em que foram solicitados ou analisados.        
    - As chaves paciente_id e consulta_id ficam em exames_laboratoriais porque um exame pertence a um único paciente (e no máximo a uma consulta específica), enquanto o paciente pode anexar dezenas de laudos ao longo dos anos.
        
- planos_alimentares -> pacientes, nutricionistas e consultas_avaliacoes (1:N):
    
    - Ela identifica para quem a dieta foi prescrita, qual nutricionista a elaborou e em decorrência de qual avaliação física ela surgiu.
    - As referências paciente_id, nutricionista_id e consulta_id residem em planos_alimentares, visto que um plano nutricionsl tem um único paciente alvo e um autor, enquanto o nutricionista prescreve vários planos e o paciente pode ter planos sucessivos durante seu tratamento.
        
- refeicoes -> planos_alimentares (1:N):
    
    - Um plano nutricional diário não é consumido em dose única; ele se fragmenta em vários momentos do dia (Café da Manhã, Almoço, Lanche, Jantar).        
    - plano_alimentar_id fica em refeicoes (lado N), pois a refeição só existe no contexto de um determinado plano, enquanto um plano agrega múltiplas refeições.
        
- Tabela Associativa, itens_refeicao -> refeicoes e alimentos (Relação N:N resolvida):
    
    - Uma refeição é composta por múltiplos alimentos da tabela nutricional (ex: Arroz, Frango, Salada), e o mesmo alimento (ex: Arroz) pode estar presente em diversas refeições de dezenas de planos de vários pacientes.(N:N).
        
    - Cria-se a tabela associativa itens_refeicao, que recebe refeicao_id e alimento_id como chaves estrangeiras. A chave estrangeira fica na tabela associativa porque cada linha representa uma ocorrência atômica da combinação entre um alimento específico e uma refeição, permitindo anexar atributos da interseção: quantidade consumida daquele alimento, medida_caseira aplicável e observacao de como deve ou como pode ser o preparo.

a baixo segue o codigo usado no dbdiagram.io (foi usando uma extensão no Vscode para facilitar a modelagem *dbdiagram*)

``` python

// ENUMS

Enum status_agendamento {

agendado

confirmado

realizado

cancelado

nao_compareceu

}

  

Enum tipo_agendamento {

primeira_consulta

retorno

}

  

Enum tipo_moradia {

propria

alugada

cedida

outro

}

  

// MÓDULO: USUÁRIOS E ACESSOS

Table nutricionistas {

id int [pk, increment] // Chave primaria

crn varchar(20) [unique, not null] // deve ser consultado se esta ativo para poder prestar serviço

cpf varchar(14) [unique, not null]

nome varchar(120) [not null]

email varchar(150) [unique, not null] // pra fazer o login no sistema

senha_hash varchar(255) [not null]

telefone varchar(20)

criado_em timestamp [default: `now()`]

}

  

Table pacientes {

id int [pk, increment] // para passar nas Request para n espor os dados do cliente nas requisições

cpf varchar(14) [unique, not null] // deve ser tratado com cuidado para n ter vazamentos de dados

nome varchar(120) [not null]

data_nascimento date [not null] // idade calculado na regra de negocios depois receber a info da data de nacimento

email varchar(150) [unique, not null] // para fazer o login no sistema e receber as horientações nutricionais

senha_hash varchar(255) [not null]

telefone varchar(20)

profissao varchar(100)

renda_mensal decimal(10,2)

tipo_moradia tipo_moradia

qtd_pessoas_moradia int [default: 1]

criado_em timestamp [default: `now()`]

}

  

Table agendamentos {

id int [pk, increment]

nutricionista_id int [not null] // para qual proficional ele ira se direcionar, chave estrangeira

paciente_id int [not null] // oq linka um paciente a uma consulta, chave estrangeira

data_hora timestamp [not null]

tipo tipo_agendamento [default: 'primeira_consulta']

status status_agendamento [default: 'agendado']

observacoes text

criado_em timestamp [default: `now()`]

}

  

// MÓDULO: CLÍNICO, ANAMNESE E EXAMES

Table anamneses {

id int [pk, increment]

paciente_id int [unique, not null] // oq linka o historico clinico do pasciente, chave estrangeira

historico_alimentar text

historico_familiar text

doencas_cronicas text

alergias text

intolerancias text

medicacoes_em_uso text

atualizado_em timestamp [default: `now()`]

}

  

Table consultas_avaliacoes {

id int [pk, increment]

agendamento_id int [unique]

paciente_id int [not null] // chave estrangeira

nutricionista_id int [not null] // chave estrangeira

data_avaliacao timestamp [default: `now()`]

peso decimal(5,2) [not null, note: 'em kg']

altura decimal(3,2) [not null, note: 'em metros']

circunferencia_cintura decimal(5,2) [note: 'em cm']

circunferencia_quadril decimal(5,2) [note: 'em cm']

percentual_gordura decimal(4,2)

percentual_massa_magra decimal(4,2)

notas_evolucao text [note: 'notas da nutricionista sobre o paciente']

}

  

Table exames_laboratoriais { // chave estrangeira

id int [pk, increment]

consulta_id int

paciente_id int [not null] // chave estrangeira

nome_exame varchar(100) [not null]

data_realizacao date [not null]

resultados text

arquivo_url varchar(255) [note: 'link para PDF/imagem do exame anexado']

criado_em timestamp [default: `now()`]

}

  

// MÓDULO: ALIMENTOS E PRESCRIÇÃO NUTRICIONAL

Table alimentos {

id int [pk, increment]

nome varchar(150) [not null]

porcao_base decimal(6,2) [default: 100.00, note: 'em gramas ou ml']

calorias_kcal decimal(6,2) [not null]

carboidratos_g decimal(6,2) [not null]

proteinas_g decimal(6,2) [not null]

gorduras_totais_g decimal(6,2) [not null]

fibras_g decimal(6,2) [default: 0]

sodio_mg decimal(6,2) [default: 0]

micronutrientes_info json [note: 'vitaminas, minerais e detalhes extras']

ativo boolean [default: true]

}

  

Table planos_alimentares {

id int [pk, increment]

paciente_id int [not null] // chave estrangeira

nutricionista_id int [not null] // chave estrangeira

consulta_id int

titulo varchar(100) [not null, note: 'Ex: Dieta Hipertrofia Fase 1']

data_inicio date [not null]

data_validade date

orientacoes_gerais text

ativo boolean [default: true]

criado_em timestamp [default: `now()`]

}

  

Table refeicoes {

id int [pk, increment]

plano_alimentar_id int [not null]

nome varchar(80) [not null, note: 'Ex: Café da Manhã, Almoço, Ceia']

horario_sugerido time

ordem int [default: 1]

}

  

Table itens_refeicao {

id int [pk, increment]

alimento_id int [not null]

refeicao_id int [not null]

quantidade decimal(6,2) [not null, note: 'baseado na porção em g/ml']

medida_caseira varchar(100) [note: 'Ex: 2 colheres de sopa cheias']

observacao text

}

  

// RELACIONAMENTOS (REFS)

  

// Agendamento

Ref: agendamentos.paciente_id > pacientes.id

Ref: agendamentos.nutricionista_id > nutricionistas.id

  

// Anamnese e Avaliações

Ref: anamneses.paciente_id - pacientes.id

Ref: consultas_avaliacoes.paciente_id > pacientes.id

Ref: consultas_avaliacoes.nutricionista_id > nutricionistas.id

Ref: consultas_avaliacoes.agendamento_id - agendamentos.id

Ref: exames_laboratoriais.paciente_id > pacientes.id

Ref: exames_laboratoriais.consulta_id > consultas_avaliacoes.id

  

// Prescrição / Dieta

Ref: planos_alimentares.paciente_id > pacientes.id

Ref: planos_alimentares.nutricionista_id > nutricionistas.id

Ref: planos_alimentares.consulta_id > consultas_avaliacoes.id

Ref: refeicoes.plano_alimentar_id > planos_alimentares.id [delete: cascade]

Ref: itens_refeicao.refeicao_id > refeicoes.id [delete: cascade]

Ref: itens_refeicao.alimento_id > alimentos.id

  

// AGRUPAMENTO VISUAL NO DIAGRAMA

  

TableGroup Acessos_e_Atendimento {

nutricionistas

pacientes

agendamentos

}

  

TableGroup Clinico_e_Prontuario {

anamneses

consultas_avaliacoes

exames_laboratoriais

}

  

TableGroup Nutricao_e_Dietas {

alimentos

planos_alimentares

refeicoes

itens_refeicao

}
```