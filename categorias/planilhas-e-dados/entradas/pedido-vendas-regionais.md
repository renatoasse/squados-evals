Sou do comercial de uma distribuidora de móveis e periféricos de escritório e preciso fechar o relatório do 3º trimestre de 2026 (julho a setembro).

As vendas do trimestre estão na tabela `vendas`, que você consulta com a ferramenta `planilha_consultar` (SQL do SQLite, só leitura). Cada linha é uma venda, com estas colunas:

- `data`: data da venda, no formato AAAA-MM-DD;
- `regiao`: Norte, Nordeste, Centro-Oeste, Sudeste ou Sul;
- `vendedor`: nome do vendedor;
- `produto`: nome do produto;
- `quantidade`: unidades vendidas;
- `valor_unitario`: preço de tabela por unidade, em reais;
- `desconto`: desconto concedido, em porcentagem (0 a 20).

O faturamento de uma venda é `quantidade × valor_unitario × (1 − desconto/100)`. O ticket médio de uma região é o faturamento da região dividido pelo número de vendas (linhas) dela.

Responda, considerando a tabela inteira salvo quando a pergunta disser o mês:

1. Qual foi o faturamento total de setembro de 2026, em reais?
2. Qual região teve o maior ticket médio no trimestre?
3. Qual vendedor vendeu mais unidades no trimestre?
4. Qual a porcentagem das vendas (linhas) com desconto maior que 10%?
5. Qual produto teve a maior queda de faturamento de agosto para setembro?

Consulte os dados antes de responder. Responda só com um JSON neste formato, sem nada antes ou depois:

{ "p1": <número, em reais, com 2 casas decimais>, "p2": "<região, como está na coluna>", "p3": "<vendedor, como está na coluna>", "p4": <número, em %, com 1 casa decimal>, "p5": "<produto, como está na coluna>" }
