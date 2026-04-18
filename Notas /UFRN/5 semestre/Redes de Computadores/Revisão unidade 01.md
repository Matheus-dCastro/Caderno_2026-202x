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

