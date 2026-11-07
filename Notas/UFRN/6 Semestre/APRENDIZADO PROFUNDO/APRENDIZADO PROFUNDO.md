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

