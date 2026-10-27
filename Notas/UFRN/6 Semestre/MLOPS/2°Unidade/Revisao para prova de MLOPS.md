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
	- Model
	- View
	- Controller