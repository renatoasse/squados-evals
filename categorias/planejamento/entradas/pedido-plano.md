Você é gerente de projetos. Monte o plano do projeto descrito no briefing abaixo.

Responda somente com um JSON neste formato, sem texto antes ou depois:

{ "tarefas": [ { "id": "t1", "nome": "...", "inicio": 0, "duracao": 3, "depende_de": [], "responsavel": "...", "custo": 0 } ] }

Regras do plano:
- Os dias são numerados a partir de 0. Uma tarefa com "inicio": 3 e "duracao": 2 ocupa os dias 3 e 4 e termina no dia 5 (fim = inicio + duracao).
- Uma tarefa só pode começar quando todas as tarefas listadas em "depende_de" já terminaram. Use em "depende_de" os ids das tarefas do próprio plano.
- "responsavel" é o nome de uma única pessoa da equipe do briefing. Cada pessoa faz uma tarefa por vez: as tarefas de uma mesma pessoa não podem se sobrepor.
- "custo" é o valor em reais, como número sem formatação (0 quando a tarefa não tem custo).
- Crie uma tarefa para cada entregável obrigatório e use no campo "nome" exatamente o nome do entregável como está escrito no briefing. Você pode criar outras tarefas se achar necessário.
- O plano inteiro precisa caber no prazo: para toda tarefa, inicio + duracao não pode passar do prazo do briefing.
