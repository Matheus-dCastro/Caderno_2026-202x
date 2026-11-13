W.A.V.E.R. (Wi-Fi Assisted Volumetric Environment Reconstruction): Framework para Gêmeos Digitais Paramétricos 3D e Estimativa de Densidade Interna Cross-Modal.

• Conceito Principal: Transformar matrizes de sinal Wi-Fi CSI (coletadas via ESP32 de baixo custo) em objetos 3D vetorizados e simuláveis (malhas sólidas .obj/.stl), indo muito além de mapas de calor 2D ou esqueletos de palito.

• Pipeline de IA Híbrido:

  • CNN: Atua na percepção e extração de características de baixo nível e atenuação dielétrica a partir dos dados de rádio.

  • LLM / VLM: Atua como o cérebro paramétrico, aplicando conhecimento prévio (anatomia e física) para estruturar a geometria e preencher lacunas de resolução.

• O Diferencial de Densidade (Cross-Modal Learning): Uso de Tomografia por Impedância Elétrica (EIT) como "Professor" em ambiente simulado/laboratório para ensinar a IA a correlacionar a atenuação das ondas de rádio com a matriz de densidade interna de variados objetos, permitindo generalização de materiais sem hardware de contato na inferência.










**Título do Projeto:** Sensoriamento RF Generativo: Da Matriz CSI à Vetorização 3D e Análise Volumétrica Cruzada.

**1. O Problema** As pesquisas atuais de _RF-Sensing_ (inclusive do MIT) param na geração de mapas de calor 2D ou na estimativa de "esqueletos de palito" (_keypoints_). O rádio atual não enxerga matéria, densidade ou volume sólido, limitando-se a rastrear humanos de forma abstrata.

**2. A Nossa Proposta (A Inovação)** Queremos transformar o sinal de Wi-Fi CSI (coletado por um hardware ultrabarato, o ESP32) em um **Gêmeo Digital 3D vetorizado e simulável** (uma malha paramétrica sólida, tipo `.obj` ou `.stl`), e não apenas uma imagem achatada na tela.

**3. O Pipeline de Inteligência Artificial (Híbrido)** Para não cairmos no erro de usar uma IA "caixa-preta", dividimos a engenharia em duas partes:

- **A CNN (Percepção):** Filtra a matriz bruta de rádio, lidando com ruídos (_multipath_) e extraindo os vetores de espaço e a atenuação global.
    
- **O Modelo Multimodal / VLM (A Razão):** Pega os dados limpos da CNN e usa _Prior Knowledge_ (regras de anatomia e física) para estruturar a geometria 3D, preenchendo as lacunas que a resolução do Wi-Fi não alcança.
    

**4. O Pulo do Gato (Densidade via Cross-Modal Learning)** A maior inovação é como vamos inferir a composição interna do objeto (ex: se é oco, madeira, osso ou músculo). Faremos um treinamento _Teacher-Student_:

- No laboratório, usaremos **Tomografia por Impedância Elétrica (EIT)** como "Professor" simultâneo ao Wi-Fi. A IA aprende a correlacionar o quanto a onda Wi-Fi atenuou com a matriz exata de densidade do EIT.
    
- Na prática (Inferência), o EIT é descartado. O sistema usa apenas o Wi-Fi CSI, e o LLM generaliza e injeta sinteticamente a densidade na malha 3D baseando-se apenas na assinatura dielétrica da onda.
    

**5. Fase Atual (Status)** Por enquanto, o escopo está estritamente focado na **Fase 1 (Fundamentação Teórica e Simulação Computacional)**. Estou pesquisando frameworks para emular os sinais EIT matematicamente e usar datasets abertos de CSI (como o Widar3.0). O desenvolvimento de hardware físico e PoC no ESP32 ficará para janeiro de 2027.


- O que nós temos na literatura sobre reconstrução 3D com wifi?
- O método com wifi é mais barato (financeiramente) do que outros métodos, por exemplo, usando som?
- Por que o método com wifi seria melhor?
- Qual a escala de resolução da leitura por wifi?
- O quanto a distância entre os pontos de Wi-Fi influencia a resolução da leitura?
- Essa ideia poderia ser desenvolvida com roteadores comerciais?

