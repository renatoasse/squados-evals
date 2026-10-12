Avalia sim/não, satisfação do atendimento e categorias com 30 casos em português e gabaritos fixos. Cada teste reúne dez casos numa requisição Decisions, repetida três vezes.

Os gabaritos estão nas assertions YAML e não são enviados à API. As referências mostram respostas ideais; anti-referências representam respostas opostas. Não há juízes LLM.

Sim/não mede cancelamento atual da assinatura: intenção indireta conta, mas negação, condição futura, pedido de instruções e cancelamento de outra coisa não contam. São cinco positivos e cinco negativos. Nota = 100 × (1 − (probabilidade − esperado)²); acerto usa corte 0,5.

Satisfação usa escala 0 muito insatisfeito, 1 insatisfeito, 2 neutro, 3 satisfeito, 4 muito satisfeito. Avalia o atendimento, não o produto. Cada nível tem dois exemplos; frases mistas sem predominância recebem 2. Nota = 100 × (1 − |previsto − esperado|/4). Não há faixa de aceitação: cada exemplo tem uma nota exata.

Categoria identifica a solicitação principal em vendas, suporte, financeiro ou outros. Menção a pagamento numa descrição de erro não muda o assunto principal para financeiro. Nota = 100 × (1 − soma dos erros quadráticos das probabilidades/2), usando o gabarito one-hot. Acerto e probabilidade da categoria correta ficam no detalhe.

A nota agregada é a média dos dez critérios; duração e custo correspondem ao lote de dez decisões. Probabilidades não são justificativas e confiança não prova correção. Estes casos são um diagnóstico inicial, não uma estimativa de acerto em produção.
