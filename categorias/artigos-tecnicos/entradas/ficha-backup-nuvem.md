# Ficha técnica — Backup automático no Arquivo Seguro Empresas

Produto: Arquivo Seguro Empresas (serviço fictício de backup em nuvem para pequenas empresas)
Versão do agente: 7.3
Público do tutorial: responsável pela TI de um escritório, sem formação técnica

## Requisitos
- Windows 10 ou 11, ou macOS 13 ou mais recente.
- 2 GB de memória livre e conexão com a internet.
- Plano Equipe ativo, com 500 GB de espaço por computador.
- Login da empresa já criado pelo administrador no painel web.

## Passo a passo (ordem obrigatória — os nomes entre aspas são os nomes exatos dos menus e botões)

1. No painel web, abra o menu "Dispositivos" e clique em "Baixar Agente". Instale o agente no computador que terá backup.
2. Abra o agente e clique em "Entrar com Conta da Empresa". Use o e-mail corporativo e a senha do painel.
3. Na tela inicial do agente, clique em "Novo Plano de Backup" e dê um nome ao plano (por exemplo, o nome do computador).
4. Em "Selecionar Pastas", marque as pastas que serão copiadas. O padrão sugerido é Documentos, Área de Trabalho e a pasta da rede compartilhada mapeada no computador.
5. Em "Regras de Exclusão", deixe ativas as regras padrão: arquivos temporários (.tmp), imagens de disco (.iso) e arquivos acima de 4 GB ficam fora do backup.
6. Em "Agendamento Automático", escolha a frequência "Diário" e o horário. O padrão é 22:00. Marque "Executar ao ligar se o horário foi perdido".
7. Em "Chave de Criptografia", crie uma chave com no mínimo 12 caracteres e guarde-a em local seguro, fora do computador. Sem a chave, nem o suporte consegue recuperar os arquivos.
8. Em "Retenção de Versões", mantenha o padrão: até 30 versões de cada arquivo, guardadas por 90 dias.
9. Depois da primeira cópia completa, abra "Testar Restauração", escolha 3 arquivos de pastas diferentes, restaure-os na pasta "Restauração de teste" e compare com os originais. Só considere o backup configurado depois desse teste.

## Observações
- A primeira cópia completa pode levar até 48 horas para cada 200 GB, dependendo da conexão; as seguintes copiam só o que mudou.
- O agente limita o upload a 50% da banda durante o expediente, para não atrapalhar o trabalho.
- O status de cada plano aparece no menu "Dispositivos" do painel web: verde (em dia), amarelo (atrasado mais de 2 dias) ou vermelho (falhou).
