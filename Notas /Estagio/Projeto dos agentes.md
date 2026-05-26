@ é um decorador de rotas estilo spring

sempre depois de um decorador de rota temos q passar um def (função do q esta acontecendo)

response_class=htmlresponse => para da resposta em formato de html no lugar de json


jinja2 => lib de crianção de modelos de html

dentro do html: usamos  o {% aqui passamos sintaxe de codigo normalmente %}

entre ele passamos oq queremos expressar dentro da pagina de html

vatiavel.infromação q quero imprimir no corpo da tags normal html e entre essa tag html passamos {{variavel.informação}}


tem q fechar o codigo do mesmo jeito

GRUD

get: ler dados
post: enviar e cirar novos dados
delete: remocer um recurso precisa ser especificado
patch: atualizaçoes parciais em dados
options: retornta os metodos http suportados por um recurso
head: parece o get mas retorna apenas o cabeçalho
trace: usado para teste de diagnostico rastrear mmensagens

deve se preoculpar de como esta importando as coisas 
precisa ter uma rota bem definida

criar as todas com apirouter

# Estrutura de banco de dados

tem q importar o sqlalchemy o crete_engine e o declaretive_base

<<<<<<< HEAD
=======


# conta de usuario

-> rotas de autenticação


criar coisas no banco de dados => post  



-> rotas de clientes


- [ ] criar metodo para atulizar registros de muitos para muitos
- [ ] criar metodos de edição
- [ ] criar metodos de listagem
- [ ] criar metodos de metricas
- [ ] criar as rotas de clientes
- [ ] criar atulizaador de metricas 
- [ ] adicionar a variavel satisfação