# Endereçamento IP: 08

identificar, localizar, encaminhar pacotes, diferente do hostname que apenas identifica quem é IP onde ele está

### 1. Endereçamento IPv4:

- **Estrutura:** numero unico de 32bits anotação decimal separada por pontos.
- **Divisão Hierárquica:** se divide em duas partes
		- Identificador de rede (prefixo)
		- Identificador de estação/Host (sufixo)
- **Interfaces:** Um endereço IP é associado esta ligado a uma interface de rede => conexão entre o dispositivo e o enlace fisico
- **Mascara de rede:** numero de 32 bits q define quais bits pertence a rede e quais ao host -> **CIDR** estima a quantidade de bits destinados ao prefixo
- **Calculo de hosts:** o numero de host é 2<sup>n</sup> - 2 (n numero de bits de host) removemos da conta o endereço da rede e o broadcast.

### 2. Gestão e Organização do espaço IP:

- **Hierarquia de alocação:** IANA coderna o espeaço global, mandando blocos para os RIRs que os distribuem para provedores e insitituições
- **Subnetting e VLSM:** O subnetting permite subdivir a rede em redes menores os VLSM sao mascaras para as sub-redes => permite criar subredes de tamanhos variados
- **NAT:** tradução de endereços permite q varios dispositivos com IPs privados acesse usando um unico ou poucos IPs publicos mitigando q o IPv4 fique cansado

### 3. Endereços reservados e protocolos de apoio:

- **Loopback:** a faixa é usada para host se comunicar consigo mesmo 127 ...
- **DHCP:** plug and play permite o host ganhar um endereço IP, mascara e gateway de forma automatica ao se conectar na rede
- **ICMP:** comunicar erros, informações base da ferramenta de ping

### 4. Endereçamento IPv6:

- **Motivação:** IPv4 n deu conta de tudo
- **Estrutura:** 128 bits cerca de 340 undecilioes de endereços 8 grupos de 4 digitos hexadecimais separados por :
- **Simplificação:** zeros a esquerda podem ser suprimidos e varios zeros consecutivos podem ser comprimidos usando ::
- **TIPOS de Unicast:**
		- **Link-local (FE80::/64)** obrigatoriso e configurado automaticamente para comunicação de mesma sub-rede
		- **Global unicast (GUA)** é o endereços roteaveis na rede publica
		- **Unique-local (ULA)** semelhante a IPs privados do IPv4
		- **Multiplos Endereçõs** no IPv6 é comum e normal que uma unica interface possua varios IPs simultaneamente

![[Revisão-1781384296817.webp]]



# Camada de rede e roteamento 09:

### 1. Visão geral e Localização:

ocorre na camada interna da rede => camada 03 é realizada no modo hop-by-hop

### 2. Entrega direta vs entrega indireta:

verifica dentro dos datagramas se o endereço esta na mesma sub-rede do no atual
- **Entrega direta:** quando o host destino esta na mesma rede **fisica** encapsula contendo o MAC do destino final
- **Entrega indireta:** quando o  destino esta em uma rede fisica diferente encapsula o endereço MAC de um roteador intermediario (gateway)
ambos os casos o IP de destino original nao é alterado no percuso

### 3. Roteamento de proximo salto (next-hop)

Roteador n conhece todo o percuso ate o destino, ele sabe somente o proximo roteador 

### 4. Tabela de rotas e tipos de rotas Unicast:

- a tabela de rotas é usado para identificar o proximo salto
**Classificação das rotas:**

- **Diretamente conectadas:** criadas automaticamente ao configurar o IP e mascara de interface ativa
- **Estatica:** colocadas manualmente pelo admin sao reagem a falhas ou trocas de topologia
- **Dinamias:** aprendidas e mudadas automaticamente atravez de protocolos de roteamento
- **Rota default:** ultimo recurso quando n se tem ciencia do do destino no roteador

### 5. Processamento de datagramas no roteador:

1. **Validação:** verifica o checksum, versao e tamanho (descarta em caso de erro)
2. **TTL:** o tempo de vida decrementado se chegar a zero o pacote é descartado 
3. **Encaminhamento:** calcula o prefixo de rede do destino, olha na tabela e defina interface de saida
4. **Checksum:** sempre calcula antes do envio para o proximo salto
5. **Fragmentação:** se o datagrama for maior q MTU da rede de saida ele se divide em pedaços menores cada qual com seu proprio cabeçalho e novos valorede de TTL e checksum

# 10_camada_de_rede_roteamento_dinamico:

### 1. Funcionamento dos Protocolos de Roteamento:

implementam o roteamento dinamico definindo as regras de troca de info entre os roteadores => reaja a falhas se um cair os outros aprendem o caminho alternativo.

### 2. Metricas de Roteamento:

para ter o melhor (mair rapido) caminho de destino

- **Tamanho do caminho:** numero de saltos
- **Atraso (delay):** tempo detravesia de um enlace
- **Carga:** nivel de oculpado de roteador
- **Confiabilidade:** disponibilidade e erros do enlace
- **Custo administrativo:** config manual ou baseado em negociações do roteadorees

### 3. Tipos de Algoritmos de roteamento:

-> Classifica com base em 3 categorias principais:

- **Vetor de distancia (RIP, EIGRP):**
		- cada roteador envia periodicamente para seus vizinhos diretos sua tabela
		- facil implementação: sofre de convergencia lenta
		- contagem de saltos
- **Estado de enlace (OSPF,IS-IS):**
		- informa sua vizinhança a todos os outros do sistema autonomo por meio de LSA
		- cada um constroi um mapa completo (grafo) e calcula o minimo caminho => algoritmo Dijkstra 
		- Mais custoso q o vetor de distancia
- **Vetor de Caminho(BGP):**
		- associa o endereço destino com atributos no caminho para poder chegar la
		- usado para interconexão de sistemas autonomos (AS)

# 10_camada_de_rede_sistemas_autonomos:

### 1. Definição de identificação:

definido como um conjunto de regras controlado por uma unica autoridade admin => compartilham uma unica politica de roteamento e geralmente usam um unico protocolo para geraenciar seus dados cada AS é identificado com um unico numero para todo o sistema. 

### 2. Gestão de endereçamento:

recebe blocos de endereçamento IP diretamente do RIRs -> pertencem ao proprio sistema autonomo esse endereçamento é independente dos provedores dos quais o AS esta conectado => mudanças nos vizinhos nao afetam os endereços internos

### 3. Tipos de sistemas autonomos:

classifica o ASs de acordo com a conectividade

- **Single-homed (stub):** unico ponto de saida externa
- **Multi-homed:** varios pontos de saida para rede externa
		- sem trasito: n permite trafego de terceiros na rede interna troca apenas entre pares
		- com trasito: permite sistemas vizinhos usar a infra para cheagar ate outros ASs facilitando acesso a rede global

### 4. Pontos de troca de trafego(PTT/IX):

facilitam a troca de trafego entre diferentes ASs reduz custo de trasito, melhora a resistentia, diminui a latencia.

### 5. Protocolos de Roteamento e o BGP:

roteamento de ASs se divide em:
- **Protocolo interno (IGP):** execultado dentro do proprio ASs
- **Protocolo externo (EGP):** entre diferentes sistemas autonomos:
	- O BGP é o principal protocolo externo da internet, construção de um grafo de conectividade ASs associa destino a atributos de caminho os sistemas anunciam sua propria rede de pares ou de terceiros dando enfase a caminhos mais curtos para montar a rota

# 11_camada_de_rede_nat:

Tradução dos endereços de rede => autera o endereço de destino ou de origem -> mantem uma tabela de tuplas (tradução) 

### 1. NAT e endereçamento privado:

criado para retardar o fim dos endereços IPv4 permintindo o use de endereços privados nas redes locais

-> ips privados nao sao unicos globalmente como o ip da porta localhost, nao sao roteaves na internet e devem ser descatados nas redes publicas

-> permite q os ips privados acesse a internet por meio de um endereço publico


### 2. Tipos de NAT:

- **Estatico (1:1):** mapea um ip privado para um publico
- **Dinamico:** utiliza pool endereços externos para mapear requisições internas => se o numero de ips privados for maior q o pool alguns ficaram sem acesso
- **Dinamico com tradução de portas (NAP/PAT):** mapeia multiplos endereços privados para um unico publico 

### 3. Encaminhamento de protas 

usa o tipo de maepamento 1:1 e portas externas para um endereço interno => para permitir q serviços mantidos em redes privadas sejam acessiveis externamente.

### 4. Carrier-Grade Nat (CGNAT):

larga escala pelo provedor de acesso q muitos usuarios compartilham o mesmo ip publico faxa especifica de endereços e traz dificuldades como inviabilização do encamiamento de portas e fica mais dificil de rastrear a origem de praticas ilicitas.

### 5. Pontos negativos e limtações:

quebra do modelo fim-a-fim: o nat mexe na comunicação entre o dipositivo e a internet
maior latencia
ruim para aplicações q precisam de atualização ao vivo
nao é uma aplicação focada em seguraça mesmo q ofereça uma certa privacidade não é ainda o ideial ja q ela é uma solução de roteamento/indereçamento

# 12_camada_de_rede_ipv6

### 1. necessidade:

como o IPv4 tava acabando criaram ele para poder comportar o numero de aparelhos

### 2. caracteristicas e vantagens do IPv6:

usa 128 bits tendo cerca de 340 undecilioes de possibilidades de endereços
- **Principais mudanças:** 
	- simplificação do cabeçalho para agilizar o processamento
			=> formado por 40 octetos faz com que seja processado mais rapido pelos roteadores, removeu uns capos q era do IPv4 para da mais velocidade e menos redundancia
				- campos matidos = versao, origem e destino -> 128bits
				- os q mudaram: 
						- classe de trafego: tipo do serviço
						- tamano do payload: tamanho total
						- limite de saltos: TTL
						- proximo cabeçalho: protocolo
				- os q sairam:
						- tamanho do cabeçalho
						- identificação, flags, deslocamento
						- fragmentação em rota
						- checksum do cabeçalho

	- melhoria da qualidade de serviço pelo campo classe de trafego
	- mecanismo de autenticação e privacidade
	- pode idenficiar fluxos de comunicação
	- **Cabeçalho de extensão:** inserido entre o cabeçalho IPv6 e a carga util de camada de transporte.
			- pode add funcionalidades opcionais 
			- pode ser colocados em serie


### 3 Formato e escrita do endereço

- **Estrutura:** 8 hexadecatetos (16 bits) escritos em hexadecimal cada grupo separado por : 
- **Regra de simplificação:** grupos consecutivos de zeros 0000 viram somente : e se forem no meio viram :: 

### 4. Tipos de endereços Unicast:

uma unica interface possua multiplos indereços simultaneamente

- **Link-local (FE80::/64):** config automatica e obrigatoria funciona somente na mesma sub-rede 
- **Unique-local (ULA - FC00::/7):** roteavel apenas internamente nas redes privadas como no ipv4
- **global unicast (GUA):** endereço roteavel na rede publica


**Lado do Cliente (Happy Eyeballs):** Para decidir qual versão usar, os clientes utilizam o algoritmo **Happy Eyeballs** (RFC 6555). Ele dispara conexões em paralelo para IPv4 e IPv6

- **Núcleo da Rede Simples:** A fragmentação é feita apenas na origem, e não mais nos roteadores intermediários (_hops_), agilizando o tráfego.
- **Eficiência Local:** O mecanismo de _broadcast_ foi substituído por **multicast**, o que economiza banda e processamento nas redes locais.
- **Desempenho de Roteamento:** O uso de um **cabeçalho de tamanho fixo** otimiza o processamento pelos roteadores.
- **Segurança Nativa:** Inclui mecanismos de autenticação e privacidade integrados através dos cabeçalhos de extensão



# 13_camada_de_enlace_1: 

L2 = entrega local de quadros entre dispositivos na mesma rede
L3 = entre a camada de rede e a camada fisica 
L1 = camada fisica

### 1. implementação e endereçamento:

- **Adaptadores de rede (NIC):** colocada no hardware, nas placas de rede identificador unico de 6bytes -> MAC
- **Alocação hierarquica:** os primeiros 24bits do MAC = fabricantes e os ultimso 24 bits identificam o adapitador
- **Protocolo ARP:** usa para achar o MAC quando se sabe apenas do IP

### 2. Tipos de enlaces e controle de acesso:

**Ponto-a-ponto:** para pares de dispositivos
**Brodcast:** para varios dispositivos
	- **Problemas de colisoes:** dois nos transmitindo ao mesmo tempo
	- **CSMA:** o negocio esta ouvindo antes de enviar se estiver livre ele envia se ta oculpado ele espera
	- **CSMA/CD:** para redes cabeadas ouve e fala oa mesmo tempo se tiver colisao ele para tudo e manda so um sinal de reforço

### 3. Enquadramento (Framing):

ela utilizar quadros
-> **Sentinelas de bits Stuffing:** usados padroes de bits para saber o inicio e o fim de um quadro se o sincronismo aparecer nos dados o emisor colocar um bit 0 extra

### 4. Equipamentos de rede

hubs e switches 


# 14_tecnologias_de_redes_locais


### 1. padrao IEEE 802 camada de enlace

divide a subcamada em duas 

- LLC: interconexão entre tecnologias disferentes e permite multiplos protocolos 
- MAC: montar o quadro e as regras de gerenciamento

### 2. IEEE 802.3 

para redes cabeadas

- acesso ao meio: para gerenciar tramissao em topologias de barramento
- permite compatibilidade de padroes novos e antigos

### 3. IEEE 8022.11 

para redes sem fio

- BSS infraestruturada ou ad hoc
- ESS varias BSS conectadas em sistrma distribuido

### 4. problemas especificos de redes sem fio

- estação oculta: quando uma estação n ve a outra concorrente por esta fora do seu lance fisico => colisoes entre as redes 
- Problemas de estação exposta: o inverso uma falsa concorrente e n quer enviar o sinal mesmo q o receptor esteja livre para receber
