# SquadOS Evals

Materiais públicos de avaliação de modelos em trabalho do dia a dia, em português: **32 testes em 12 categorias**.

Este repositório documenta os testes; não distribui a aplicação, o motor nem uma CLI de execução.

| Categoria | Testes |
|---|---:|
| [Copywriting](categorias/copywriting/README.md) | 3 |
| [Artigos técnicos](categorias/artigos-tecnicos/README.md) | 3 |
| [Resumo de documentos e atas](categorias/resumos-e-atas/README.md) | 2 |
| [Análise de planilhas e dados](categorias/planilhas-e-dados/README.md) | 2 |
| [Pesquisa com fontes](categorias/pesquisa-com-fontes/README.md) | 2 |
| [Revisão de contratos](categorias/revisao-de-contratos/README.md) | 2 |
| [Atendimento de suporte](categorias/suporte/README.md) | 3 |
| [Atendimento comercial e vendas](categorias/comercial-e-vendas/README.md) | 3 |
| [Tarefa de vários passos com ferramentas](categorias/ferramentas-varios-passos/README.md) | 3 |
| [Planejamento de tarefa longa](categorias/planejamento/README.md) | 3 |
| [Edição de vídeo](categorias/edicao-de-video/README.md) | 3 |
| [Decisões](categorias/decisoes/README.md) | 3 |

Consulte a [metodologia](metodologia/README.md), os [juízes](metodologia/juizes.json) e os [schemas de ferramentas](metodologia/ferramentas.json). Cada tarefa tem JSON documental com entradas, critérios, pesos, métricas e perguntas de julgamento. Os caminhos de entrada são relativos à raiz deste repositório. As referências e anti-referências estão em `referencias/<id>/`.

O template `prompt.txt` usa as variáveis documentadas em cada tarefa. As datas em `metadata.publicada` são metadados do catálogo de origem, não evidência de publicação ou execução nessa data.

A versão dos materiais é identificada pelo commit público e pelo [manifesto SHA-256](manifesto.json). Os arquivos são snapshots gerados a partir da fonte privada. Não há resultados de ranking ou alegação de desempenho nesta edição.

Referências de transparência: [LiveBench](https://github.com/LiveBench/LiveBench), [Simple Evals](https://github.com/openai/simple-evals) e [AlpacaEval](https://github.com/tatsu-lab/alpaca_eval). Esses projetos também disponibilizam código; aqui o escopo é documental.
