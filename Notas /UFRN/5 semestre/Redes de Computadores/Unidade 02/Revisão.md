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

