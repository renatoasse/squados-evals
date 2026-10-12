# Metodologia de avaliação

O benchmark avalia tarefas de trabalho em português com materiais definidos, critérios explícitos e pesos. É uma bateria pequena e dirigida; suas notas não estimam automaticamente desempenho em qualquer cenário de produção.

## Materiais e critérios

Cada teste publica o pedido, seus materiais de contexto, um template de prompt, critérios, pesos e métricas. Referência é uma saída ideal de controle; anti-referência é uma saída que viola critérios. Não são respostas de modelos avaliados. Os JSONs de execução em entradas descrevem cenários, estados e ferramentas do teste, não resultados pagos do ranking.

Os materiais incluem cenários fictícios, dados sintéticos e documentos simulados, inclusive exemplos com aparência de normas e fontes oficiais. Valores e datas desses exemplos servem ao teste de uso das fontes fornecidas; não são orientação jurídica, contábil ou informação atual sobre legislação.

Critérios `codigo` representam checagens determinísticas cuja condição está descrita no material público. Critérios `juiz` publicam a pergunta e a variável de contexto fornecida aos verificadores. O código desses verificadores e dos simuladores não é distribuído aqui; a descrição não substitui a implementação para reprodução idêntica.

## Julgamento de texto

Cada critério de juiz é submetido a três modelos, documentados em `juizes.json`, com temperatura 0 e configuração de reasoning/limite de saída ali registrada. O critério passa com pelo menos dois votos `sim`. Uma saída vazia reprova. Resposta inválida de juiz não conta como voto positivo; erro de infraestrutura torna a avaliação incompleta.

Instrução de sistema do juiz:

> Você é um verificador objetivo. Avalie SOMENTE a condição dada, sem opinar sobre qualidade. Responda apenas com JSON: {"resposta":"sim"|"nao","evidencia":"<trecho literal da RESPOSTA AVALIADA que sustenta a decisão, ou vazio>"}. Responda "sim" somente se a RESPOSTA AVALIADA satisfaz a condição.

O pedido ao juiz contém `CONDIÇÃO: <pergunta>`, opcionalmente `MATERIAL DE REFERÊNCIA: <contexto>`, e `RESPOSTA AVALIADA: <saída>`, separados por linhas em branco.

## Notas e agregação

A nota de cada execução é `100 × soma(score do critério × peso) / soma(pesos)`, arredondada a uma casa decimal. Critérios binários usam 1 quando passam e 0 quando reprovam. Critérios contínuos usam o score entre 0 e 1.

Cada par teste/variante de modelo requer três repetições distintas na mesma rodada, sem cache. Nota baixa ou limitação válida do modelo conta como avaliação; erro de provedor ou juiz e repetição ausente não completam cobertura. A nota do teste é a média das três execuções; a variação é máximo menos mínimo.

A nota de categoria é a média dos testes da categoria, e a nota geral é a média das categorias, com pesos iguais entre categorias. O ranking de texto exige cobertura completa dos testes de texto atuais e um método de avaliação conhecido. Modelos de decisão são tratados separadamente.

Intervalos são percentis 2,5% e 97,5% de 2.000 reamostragens bootstrap, seed 42, reamostrando tarefas dentro das categorias e execuções dentro das tarefas. São intervalos descritivos para esta bateria. As faixas são atribuídas em ordem decrescente de nota: uma nova faixa começa quando o limite superior do modelo fica abaixo do limite inferior do líder da faixa atual.

## Modelos de decisão

Há três testes de dez casos cada, com três repetições por lote. Não usam juízes LLM. O gabarito aparece nos critérios públicos e não no pedido ao modelo.

- Sim/não: `100 × (1 − (probabilidade − esperado)²)`. Acerto usa corte 0,5.
- Satisfação: `100 × (1 − |previsto − esperado| / 4)`, em escala 0–4.
- Categoria: `100 × (1 − Brier multiclasse / 2)`, com gabarito one-hot.

A nota é a média dos dez casos. Custo e duração correspondem ao lote. Scores de decisão não entram no ranking público de texto.

## Ferramentas e parâmetros

Os schemas publicados descrevem os nomes, argumentos e descrições das ferramentas simuladas. Estados iniciais e pedidos ficam nas entradas das tarefas. O simulador privado fornece as transições de estado; publicar schemas não publica seus executores.

O protocolo privado permite até 25 passos por turno e 10 minutos por célula. O pedido usa mensagem de usuário e, quando definida, a variável `sistema` como mensagem de sistema. Em cenários com roteiro, o sistema recebe instrução inicial mais o prompt, e as falas do cliente são enviadas em sequência, preservando o histórico e os retornos das ferramentas. São detalhes documentais do protocolo, sem incluir sua implementação.

Um resultado de ranking depende da versão do dataset, do identificador completo do modelo, do reasoning, dos limites de saída, da data de execução e do método de julgamento. Esta edição publica os materiais e a configuração atual dos juízes, mas não resultados nem configurações de participantes de rodadas. Quando resultados forem publicados, deverão identificar esses parâmetros e o commit dos materiais usado, sem misturar rodadas de métodos diferentes.
