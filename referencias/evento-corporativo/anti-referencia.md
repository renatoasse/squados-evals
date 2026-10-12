{
  "tarefas": [
    {
      "id": "t1",
      "nome": "Reserva do local",
      "inicio": 0,
      "duracao": 3,
      "depende_de": [],
      "responsavel": "Larissa Pires",
      "custo": 30000
    },
    {
      "id": "t2",
      "nome": "Contratação do buffet",
      "inicio": 0,
      "duracao": 4,
      "depende_de": [],
      "responsavel": "Paulo Sena",
      "custo": 57000
    },
    {
      "id": "t3",
      "nome": "Contratação de som e luz",
      "inicio": 2,
      "duracao": 3,
      "depende_de": [],
      "responsavel": "Paulo Sena",
      "custo": 12000
    },
    {
      "id": "t4",
      "nome": "Identidade visual do evento",
      "inicio": 0,
      "duracao": 4,
      "depende_de": [],
      "responsavel": "Renata Lima",
      "custo": 6000
    },
    {
      "id": "t5",
      "nome": "Convites e inscrições",
      "inicio": 2,
      "duracao": 5,
      "depende_de": ["t1", "t4"],
      "responsavel": "Renata Lima",
      "custo": 3000
    },
    {
      "id": "t6",
      "nome": "Brindes",
      "inicio": 7,
      "duracao": 5,
      "depende_de": ["t4"],
      "responsavel": "Paulo Sena",
      "custo": 12000
    },
    {
      "id": "t7",
      "nome": "Credenciamento",
      "inicio": 9,
      "duracao": 3,
      "depende_de": ["t5"],
      "responsavel": "Larissa Pires",
      "custo": 2400
    },
    {
      "id": "t8",
      "nome": "Roteiro e palestrantes",
      "inicio": 8,
      "duracao": 6,
      "depende_de": [],
      "responsavel": "Larissa Pires",
      "custo": 9000
    },
    {
      "id": "t10",
      "nome": "Realização do evento",
      "inicio": 30,
      "duracao": 1,
      "depende_de": ["t2", "t6", "t7", "t8"],
      "responsavel": "Larissa Pires",
      "custo": 0
    }
  ]
}
