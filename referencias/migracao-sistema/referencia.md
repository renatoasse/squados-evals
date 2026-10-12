{
  "tarefas": [
    {
      "id": "t1",
      "nome": "Levantamento dos processos",
      "inicio": 0,
      "duracao": 6,
      "depende_de": [],
      "responsavel": "Rafael Costa",
      "custo": 0
    },
    {
      "id": "t2",
      "nome": "Mapeamento do banco atual",
      "inicio": 0,
      "duracao": 6,
      "depende_de": [],
      "responsavel": "Marina Lopes",
      "custo": 0
    },
    {
      "id": "t3",
      "nome": "Configuração do novo ERP",
      "inicio": 6,
      "duracao": 15,
      "depende_de": ["t1"],
      "responsavel": "Sofia Martins",
      "custo": 0
    },
    {
      "id": "t4",
      "nome": "Script de migração dos dados",
      "inicio": 6,
      "duracao": 12,
      "depende_de": ["t2"],
      "responsavel": "Marina Lopes",
      "custo": 0
    },
    {
      "id": "t5",
      "nome": "Integrações com banco e loja virtual",
      "inicio": 21,
      "duracao": 10,
      "depende_de": ["t3"],
      "responsavel": "Rafael Costa",
      "custo": 0
    },
    {
      "id": "t6",
      "nome": "Carga de teste",
      "inicio": 21,
      "duracao": 5,
      "depende_de": ["t4", "t3"],
      "responsavel": "Marina Lopes",
      "custo": 0
    },
    {
      "id": "t7",
      "nome": "Validação dos dados migrados",
      "inicio": 26,
      "duracao": 6,
      "depende_de": ["t6"],
      "responsavel": "Marina Lopes",
      "custo": 0
    },
    {
      "id": "t8",
      "nome": "Treinamento dos usuários",
      "inicio": 21,
      "duracao": 8,
      "depende_de": ["t3"],
      "responsavel": "Tiago Nunes",
      "custo": 0
    },
    {
      "id": "t9",
      "nome": "Corte para o novo ERP",
      "inicio": 55,
      "duracao": 2,
      "depende_de": ["t7", "t8", "t5"],
      "responsavel": "Marina Lopes",
      "custo": 0
    },
    {
      "id": "t10",
      "nome": "Acompanhamento pós-corte",
      "inicio": 57,
      "duracao": 3,
      "depende_de": ["t9"],
      "responsavel": "Sofia Martins",
      "custo": 0
    }
  ]
}
