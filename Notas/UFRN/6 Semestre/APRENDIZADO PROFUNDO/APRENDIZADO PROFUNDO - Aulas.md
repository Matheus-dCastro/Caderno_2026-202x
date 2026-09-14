Como formar as informações atravez dos dados e saber identificar as coisas;
-> Abstrair principal causas;sintonização

task, performace, experience


- separação treino validação test implanta sintonização 

Representation learning;

# Aula do dia 12/08

### Revisão e intro a pytcho

``` python

s = torch.tensor()
s.ndin # informa o numeroa da dimencoes do tensor

randn isso faz com que use uma gausiana com devio padrao igual 0

o mean n pode ser acessado pelo type int diratamente quando estamos trabalhando com tensor apenas pelo tipo float

view serve para mudar o formato mas n mudar na memoria o var q passei

x = torch.arange(12) # vetor com 12 elementos
passar o -1 no resheape ele competa as dimençoes do vetor dividindo pelo outro numero q eu passei




```

# Aula 03

### Revisao de calculo e algebra + probabilidade:

Probabilidade +> determinismo e incerteza linguagem do q nao sabemos -> yugioh

**Frenquntista:** probabilidade é a frequencia realtiva do evento sobre a repetição do evento.
**Bayesiana:** sobre cresça, probabilidade é o grau de crença sobre o evento, daod o conhecimento disponivel.

revisao da materia de tetso
revisao de calculo

vetores sao representações de data point(as coordenadas sao os valores de cada feture)

Como o numero é retornado define ja a relação entre dois vetores: 

**positivo:** essa projeção as direções são semelhantes e se colocar um sobre o outro tem o mesmo sentido
**negativo:** direções opostas, projeção aponta para o sentido aposto
**ZERO:** são ortogonais nenhuma parte de um é projetada no outro 


# Aula 04:

Modelos lineares: deve satisfazer duas propriedades:
	- A transformação da soma é igual a soma das transformações
	- escalar a entrada escala proporcionalmente a saída
	=> o modelo supoem que a saida é uma combinação linear das entrada mais um deslocamento
		os pesos dizem o quanto aquela feture pesa(é significante) para formar aquela saida
		o vies desloca a saida quando todos os pesos são nulos
		a superfice da resposta é sempre um hiperplano no espaço das fetures
		A **Fronteira** é sempre d-1 dimensoes sendo d o numero de dimenções(caracteristicas) dos dados
		-> na pre-ativação da função é onde a parte linear e unico lugar em que vai aparecer
		-> na função é onde add a parte não linear do modelo e é aqui q descide qual tipo de saida o modelo irá produzir.
	
Gradiente descendente extocatico
Regressao logistica

Definição de neuronio => modelo linear com uma nao lineariedade no final com pesos, para produzir a saida


# Redes Neurais:

pre-ativação -> ativação => determina a imagem de saida

### Limites dos modelos lineares:

deformar o espaço para achar um hiperplano q separe perfeitamente ou quase os dados
cada peso de cada neuronio é idependente e cada peso por cada neuronio cria uma nova representação da entrada

+> introduzir n linearidade
sigmoid = para saida probabilistica
tahh = para saidas de ecopo de -1 a 1
relu = para saidas lineares -> zera o lado negativo e deixa o positivo intacta 


#### Saturação e Gradiente:

satuação: pre-ativação o grandiente a derivada tende a zero

### Teorema do aproximador universal

pode ser continua e descontinua contado q esteja em um espaço medio compacto

# Aula do dia 31/08

Revisão de tensor inicial

Revisar OO, revisar tensorflow, revisar estrutura de camadas de um neural network,

# Aula do dia 14/09
### Estabilidade e Treinamento:

