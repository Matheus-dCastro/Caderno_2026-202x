## Notas de aulas:

-> Implatação: tudo entre um modelo treinado e o usuario.
-> Serviço: toda base em um unico repositorio, tudo compactado para deploy, chamadas e comonicaçoa interna do sistema
-> codigo em pastas: padrao de MVC, divisao em modals
-> serviço: http usando fastapi
-> manutençao: encapsulado escondendo o codigo por meio de def de alto nivel
-- o modelo deve ser sevido online ou em lotes por meio do docker empacontano o comportamento e as funcionalidade dele

**É feita a implantação em duas frentes:** 
	- Amplo => modelo treinado e basta coloca-lo no ar e consumir todo o meio do caminho -> projetar, escolher arquitetura, organizar codigo, encapsular, subir o serviço
	- Estrito => pega o codigo e sobe o serviço -> apenas subir (DEPLOY)

**1.2 serviço e API:** representam a mesma coisa no contexto de MLOPS
**1.3 1°pergunta de um novo projeto:** qual sera a arquitetura do serviço? 

**2. Arquiteturas do serviço:** 
Como dividir melhor os sistema e como elas iram se comunicar

-> Monolitica: um unico serviço para todo o sistema (simples para desenvolvimento)
-> Monolitica modular: partes independetes q fazem seus trabalho e se juntam no final.
-> Microsserviços: divide em varios serviços separados para atender uma necessidade sua vantagem é a especificidade podendo fazer mais de ums saas consumir um mesmo microserviço
-> Orientada a serviços: SOA reuso entre sistemas governança de contratos entre serviçoes
-> Orientada a eventos: consome oq cada def faz oq ela gerou de objeto ou arquivo e afins 
-> Em camadas: Separa o sistema em niveis horizontais defindos com cada responsabilidade

+> as principais apontadas na web sao monolito, microsserviçoes, SOA e orientada a eventos. 

+> usar uma arquitetura de microsserviços sem uma separaçao das equipes é um tiro no pé

**3.0** cada pastinha tem uma responsabilidade para o sistema essa separação ajuda a manter o controle e o fluxo das informações o mais comum sendo:
	- Model: acesso ao banco
	- View: interface de usuarios
	- Controller: meio termo entre o view e o model para fazer o controle das requisiçoes
no esquemas mais novos o model tem acesso apenas aos equema ja o repository q tem acesso ao banco de fato

*Modelos de ML ficam no service encapsulando o modelo e suas defs*

geralmente são trabalhados de modo http via metodos get, post alem de outros metodos especificos para cada tipo de coisa q queira fazer no sistema.

**5.0** Encapsular o modelo de ML:

- Manutenção do codigo e do sistema do ML;
- Encapsular ajuda a metigar os problema q podem surgir para da manutenção
	- um mesmo encapsulador deve atender os dois requisitos tanto para quem vai prestar manuteção no treino quanto no serviço da aplicação;
	- e puxa no service a solução de ML 

**6.0**  Online ou em Lote:

analise online chega o precisa ser processado e é devolvido momentos depois, ja o sistema em lotes recebe uma ruma de coisa e é devolvido com um tempo depois

**6.3** Previa: Docker

esse é o ponto em q empacotamos o codigo do agente e subimos essa aplicaçao para ser usado 
mas nem todo conteneir é de fato um VM ele chega apenas a compartilhar os recursos do pc


## Intodução ao CI e CD (cdd): 

- Integração continua (CI):
	integra as mudaças de todos com frequência fazendo o check de cada uma automaticamente

	Quando: da um push ou pull
- Entrega e implantação (CD):
	leva para o usuario a resposta
	depois de dar merge na main
	manda a imagem docker pronta para publicar
	cada mudança sobe para produção sozinha

sem esses passos pode restringir a "*funciona na minha maquina*" 
	agiliza e automatiza os processos de deploy alem de implementarde forma automatica os testes

Todo **PR** é sempre verificado do mesmo jeito sempre em uma maquina limpa caso de erro aparece minutos depois onde foi o erro depois de dar push

nunca faz merge com teste vermelho na main 
o processo sempre vira codigo versionado junto da main

biblioteca: Pytest => encontra e roda testes escritos em python, apenas em passar o nome do arquivo

*Os principais teste:* 
	Unitarios: testar funcioes isoladas
	Integração: testar oq passou no unitario juntos
	Ponta a ponta: testar todo o sistema de verdade
	Smoke test: um e2e minimo, o sistema liga e reponde


