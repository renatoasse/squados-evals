# Migração do ERP da Distribuidora Serra Azul

A Distribuidora Serra Azul vai trocar o ERP antigo por um novo sistema de gestão. O projeto tem 60 dias, numerados de 0 a 59; o prazo do plano é, portanto, 60.

## Restrições

- Só existe um DBA na empresa, a Marina Lopes. Todas as tarefas de DBA são dela, e ela faz uma de cada vez.
- O corte para o novo ERP só pode acontecer no fim de semana liberado pela diretoria: a tarefa "Corte para o novo ERP" começa obrigatoriamente no dia 55 e dura 2 dias (dias 55 e 56).
- Os usuários precisam estar treinados antes do corte, e os dados precisam estar validados antes do corte.

## Equipe

- Marina Lopes — DBA
- Rafael Costa — analista de sistemas
- Sofia Martins — analista de sistemas
- Tiago Nunes — instrutor

Cada entregável só pode ser feito por alguém da função indicada.

## Entregáveis obrigatórios

| Entregável | Função | Duração (dias) | Depende de |
|---|---|---|---|
| Levantamento dos processos | analista de sistemas | 6 | — |
| Mapeamento do banco atual | DBA | 6 | — |
| Configuração do novo ERP | analista de sistemas | 15 | Levantamento dos processos |
| Script de migração dos dados | DBA | 12 | Mapeamento do banco atual |
| Integrações com banco e loja virtual | analista de sistemas | 10 | Configuração do novo ERP |
| Carga de teste | DBA | 5 | Script de migração dos dados, Configuração do novo ERP |
| Validação dos dados migrados | DBA | 6 | Carga de teste |
| Treinamento dos usuários | instrutor | 8 | Configuração do novo ERP |
| Corte para o novo ERP | DBA | 2 | Validação dos dados migrados, Treinamento dos usuários, Integrações com banco e loja virtual |
| Acompanhamento pós-corte | analista de sistemas | 3 | Corte para o novo ERP |

Não há custos externos neste projeto: use custo 0 em todas as tarefas.
