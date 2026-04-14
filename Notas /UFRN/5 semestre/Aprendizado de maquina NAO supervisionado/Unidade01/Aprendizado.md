[[Aprendizado de maquina NAO supervisionado]]

[Caderno de Fundamentos - Unidade 01](file:///home/alomyr/Projetos/Apredizado-de-maquina-NAO-supervisonado/unidade_01/01%20-%20Fundamentals.ipynb)

usamos vetores para representar dados e cada dimensado do vetor significa um feature do dado, matrizes servem para representar varios dados de uma vez so no espaço vetorial

Distancia e a diferenca entre dois vetores ou dois dados similaridade mede sua origem (angulo) independente de seu tamanho

Centroides sao os pontos medios de todos os dados q fazem parte daquel grupo ou seja cluster 


K-means: busca por distancia em minimizar a variancia entres os pontos para formar clusters o valor de k deve ser passado ou descoberto atravez do metodo do cotovelo e sempre q add um novo atualizar o valor do centroide repete ate todos os pontos estarem em um cluster 

a preparacao de dados segue a mesma de aprendizado supervisionado


k-menas: pontos aleatorios para inicializar (deve passar a semente para q seja sempre parecido o valor de inicio apenas variando o k)
atribui esse ponto aleatorio como centroide e pega o vizinho mais proximo dele = imagens 

# notebook 03

hierarquizacao de clusters:

pode ser feito apartit de 4 formas

single : acada dois clusters com menor distancia e une eles : alongados sofre do efeito corrente
avarange :feito apartir da media das distancia entre todos os pontos dos clusters analizado : meio termo entre single e complete
ward: soma dos quadrados das diantacia dos pontos para o centroide do par de clusters : miniza a variancia 
complete: usa a distancia mais distante entre os clusters mais compactos e esfericos


# notebok 04

DBSCAN baseado na desnidade para formar um cluster

n precisa passar o k mas preciso passar o numero minimo de pontos vizinhos para q ele seja cosiderado parte do cluster q esta formado 

so para de considera se n consegue mais pegar pontos para o cluster 

silhoette score: fica entre -1 a +1 foca em media dos todos os pontos dos dois clusters (mais proximo) e ve qual oq sai se sair mais de +1 ta bom se sair menos de -1 ta ruim 

davies-bouldin (DBI)

pela simelaridade (angulo do vetor vamos falar assim)
mede a dispersao dos pontos do cluster quando mais disperso em comparacao ao cluster vizinho mais proximo ta ruim
divide pela distancia entre eles (similaridade)

dunn index: 

foca no pior caso (similar ao de cima) foca na maior distancia e menor dispersao (tamanho do maior cluster do par q esta sendo analizado)

basicamente 

SS: quanto maior melhor
DBI: quanto menor melhor
DI: quanto maior melhor

