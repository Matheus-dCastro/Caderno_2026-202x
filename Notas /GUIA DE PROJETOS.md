## apa da Jornada de Desenvolvimento

```
[FASE 1: Fundações & Dados]   ➔   [FASE 2: Automação & MLOps]   ➔   [FASE 3: Interfaces & APIs]
          (Projeto 1)                         (Projeto 2)                    (Projetos 3 e 4)
                                                                                    │
[FASE 5: IA Generativa Avançada] ◀ [FASE 4: Alta Performance & Cache] ◀─────────────┘
          (Projeto 6)                         (Projeto 5)
```

## 📊 FASE 1: Fundações e Engenharia de Dados Brutos

### Projeto 1: O Alicerce – Pipeline de Dados e Análise Bruta

- **Descrição:** O objetivo deste projeto é provar que você domina o ciclo inicial do dado. Você criará um pipeline automatizado que ingere dados brutos e públicos de mercado (ex: transações financeiras ou e-commerce), valida sua integridade, realiza uma análise exploratória robusta e treina um modelo preditivo clássico de Machine Learning.
    
- **O que você vai desenvolver:**
    
    - **Script de Ingestão:** Código em Python puro que consome dados via scraping ou APIs públicas e os organiza em uma estrutura de pastas simulando um Data Lake local (camadas _Bronze, Silver_ e _Gold_).
        
    - **Camada de Validação:** Implementação do `Pydantic` ou `Great Expectations` para garantir que dados corrompidos ou tipos errados não entrem no modelo.
        
    - **Notebook de Análise Bruta e Feature Engineering:** Tratamento rigoroso de valores nulos, detecção de outliers e criação de variáveis preditivas armazenadas em formato otimizado **Apache Parquet**.
        
    - **Modelagem Clássica:** Treinamento e tunagem de hiperparâmetros de um modelo (ex: _XGBoost_ ou _Random Forest_) usando `Scikit-Learn` e registrando os experimentos com `MLflow`.
        
- **Stack:** Python, Pandas, Numpy, Pydantic, Apache Parquet, Scikit-Learn, MLflow.
    

## ⚙️ FASE 2: Automação de Processos e MLOps Leve

### Projeto 2: O Automatizador – Fluxos de IA com e sem n8n

- **Descrição:** Aqui você transforma o modelo estático da Fase 1 em um componente vivo da operação de uma empresa, dividindo a arquitetura em automações visuais (baseadas em eventos) e automações em código de background.
    
- **O que você vai desenvolver:**
    
    - **Fluxo com n8n (Triagem Inteligente):** Um webhook no n8n recebe um gatilho externo (ex: um e-mail ou formulário). O n8n extrai o texto, consome uma API local em Python que analisa a urgência do texto usando NLP, e toma uma decisão baseada no resultado (enviar alerta crítico no Discord/Slack ou salvar em planilha).
        
    - **Fluxo sem n8n (Retreinamento Assíncrono com Celery/Redis):** Um script configurado para rodar periodicamente que verifica a chegada de novos dados. Usando **Celery** e **Redis** como _message broker_, o sistema dispara em background o retreinamento do modelo do Projeto 1, avalia se a nova acurácia é superior à atual e substitui o artefato (`.pkl`/`.joblib`) sem derrubar a API de produção.
        
    - **Tratamento de Erros:** Configuração de nós de _Error Trigger_ no n8n para criar caminhos de contingência caso a API de ML fique fora do ar.
        
- **Stack:** n8n, Python (FastAPI), Celery, Redis, Webhooks, Linux Cron / Bash Scripts.
    

## 🖥️ FASE 3: Entrega de Valor e Interfaces do Usuário

### Projeto 3: O Sistema Web – Plataforma de Predição End-to-End

- **Descrição:** Este projeto transforma os modelos de inteligência artificial criados nas fases anteriores em um produto SaaS real acessível via navegador, focando em segurança, monitoramento de métricas e design de software limpo.
    
- **O que você vai desenvolver:**
    
    - **Backend (API de Inferência):** Uma API robusta que recebe requisições JSON, aplica o pré-processamento nos dados em tempo real, executa o modelo e retorna a predição. Inclui controle de acessos com tokens JWT e limitação de requisições por IP (_Rate Limiting_).
        
    - **Banco de Dados de Logs:** Persistência de todas as requisições e predições em um banco PostgreSQL ou MongoDB. Esse log servirá para analisar futuros desvios de dados (_Data Drift_).
        
    - **Frontend Web & Dashboard:** Uma interface web responsiva onde gerentes preenchem dados de entrada em formulários para ver predições instantâneas e acompanham gráficos consolidados com o desempenho geral da empresa.
        
    - **Infraestrutura:** Empacotamento de toda a aplicação usando **Docker** e escrita de testes unitários com `pytest` para a etapa de inferência.
        
- **Stack:** Python (FastAPI), PostgreSQL/MongoDB, Docker, Pytest, HTML/CSS/Tailwind, JavaScript.
    

### Projeto 4: O Aplicativo – IA na Palma da Mão (Edge AI & Cloud)

- **Descrição:** Expandir o ecossistema para dispositivos móveis, demonstrando sua capacidade de trabalhar com restrições de latência, consumo de bateria e arquiteturas híbridas de conexão.
    
- **O que você vai desenvolver:**
    
    - **Aplicativo Mobile:** Uma interface móvel focada na experiência do usuário para interagir com o ecossistema (ex: capturar uma foto de um produto ou registrar um log rápido de atividades).
        
    - **Integração Online e Offline (Edge AI):** Implementar duas rotas tecnológicas no aplicativo:
        
        1. _Rota Online:_ O app consome diretamente a API REST desenvolvida no Projeto 3.
            
        2. _Rota Offline (O Diferencial):_ Converter um modelo preditivo leve para o formato **ONNX** ou **TensorFlow Lite** e embarcá-lo diretamente dentro do aplicativo, permitindo inferências instantâneas mesmo sem sinal de internet.
            
    - **Sincronização Over-the-Air (OTA):** Mecanismo onde o aplicativo checa se há uma versão mais nova do arquivo `.onnx` ou `.tflite` no servidor e faz o download em segundo plano para se manter atualizado.
        
- **Stack:** Flutter ou React Native, ONNX Runtime / TensorFlow Lite Mobile, REST APIs.
    

## ⚡ FASE 4: Otimização de Arquitetura e Alta Performance

### Projeto 5: O Motor de Recomendação e Camada de Cache

- **Descrição:** Resolver o principal gargalo de sistemas de recomendação comerciais: a altíssima latência. Você criará uma arquitetura desacoplada onde predições complexas são feitas em lote de madrugada e disponibilizadas instantaneamente durante o dia.
    
- **O que você vai desenvolver:**
    
    - **Pipeline de Filtragem Colaborativa:** Um algoritmo focado em gerar recomendações personalizadas baseadas no comportamento cruzado dos usuários (usando bibliotecas como `Surprise` ou decomposição de matrizes).
        
    - **Injeção em Memória (Redis NoSQL):** Em vez de forçar a API web a buscar cálculos matemáticos pesados em bancos relacionais a cada clique do usuário, o pipeline pré-calcula o Top 20 itens de cada usuário e armazena diretamente no **Redis** como pares chave-valor.
        
    - **API Ultra Veloz:** Atualização da API do Projeto 3 para ler o Redis. Quando o app ou a web solicitam a home do usuário, a resposta de recomendação personalizada é entregue em menos de $10\text{ms}$.
        
- **Stack:** Python, Redis, Surprise Library, Scikit-Learn, PostgreSQL.
    

## 🤖 FASE 5: Inteligência Artificial Generativa Avançada

### Projeto 6: O Orquestrador GenAI – Plataforma RAG Corporativa

- **Descrição:** O fechamento do ecossistema. Implementar um sistema de IA Generativa moderno utilizando a arquitetura RAG (_Retrieval-Augmented Generation_), permitindo que uma LLM responda a perguntas complexas consultando documentos internos de forma segura e contextualizada.
    
- **O que você vai desenvolver:**
    
    - **Pipeline de Processamento de Documentos (n8n):** Um fluxo no n8n monitora uma pasta ou canal de entrada. Sempre que um novo documento (PDF, Markdown ou TXT) é detectado, o n8n extrai o texto, realiza o agrupamento em pedaços lógicos (_text chunking_) e envia para processamento.
        
    - **Geração de Embeddings e Banco Vetorial:** Um script em Python recebe os pedaços de texto, gera as representações matemáticas vetoriais (embeddings) e os armazena em um banco de dados vetorial específico, como **ChromaDB** ou **Qdrant**.
        
    - **Mecanismo de Busca e Síntese (LangChain):** Uma rota na API do backend recebe a dúvida do usuário no frontend, faz o embedding da pergunta, pesquisa os pedaços de textos mais relevantes dentro do banco vetorial e injeta esses trechos no contexto de uma LLM (pode ser uma API de mercado ou um modelo local rodando via **Ollama**), garantindo respostas precisas, auditáveis e sem alucinações.
        
- **Stack:** n8n, Python (LangChain ou LlamaIndex), ChromaDB ou Qdrant, Ollama / APIs OpenAI, Frontend Web.
    

## 🎨 Guia de Entrega e Apresentação para o Portfólio

Para que esse roteiro salte aos olhos de recrutadores e líderes técnicos, mantenha um padrão visual rigoroso em cada repositório do GitHub:

1. **Diagramas Dinâmicos:** Abra o arquivo `README.md` de cada projeto com um belo diagrama de fluxo de dados desenhado em _Mermaid.js_ ou _Excalidraw_.
    
2. **Trade-offs Técnicos:** Justifique suas escolhas de design. Explique claramente por que usou Redis para cache no Projeto 5 ou por que escolheu o formato Parquet no Projeto 1.
    
3. **Métricas de Negócio:** Sempre encerre a documentação explicando como o projeto economizaria dinheiro, otimizaria o tempo dos funcionários ou melhoraria a experiência do cliente final em uma empresa de verdade.