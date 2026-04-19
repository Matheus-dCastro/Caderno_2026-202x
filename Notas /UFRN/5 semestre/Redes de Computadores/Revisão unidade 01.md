# Historico e cenario atual das redes de computadores



Toda Rede de computadores sao os
	- dispsitivos/sistemas finais da redes => pc e afins
	- Equipamentos de comunicacao => rotadores e afins
	- enlace de dados => ligacoes entre dispositivos



### Serviço:

infra da aplicacao/servico
sistemas finais (set de aplicacoes e servicos) oferece interface de programacao (api) => set de regras do sistema para pode enviar e receber os dados define como sera feito o envio das infos pela internt

### Protocolos

definem a forma com oq sera o envio e recebimento entre dois ou mais dispostivos de informacoes no sistema 

##### Oq e um protocolo

execultado no hardware so sistema de dois pcs como sera a troca de infos entes eles

de congestionamento: taxa de transferencia dos dados

de roteamento: definem as rotas de ida e vinda

# Historia das redes de computadores

inicio na decada de 60 (1960) um dos primeiros pcs de pacotes foram o leonardo kleinrock

surgiu na arpanet em 1970, 1972 cerca de 15 nos
<mark style="background:#fff88f">arpanet</mark> era fechada e isolada => ainda em 70 surgiram novas redes independentes de comutacao de pacotes

sobre o patrocinio da <mark style="background:#fff88f">DARPA</mark> cria uma rede de redes => internetting para descrever isso

principal evento em 90 foi o surgimento do WWW => World Wide Web 

## No Brasil:

<mark style="background:#fdbfff">87/88 - LNCC e FAPESP se conectaram a uma instituiçao no EUA</mark>
em 88 UFRJ link com a UCLA
em 90 O MCT cria a iniciativa de RNP 
	- implementar de forma nacional a internt
	- 95 a RNP se restria somente a comunidade de educacao e pesquisa

-> natal tinha uma das mais velozes conecxoes da rede naquela epoca

## o impulso das novas tecnologias

reducao de tamanho aumento no consumo de quipamentos inteligentes
internet das coisas fica cada mais emergente
- IoT
- cloud
- SDN
- NFV


# 4 problemas fundamentais

- 1 <mark style="background:#40a9ff">local e destino</mark> => nomeacao e enderecamento
- 2 <mark style="background:#40a9ff">rotemento</mark> => caminho para o destino
- 3 <mark style="background:#40a9ff">encamihamento </mark>=> enviar sem perdas para o destino
- 4 <mark style="background:#40a9ff">confiar</mark> => falhas, perdas, e info fakes


ponto de vista **fim-a-fim**

host => onde o endereco esta localizado -> host de destino
seu endereco pode mudar mas o nome n pode mudar

DNS => mapeamos nomes para endereços por isso endereços podem mudar mas nomes não mudam

## Roteamento

<mark style="background:#fdbfff">Tabela de roteamento</mark>: determinar o link de saida para o pacote q sera enviado
sabe atravez dos <font color="#00b050">protolos de roteamento</font> => **Distribuido**: nenhum roteador conhece a rede por completo
faz calculos em cima da topologia guardar informacoes de encaminhamento para cada roteador
	pacote veio de x => va para linky se saida e seu Ln 

### Encaminhamento

pacote chega as filas de entrada => divide cada fila de entrada em varias filas de saida (virtual) => saida virtual = link de saida => envia 

todo pacote requer <mark style="background:#ff4d4f">cabecalho</mark>: 
	destino, origem, dados 
-> atraso de processamento: cada router linda de onde colocar o pacote => verifica o cabecalho
-> // de enfileiramento: vez da fila, transito da rede => quanto mais transito de rede -> perda de pacotes

### Confia ai pai?







Pilha de rede: proprio SO gerencia => qualquer app q usar recurso de rede abre o socket e todo socket tem uma porta e essa porta e o cpf para onde vai mandar ou receber a info da rede pelo pc => **tudo para no cabecalho**

# responsabilidades

rede: host a host entrega pacotes
pilha(SO): pega o pacote e enfia no socket certo (pela porta dele)
Aplicacoes: envia e recebe pacotes, entende o conteudo e carrega o corpo do pacote 

# Metricas 

Banda = numero de bits enviados 
latencia: tempo para as coisas se mexerem de um link para o outro


#### DELAY:

link:
	transmicao: tempo de enviar o pacote
	propagacao: quanto tempo leva para mover o bit
Matriz de trafico:
	Processamento:
	enfileiramento:



![[Pasted image 20260417212022.png]]


# Mudalaridade 

se a tarefa esta bem definida e possivel substituir esse componente por qualquer implementacao q realize o mesmo efeito 

cada modulo de um sistema tem um interface bme definida => flexibilidade em implementar

encapsular funcinalidades

em redes => host, esquipamentos de rede, etc...

Modelo em camadas, principio fim-a-fim


Modelo: TCP/IP

<mark style="background:#ff4d4f">aplicacao</mark>   <mark style="background:#d4b106">L7</mark>  navegadores, cliente de email etc
entrega de dados <mark style="background:#ff4d4f">transport</mark> <mark style="background:#d4b106">L4</mark> SO
entrega de pacotes globais <mark style="background:#ff4d4f">rede</mark> <mark style="background:#d4b106">L3</mark> SO
estrega de pacotes locais <mark style="background:#ff4d4f">enlace</mark> <mark style="background:#d4b106">L2</mark> hardware
estrega fisica <mark style="background:#ff4d4f">fisica</mark> <mark style="background:#d4b106">L1</mark> hardware

camada de N faz somente contato com N-1 e N+1 



![[Pasted image 20260417213117.png]]

cada cama a cima de outra e sustentada pela de baixo 

quando a multiplas versoes de camada a os componentes escolhem o protocolo automticamente
IP apenas unifica tudo

modelo de camadas tras evolucoes principalmente nas macadas exterenas

host: mantem a aplicacao e seus niveis receber/enviar
roteadores propagam a informacao de forma confiavel para o globo de um host para outro 


switches trabalham somente local fazendo o mesmo q um roteador, roteador faz a entraga global 

# Topologias de redes

## Fluxo de dados:

### Simplex: 
sentido unico
### half-duplex:
um sentido por vez

### Flul-duplex:
os dois sentido ao mesmo tempo

## Classificacao:

poto-a-ponto: p2p, set de conexoes entre pares de pcs, link dedicada por par 

Multiponto: um envia varios recebem mas de dois compartilham um link unico 
espacialmente -> todo mundo junto
tempo -> um por vez

## Topologia de rede:

logica: define com o hardware e usado pelo host para envio de dados
Fisica: layout dos cabos
- Barramento => enfileirada em um unico cabo -> um por vez para falar e todo o resto so escuta, economica e facil de add, lenta, isolamento e dificil, falha um falha tudo
- Estrala => com um hub -> ponto a ponto centralizada e facil de isolar bos, falha um so falha ele simpls de add, so da merda se falhar o centro
- Anel => em forma circular -> ponto a ponto fechada sobre si mesma, melhor quando tem poucos nos e rapida, facil de add, mas cara, para funcionar os pcs tem q esta ligados para q isso funcione, um pc com bo 
- Malha => toda fechada com um pentagrama no centro (cruz credo) -> ponto a ponto, varios caminhos para chegar num unico ponto, privacidade, mas complexa, mas cara

## Classificacao: 

Pan: redes pessoais, ate 10m, bt zigbee
Lan: redes de area local privadas, wifi, ethernet
Man: redes de acesso para interconexa de lans -> cidades, telefonias, dados operado sobre cabos (TV), provedores
Wan: conecta cidades, cara, satelites/enlaces de fibra ou microondas


## Arquitetura de comunicacao

![[Pasted image 20260418160114.png]]


### TCP/IP: 

Modelo OSI:

<mark style="background:#d4b106">Aplicacao:</mark>
	comunicacao entre programas (process) e seis hosts
	full-duplex entre process, interagem com o usuario
	-> tipo da mensagem
	-> sintaxe 
	-> semantica
	-> quem fala e quando fala
	
<mark style="background:#d4b106">Apresentacao:</mark>
	mostra os dados em um formato cagando para arquitetura dos sistemas q fazem parte da resenha
	semantica das transmisoes

<mark style="background:#d4b106">Sessao:</mark>
	estabelece comunicaca entre process em maquinas distintas
	cria e mantem a conversa entre origem e destino (Jogos)
	mantem,pausa ou reinicia

### Arquitetura cliente-servidor:

<mark style="background:#9254de">cliente:</mark> puxa papo, so fala com o serve diretamente, intermitente (n funciona de forma continua).
<mark style="background:#9254de">servidor:</mark> responde quando o cliente fala, host e servicos sempre on, ip permanente

### Arquitetura peer-to-peer:

comunicacao direta entre os hosts, pares (2) fica megando entre cliente e servidor, tambem e intermitente, pode crescer rapido essa suruba (Torrent) => quanto mais melhor

### Arquitetura Hibrida:

junta o melhor dos dois mundo, se conecta a plataforma la ela resolve as coisas mas vc e a outra pessoa se falam diretamente ou pegam os arquivo um do outro

### A comunicacao entre os processos:
socktes de envio, cada um esta preso a um unico processo com isso se sabe para onde o dado vai para o processo certo =>
usa o endereso ip do processo para saber o sockets 


![[Pasted image 20260418162022.png]]


# Camada de transporte - GERAL

Permite aplicacoes usarem a camada de rede
camada 01 da fim a fim

varias coisas penetrando ao mesmo tempo 
possuem 16 bit e sao organizadas pela RFC 6335:

IANA:
0-1023: portas do sistema
1024-49151: portas de usuario
49152-65535 portas dinamicas

## Sockets:

multiplexacao -> varias comunicacoes simultaneas de varias aplicacoes

cliente => ip do cliente + porta dinamica
servidor => ip do servidor + porta de sistema +> bind e listen
	bind: vinculace
	listen: ta na espera 8=D

#### Orientado a conexao: 
entrega confiavel,acordo entre as partes fluxo de receber e enviar


#### NAO Orientado a conexao: 

entrega confiavel, nao te acordo do fluxo, nao garante vc receber

## Protocolos
UDP: usado para jogos e videochat, n garante entregar os dados
TCP: garante entrega, navegacao web, email e transferencias
RTP: serve para transportar dados em tempo real de audio, videos, videoconferencias garante a entrega
RTCP: auxilia o RTP, da p feedback das coisas monitora e te mostra como q ta as coisas


# TCP:

RFC - 793

orientado a conexao com entrega confiavel, tem mecanismo para recuperar dados ACK
implemta mecanismos de fluxo de dados todas as mensagens sao passadas na ordem q foram enviadas e na speed q maquina destino aguenta

### Cabecalho:

portas => id para saber a origem e o destino
numero de sequencia => lugar do primeiro octeto (dados) do processo
ACK => numero de confirmacao, proximo octeto, reconhecendo todos de valor inferior

size: 32 bit palavras, 
windows size: quantos octetos o caba q mandou esta pronto para receber antes do ACK 


### Bit de codigo 
=> <mark style="background:#ff4d4f">flags</mark> operacoes de protocolo de TCP:

SYN: estabelece a conexao (sincroniza as n sequencias)
ACK: numero de confirmacao n-1 octetos (+)
FIN: sinaliza de forma ordenada o fim da conexao
RST: operacao de reset
PSH: buffet q entrega os dados imediato para camada de cima
URG: indica q tem dados urgentes
checksum: (cabecalho + dados) integridade TCP
ponteiro: indica onde tem URG

opcoes: infos de negocio de capacidade (origem/destino)
Para pseudo-cabecalho se utilisa => checksum

PRECISA estabelecer conecxao entre cliente e servido para o tcp funcionar

## Controle de erro - go-back-n

se tiver um errado ele forca o caba q enviou mandar tudo de novo => manda/recebe tudo de uma vez mas se tiver algo errado ele pega e pede tudo de novo do zero

### reconhecimento explicito
quando o caba q recebe n tem dados para mandar de volta -> nao tem dados de sequencia

piggyback: envia um segmento para enviar dados no sentido oposto aproveita melhor a banda


## Janela deslizante:

otimiza o envio de ACKs, o caba q recebe usa um buffer, onde o numero de segmentos podem ser recebidos sem precisar ser validados um por um de forma imediata, 

so e enviado a quantidade de segmentos q o caba q recebe suporta

quanto ta no tamanho da janela e nao recebeu os AKCs, o caba q mandou fica no estado de espera ate receber os AKC,

o caba para de mandar dados ate receber o AKCs do outro

## Flags, push e urg:

alguns ai pode pedir para q os dados sejam enviados diretamente a uma camada x superior sem poder esperar q a o buff seja peenchido completamente => entrega de dados forcado -> PSH=1

a aplicacao pode precisar q seja enviados x dados urgentes e n pode esperar o fim do fluxo, => entrega urgente -> urg=1



# UDP:

RFC 768

esse NAO e orientado a conexao e nao e confiavel 

nao usa mensagens de reconhecimento ACK
nao ordenar as mesagnes passou passou 

pode perder as mensagens, duplicalas, nao receber na ordem, e podem ser mais rapidas do q a maquina aguenta

vai ate 16bit

somente checa o destino do segmento udp recebido
calulo do checksum = 0 e o calculo e usando o pseudo
mesma coisa do TCP so q ele e removido depois de fazer as contas do checksum 

concatena o pseudo, caso tenha um octeto de zeros tambem e concatenado para vire um numero multiplo de 16bit

#### Calculo do checksum => slide checksum esta aqui tambem

preenche com zeros os campos do checksum com zeros
divide o datagrama em pedacos de 16bit

realiza a soma binaria dos pedacos e faz o complemento de 1 do resultado

### Transmissao:

remove o pseudo e o pad
atualiza os campos de checksum
envia o datagrama UDP

slide 07 e revisao da parte 06

