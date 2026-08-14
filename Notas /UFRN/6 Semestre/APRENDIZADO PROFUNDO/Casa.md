# Pytorch:

como usar:
tensor => generalização de um escalar -> ordem 0 escalar, ordem 1 vetor, ordem 2 matriz ou seja um conjunto de matrizes 



``` python

import torch # preciso importa essas como principal antes de trabalhar com as redes
import numpay as np # para fazer matrizes e operaçoes nos dados

escalar = torch.tensor(25) # cria uma variavel tensor q ndim de 0 a 2
vetor = torch.tensor([1,2]) # torch.ndim => no numero de imenções do tensor
matriz torch.tensor([1,2],[1,2])




```

comando basicos de preenchimento de tensor

- `torch.zeros(shape)` e `torch.ones(shape)`: tensores preenchidos com 0 e com 1.

- `torch.rand(shape)`: valores de uma distribuição uniforme em $[0, 1)$.

- `torch.randn(shape)`: valores de uma distribuição normal padrão, média 0 e variância 1.

- `torch.arange(start, end, step)`: valores em um intervalo.

- `torch.linspace(start, end, steps)`: `steps` valores igualmente espaçados entre `start` e `end`.

- `torch.eye(n)`: matriz identidade de ordem $n$.


Usa geralmente a norma euclidiana como paramentro -> tira a raiz
				   manhattan mesma conta so q sem raiz e soma os valores absolutos da sequancia ou seja cada valor passar por um modulo

