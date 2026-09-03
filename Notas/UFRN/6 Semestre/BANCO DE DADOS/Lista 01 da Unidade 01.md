# 1. Um índice novo em produção

*Um sistema de vendas já em produção tem dezenas de consultas SQL escritas contra a tabela*
*Pedidos. O time cria um índice na coluna Status, muito usada em filtros WHERE, sem tocar em*
*nenhuma consulta existente. Quantas dessas consultas precisam ser reescritas para passar a*
*aproveitar o índice novo?* 

<font color="#00b050">a) Nenhuma: o otimizador do SGBD passa a usá-lo sozinho, sem intervenção do programador.</font>
b) Todas as que filtram por Status, porque o plano de execução delas precisa ser reescrito à mão.
c) Só as que fazem JOIN envolvendo a tabela Pedidos.
d) Todas, porque o caminho de acesso ao dado mudou e cada consulta precisa apontar para ele.

-- Como em um modelo em modelo relacional o que é definido é oq deve ser retornado e não como é feita a consulta, então uma modificação fisica não altera a logica

