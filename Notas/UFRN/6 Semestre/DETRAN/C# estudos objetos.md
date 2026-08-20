# Recurso de infração


Consultar, visualizar (parecer, depachos, votos) e atramitação de processos entre setores => validando requisitos: [*obrigatorios*] : assinaturas e despachos.

### Techs:

<mark style="background:#40a9ff">db:</mark> sql serve, postgress SQL;
<mark style="background:#40a9ff">techs:</mark>  Entity Framework, Docker, Kubernets, Swagger/Swashbuckle,
<mark style="background:#40a9ff">seguranaça:</mark> token JWT

*post/.../arquivos:* metodo responsavel -> lista (pdf, imagens) realiza bloqueio de visualizar (Auditoria)

- Todos os meios sao string

=> return: infos do processo e documentos
=> erro: token invalido (401)
=