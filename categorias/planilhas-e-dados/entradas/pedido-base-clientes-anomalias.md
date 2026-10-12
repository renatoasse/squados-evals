Vou migrar a base de clientes da loja para um CRM novo e preciso limpar os dados antes.

A base está na tabela `clientes`, que você consulta com a ferramenta `planilha_consultar` (SQL do SQLite, só leitura). Cada linha é um cliente, com estas colunas:

- `id`: identificador numérico do cliente;
- `nome`: nome completo;
- `email`: e-mail de contato;
- `cpf`: CPF;
- `cidade`: cidade do cadastro;
- `valor_compras`: total comprado pelo cliente, em reais.

Encontre três tipos de problema:

1. **Duplicados:** o mesmo e-mail cadastrado em mais de um cliente. O nome pode ter sido digitado de outro jeito no segundo cadastro. Informe cada par de ids.
2. **Outliers de valor:** clientes cujo `valor_compras` é de 50 vezes a mediana da coluna ou mais (provável erro de digitação).
3. **CPF com formato inválido:** o formato válido é `000.000.000-00` (11 dígitos, com os dois pontos e o traço). Não precisa conferir os dígitos verificadores.

Consulte os dados antes de responder. Responda só com um JSON neste formato, sem nada antes ou depois:

{ "duplicados": [[<id>, <id>], ...], "outliers": [<id>, ...], "cpf_invalido": [<id>, ...] }
