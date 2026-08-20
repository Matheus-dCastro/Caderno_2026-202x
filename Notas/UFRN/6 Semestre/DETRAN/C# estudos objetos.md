=# Recurso de infração


Consultar, visualizar (parecer, depachos, votos) e atramitação de processos entre setores => validando requisitos: [*obrigatorios*] : assinaturas e despachos.

### Techs:

<mark style="background:#40a9ff">db:</mark> sql serve, postgress SQL;
<mark style="background:#40a9ff">techs:</mark>  Entity Framework, Docker, Kubernets, Swagger/Swashbuckle,
<mark style="background:#40a9ff">seguranaça:</mark> token JWT

*post/.../arquivos:* metodo responsavel -> lista (pdf, imagens) realiza bloqueio de visualizar (Auditoria)

- Todos os meios sao string

=> return: infos do processo e documentos
=> error: token invalido (401)
=> error: sem permição (403)

*post/.../enviar:* finaliza a analise e tramita, validação de negocio (ex.Despachos, assinatura de voto) 

**Antes de mover:** 

- Todos os meios sao string

=> return: success: bool, data (lista) mensagem: string (caso de erro messagem -> error:string)


*post/.../anexarParecer:* gera pdf apartir do html -> registra no processo e de forma opcional pode fazer o upload em lote dos arquivos => pdf é obtido por meio do token jwt (multipart/form-data: content-type)

=> in: + token
 "codigoOrgao": 120100,
  "instancia": 2,
  "numeroProcesso": 123456,
  "anoProcesso": 2026,
  restante: string

*get/.../tipoArquivos:* reponsavel listar tipos de arquivos rela ao processo

*get/.../orgaos:* lista quais orgaos o operador tem

# JAIR: Junta Administrativa de Recursos de Infração




- **`Domain` (Núcleo do Negócio):** É o centro da aplicação e não deve ter dependências externas. Contém entidades de negócio, _Value Objects_, _Enums_, interfaces de repositórios e regras puras do domínio.
    
- **`Application` (Regras de Aplicação):** Orquestra os fluxos do sistema. Costuma conter casos de uso (_Use Cases_ / _Handlers_ como MediatR/CQRS), DTOs, _mappings_ (AutoMapper/Mapster), validações (FluentValidation) e interfaces de serviços.
    
- **`Persistence` (Camada de Dados):** Implementa as interfaces de repositórios definidas no _Domain_. Contém o `DbContext` do Entity Framework Core, migrações (_Migrations_), mapeamentos relacionais e scripts de banco de dados.
    
- **`RecursoInfracaoDetranet` (Camada de Apresentação/Host):** Ponto de entrada executável da aplicação no .NET 8 (provavelmente uma **ASP.NET Core Web API** ou **Worker Service**). Contém o `Program.cs`, _Controllers_ ou _Minimal APIs_, `appsettings.json` e a injeção de dependência que amarra todas as outras camadas.

# Arquitetura 