
## Slide 07:

Todas as ativações sao realizadas por meio de camadas divididas em 3 tipos:

Camada de entrada
Camadas internas HIDER
Camada de saida

pelo fator no linear add entres as matrizes lineares conseguimos assim aumentar a variancia entres as layer internas e dessa forma melhorar as responstas dos modelos alem claro de outras tecnicas de variação.

-> inialização xavier tecnica q define os pesos antes de começar o treinamento, ajustando a variancia => ela inicia os pesos de forma aleatora preservando a variancia mais proxima a 1 de forma q o modelo n carrege grandes valores ou muito pequenos tudo depende do numero de entradas q estamos recebendo naquele momento para manter o sinal estavel.

+> concentra de forma que faz manter mais proximo a uma distribuição central.


-> Como ela atua junto geralmente da ReLu fazendo praticamento metade das entradas zerarem (numeros negativos) a inicialização de HE dobra a variancia em relaçao aos dados q n foram zerados compensando a perca das entradas q foram zeradas 


## Processo de Normalização:

nesse processo estamos tentando por escalas distintas de dados em uma mesma escala

a media é feita uma vez e depois é usado para tentar inferir e prever os nos dados de teste (nunca é feito um recalculo)

Oq esse processo faz é colocar a meida a 0 e a variancia a 1 

O processo de Batch Normalization infere em aumentar a taxa de aprendizado sem fazer o modelo convergir estabilizando o gradiente tornando o mdoelo menso dependete da inicialização (sorteio dos pesos)

### Learning rate constante

seria como se fossem agendadores no apredizado da maquina, 
**step decay:** reduz a traxa de aprender em intervalos fixos -> quando orçamento fixo e conhecido de epocas => ajusta o fator de reduçao e o intervalo das epocas so decai esse passo de aprender quando o erro para de reduzir

**Explonential dacay** funciona da mesma forma da de cima porem de maneira mais suave ne fazendo um decaimento na taxa de aprender de forma abrupta 

**Cosine annealing** esse aqui no lugar de se via exponencial vai fazendo um decaimento na taxa de aprendizado usando uma func cosseno => padroa mais moderno hoje para visao 

**Warmup** ela da um passo grande em aprender muito no inicio e tenta balancear essa taxa de aprender no decorrer q se mantenha na mesma de q quando iniciou. ela tenta segurar a intenreçao inical

 
## Slide 08:

Erro impirico: media da funçao de perca da loss sobre a amostra do conjunto 
-> n garante q o molode n tenha ouverfinting 

os mesmo atributos estao fazendo intersecsao entre classes diferentes 
