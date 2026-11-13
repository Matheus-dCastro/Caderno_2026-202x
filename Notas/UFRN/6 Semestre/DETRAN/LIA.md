# Sprint 1: 

#### Bloco 1: Infraestrutura e Conteinerização (Dias 1 a 4)

- **Banco de Dados em Docker (`docker-compose`):**
    
    - Subir o container do PostgreSQL (para persistência de dados relacionais e metadados de processos).
        
    - Configurar volumes persistentes (`volumes:`) para evitar perda de dados ao derrubar os containers.
        
    - Configurar variáveis de ambiente (`.env`) para gerenciar credenciais de forma segura.
        
- **Dockerização da Aplicação:**
    
    - Criar o `Dockerfile` otimizado para o microsserviço/API em FastAPI.
        
    - Garantir a integração de rede interna no Docker Compose entre a API e o PostgreSQL.
        

#### Bloco 2: Refatoração da Arquitetura e Módulos (Dias 5 a 8)

- **Reestruturação de Pastas (Clean Architecture / Modular):**
    
    - Separar claramente as camadas: **Rotas/Endpoints** (controllers), **Serviços** de negócio, **Repositórios/Acesso a Dados** (SQLAlchemy ou ORM escolhido) e **Módulo de IA** (conexão com LangChain/AgentKit e LLMs).
        
- **Modelagem do Fluxo do Agente:**
    
    - Ajustar as classes de estado e o pipeline de execução do agente (entrada de dados do auto-infracionamento -> estruturação do prompt -> inferência -> geração do rascunho de parecer jurídico).
        

#### Bloco 3: Conectividade de Endpoints e Banco (Dias 9 a 11)

- **Conexão API ↔ Banco:**
    
    - Implementar a camada de persistência para salvar as requisições recebidas e os pareceres gerados pela IA.
        
- **Conexão API ↔ Modelo/Agente:**
    
    - Garantir que o endpoint principal receba o payload do processo administrativo de trânsito, acione o AgentKit/FastAPI e devolva a resposta estruturada.
        
- **Configuração de Webhooks:**
    
    - Estruturar o endpoint receptor de webhooks para comunicação assíncrona com os sistemas do DETRAN-RN.
        

#### Bloco 4: Testes e Correções Finais (Dias 12 a 15)

- **Testes Automatizados Básicos:**
    
    - Escrever testes unitários para os endpoints principais usando `pytest`.
        
    - Validar o fluxo de ponta a ponta (mocking de requisições de infrações e resposta do agente).
        
- **Correções de Implementação:**
    
    - Ajustes finos de tratamento de exceções, logs estruturados e estabilização de prompts


