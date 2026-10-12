{
  "tarefas": [
    {
      "id": "t1",
      "nome": "Protótipo das telas",
      "inicio": 0,
      "duracao": 6,
      "depende_de": [],
      "responsavel": "Carla Mendes",
      "custo": 0
    },
    {
      "id": "t2",
      "nome": "Back-end da API",
      "inicio": 0,
      "duracao": 12,
      "depende_de": [],
      "responsavel": "Ana Ribeiro",
      "custo": 0
    },
    {
      "id": "t3",
      "nome": "Telas do app",
      "inicio": 6,
      "duracao": 14,
      "depende_de": ["t1"],
      "responsavel": "Bruno Tavares",
      "custo": 0
    },
    {
      "id": "t4",
      "nome": "Integração de pagamentos",
      "inicio": 12,
      "duracao": 6,
      "depende_de": ["t2"],
      "responsavel": "Ana Ribeiro",
      "custo": 2500
    },
    {
      "id": "t5",
      "nome": "Testes do app",
      "inicio": 20,
      "duracao": 5,
      "depende_de": ["t3", "t4"],
      "responsavel": "Ana Ribeiro",
      "custo": 0
    },
    {
      "id": "t6",
      "nome": "Material da loja",
      "inicio": 6,
      "duracao": 4,
      "depende_de": ["t1"],
      "responsavel": "Carla Mendes",
      "custo": 0
    },
    {
      "id": "t7",
      "nome": "Publicação na loja",
      "inicio": 25,
      "duracao": 3,
      "depende_de": ["t5", "t6"],
      "responsavel": "Bruno Tavares",
      "custo": 500
    },
    {
      "id": "t8",
      "nome": "Landing page",
      "inicio": 10,
      "duracao": 5,
      "depende_de": ["t1"],
      "responsavel": "Carla Mendes",
      "custo": 1200
    },
    {
      "id": "t9",
      "nome": "Plano de comunicação",
      "inicio": 0,
      "duracao": 4,
      "depende_de": [],
      "responsavel": "Diego Arruda",
      "custo": 0
    },
    {
      "id": "t10",
      "nome": "Campanha de lançamento",
      "inicio": 15,
      "duracao": 8,
      "depende_de": ["t8", "t9"],
      "responsavel": "Diego Arruda",
      "custo": 15000
    }
  ]
}
