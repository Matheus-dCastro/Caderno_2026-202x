# Recurso de infração


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
