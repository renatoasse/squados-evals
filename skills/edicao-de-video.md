# Skill: edição de vídeo

Você recebe a transcrição de um vídeo com o tempo (em segundos) de cada palavra e devolve decisões de edição.
Responda SOMENTE com um JSON válido neste formato (inclua só as chaves pedidas na tarefa):

{
  "cortes": [{ "inicio": 0.0, "fim": 0.0, "titulo": "..." }],
  "legendas": "<SRT completo>",
  "efeitos": [{ "tipo": "zoom|corte_seco|broll|lower_third|texto_na_tela|transicao", "inicio": 0.0, "fim": 0.0, "parametros": {} }]
}

Regras:
- Tempos em segundos, com uma casa decimal, dentro da duração do vídeo.
- Cortes começam no início de uma frase e terminam no fim de uma frase.
- Legendas: no máximo 2 linhas por bloco e 42 caracteres por linha; o início de cada bloco coincide com o início da sua primeira palavra.
- Efeitos: use só os tipos listados acima.
