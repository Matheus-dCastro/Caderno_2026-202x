metodos para analizar:

- `ObterPendenciasEletronicasGlobalAsync`
    
- `ObterPendenciasEletronicasUsuarioAsync`
    
- `ObterPendenciasEletronicasInstanciaAsync`
    
- `ObterPendenciasEletronicasJariAsync

=> pouca diferença entre filtros e condições.

Termo de filtro de busca inicial é padrao para os 4 metodos

todo contem o mesto estilo de filto inicial 
        var baseQuery = context.VwInfDadosRecursoDefesas.AsQueryable();

  

        if (!string.IsNullOrWhiteSpace(request.TermoBusca))

        {

            var termo = request.TermoBusca.ToUpper().Trim();

            bool isNumero = int.TryParse(termo, out int numeroProc);

  

            baseQuery = baseQuery.Where(rd => (rd.Placa != null && rd.Placa.ToUpper().Contains(termo))

                                           || (rd.NumeroAutoInfracao != null && rd.NumeroAutoInfracao.ToUpper().Contains(termo))

                                           || (isNumero && rd.NumeroProcesso == numeroProc));

        }
       