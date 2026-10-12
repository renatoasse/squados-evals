# Transcrição — Reunião quinzenal de produto do Pedido Certo

Empresa: Rota Verde Tecnologia
Data: segunda-feira, 14 de setembro de 2026, das 10h00 às 10h40, por videochamada
Participantes: Mariana Lopes (gerente de produto, conduz a reunião), Diego Santana (líder técnico), Priscila Nogueira (designer), Júlio Ferraz (sucesso do cliente) e Tatiane Rocha (dados e qualidade)
Transcrição automática, revisada só para corrigir nomes próprios.

[00:00] Mariana: Bom dia, gente. Deixa eu ver se todo mundo entrou. Diego, Priscila, Tati... Júlio, você está aí?

[00:08] Júlio: Estou, estou. Só fechando a janela aqui que o vizinho resolveu cortar grama justo agora.

[00:14] Priscila: Clássico. Aqui em casa o problema é o gato, que decidiu que o teclado é a cama dele. Se aparecer uma frase sem sentido no chat, já sabem quem foi.

[00:27] Diego: Pelo menos o seu gato escreve. O meu só derruba copo da mesa.

[00:33] Júlio: E aí, Diego, viu o jogo ontem? Que vergonha aquele segundo tempo.

[00:39] Diego: Nem me fala. Desliguei a televisão no segundo gol. Fui lavar louça, foi mais produtivo.

[00:45] Júlio: Eu fiquei até o fim por teimosia. Aquele pênalti não existiu, pode olhar o replay quantas vezes quiser.

[00:53] Tatiane: Vocês sabem que isso está sendo transcrito, né? Vai ficar registrado para sempre que o Júlio chorou o pênalti.

[01:02] Júlio: Pode registrar. Quero que a história saiba.

[01:05] Mariana: Tá bom, deixa o futebol para o almoço. Antes de começar, um aviso rápido que não tem a ver com produto: a máquina de café do terceiro andar quebrou de novo, e o pessoal de facilities pediu para ninguém mexer nela, porque da última vez alguém tentou consertar e piorou.

[01:27] Diego: Não fui eu.

[01:28] Mariana: Ninguém falou que foi você, Diego.

[01:31] Diego: Só estou deixando registrado, já que a Tati disse que tudo fica registrado.

[01:37] Mariana: Certo. Bom, a pauta de hoje é a versão 3.2 do Pedido Certo. Eu mandei ontem à noite no canal. São seis assuntos: primeiro, os números do checkout que a Tati trouxe; segundo, o pagamento por Pix; terceiro, o fornecedor de notificações push; quarto, o modo offline que o Grupo Sabor Serrano pediu; quinto, o onboarding; e sexto, a notificação de entrega por WhatsApp. Temos quarenta minutos, então vou tentar segurar o tempo. Tati, quer começar?

[02:10] Tatiane: Quero. Vou compartilhar a tela. Estão vendo?

[02:13] Priscila: Estamos.

[02:14] Tatiane: Então, isso aqui é o funil de compra dos últimos trinta dias, só de restaurantes que já fizeram pelo menos um pedido antes. Ou seja, não é gente nova, é cliente que já conhece o app. Do total de carrinhos que chegam até a revisão do pedido, 31% abandonam na etapa de pagamento. Na etapa de revisão, o abandono é de 9%, e na escolha do horário de entrega fica em 6%. Então o gargalo claramente é o pagamento.

[02:47] Mariana: Trinta e um por cento é muito.

[02:51] Tatiane: É muito. E quando eu cruzo com os chamados de suporte, aparece uma coisa interessante. Dos chamados abertos no mesmo período sobre pagamento, a maioria é sobre boleto: restaurante que gerou o boleto, esqueceu de pagar, o pedido caiu e o produto não foi separado. E tem outro grupo grande de gente perguntando se dá para pagar com Pix.

[03:16] Júlio: Isso bate com o que eu ouço todo dia. O dono de restaurante pequeno não quer boleto. Ele quer pagar na hora, ver que pagou e esquecer. O cartão corporativo, muitos nem têm.

[03:30] Tatiane: E tem mais um dado. Na pesquisa que mandamos em agosto, 42% dos restaurantes que responderam colocaram o Pix como a melhoria mais importante. Foi a primeira da lista, bem na frente da segunda, que era o histórico de preços.

[03:48] Mariana: Quantos responderam a pesquisa?

[03:50] Tatiane: Cento e oitenta e sete restaurantes. É uma amostra boa para o nosso tamanho.

[03:56] Mariana: Tá. Então isso já puxa o segundo assunto. Diego, Pix. O que a gente precisa para colocar na 3.2?

[04:04] Diego: Então, a parte técnica não me assusta. O gateway que a gente usa hoje, a Pagare, já oferece Pix na API. A gente geraria o QR Code e o código copia e cola no checkout, e o pedido só é confirmado quando chega a notificação de pagamento. O que eu ainda não sei é a taxa por transação e o prazo de liquidação. Se o dinheiro cair para o distribuidor só em dois dias, por exemplo, muda a conversa com eles.

[04:39] Júlio: Para o distribuidor, o prazo de liquidação é tudo. Se for igual ou melhor que o do cartão, eles topam na hora.

[04:48] Diego: Então, preciso confirmar com a Pagare. Na documentação pública tem uma tabela, mas ela diz "condições negociadas por volume", que é o jeito educado de dizer "liga para a gente".

[05:02] Priscila: E do lado do design, é tranquilo. O checkout já tem espaço para mais um método de pagamento. Eu só preciso desenhar a tela do QR Code e o estado de "aguardando pagamento", que hoje não existe, porque o cartão é instantâneo e o boleto sai do app.

[05:22] Mariana: E o tempo de expiração do QR Code? Se o restaurante gerar e não pagar?

[05:29] Diego: A gente define. Normalmente se usa trinta minutos. Depois disso o pedido volta para o carrinho, sem perder os itens.

[05:38] Tatiane: Eu gosto disso, porque hoje com o boleto o pedido simplesmente some, e o cliente tem que montar tudo de novo. Metade das reclamações vem daí.

[05:49] Júlio: Tem uma coisa do lado dos distribuidores que eu queria levantar antes de a gente fechar. Hoje eles fazem a conciliação dos pagamentos numa planilha, cruzando o extrato da Pagare com os pedidos do painel. Com o boleto já dá trabalho. Se entrar o Pix e cada pagamento chegar com um identificador diferente, eles vão enlouquecer.

[06:13] Diego: Isso dá para resolver. A gente manda o número do pedido no campo de identificação da cobrança Pix. Aí, no extrato, cada pagamento aparece com o número do pedido do lado. Fica até mais fácil que o boleto.

[06:29] Júlio: Se for assim, ótimo. Esse é o tipo de detalhe que faz o distribuidor gostar ou odiar a novidade.

[06:38] Tatiane: E para a gente medir depois, eu preciso que o método de pagamento venha certinho no evento de pedido confirmado. Hoje o evento só diz "pago" ou "não pago". Se a gente não separar por método, eu não consigo dizer se o Pix reduziu o abandono ou não.

[06:58] Diego: Anotado, isso entra junto com a integração. É um campo a mais no evento.

[07:05] Priscila: E uma pergunta de design: o Pix aparece como primeira opção na tela de pagamento ou a gente mantém a ordem atual, com o cartão primeiro?

[07:16] Tatiane: Eu colocaria o Pix primeiro. Se 42% pediram, é o que a maioria vai querer usar.

[07:23] Júlio: Concordo. E o restaurante que usa cartão já sabe onde está o cartão, não vai se perder.

[07:31] Priscila: Então Pix primeiro, cartão depois, boleto por último. Isso fica comigo, no desenho da tela.

[07:38] Mariana: Bom, eu acho que aqui não tem muita dúvida. A demanda é clara, o gateway suporta e o design cabe. Alguém é contra colocar o Pix na 3.2?

[07:50] Diego: Contra, não. Só quero deixar claro que, se a taxa da Pagare vier muito alta, a gente volta a falar.

[07:59] Mariana: Justo. Então fica decidido: o Pix entra no checkout da versão 3.2. E Diego, você levanta com a Pagare a taxa por transação e o prazo de liquidação. Consegue até quando?

[08:12] Diego: Eu tenho uma call com o gerente de conta deles na quinta. Consigo trazer até sexta.

[08:19] Mariana: Sexta, dia 18. Combinado. Priscila, a tela do QR Code entra no seu fluxo normal da sprint, né? Não precisa de prazo separado?

[08:29] Priscila: Não precisa, entra no fluxo. Eu aviso se apertar.

[08:33] Mariana: Ótimo. Terceiro assunto: notificações push. Diego, você que trouxe.

[08:38] Diego: Isso. Então, o PushNow, que é o fornecedor que a gente usa hoje, está com uma taxa de entrega ruim. No último mês, só 87% das notificações foram entregues no Android. No iPhone está melhor, mas no Android, que é a maioria dos nossos usuários, está ruim. E a notificação é justamente o que avisa o restaurante que o pedido foi confirmado ou que o caminhão saiu.

[09:06] Júlio: Isso eu sinto no suporte. Tem cliente que liga perguntando se o pedido foi confirmado, porque não recebeu nada.

[09:15] Tatiane: Eu consigo confirmar isso nos dados. Quando a notificação de "pedido confirmado" não é entregue, a chance de o restaurante abrir um chamado no mesmo dia mais que dobra.

[09:27] Diego: Então, eu andei olhando alternativas, e a que me pareceu melhor é a Sinalix. A taxa de entrega que eles divulgam é bem maior, o painel de métricas é melhor, e o preço por mil notificações é parecido com o que a gente paga hoje.

[09:47] Mariana: E a migração? Quanto trabalho dá?

[09:50] Diego: Do lado do servidor, pouco. É trocar a chamada de envio. Do lado do app, tem que trocar o SDK, mas parece simples. Eu chutaria uma sprint, no máximo.

[10:02] Priscila: Muda alguma coisa para o usuário? Permissão nova, alguma tela?

[10:07] Diego: Para o usuário, nada. Ele continua recebendo a notificação igual.

[10:11] Mariana: Bom, se o problema é real e a troca é simples, eu não vejo por que segurar. Vamos fazer assim: a gente migra as notificações push do PushNow para a Sinalix na versão 3.2. Diego, você abre a conta lá e começa a integração?

[10:30] Diego: Abro. Hoje mesmo eu peço o acesso de teste.

[10:35] Mariana: Fechado. Então: Pix na 3.2 e migração para a Sinalix na 3.2. Vamos para o quarto assunto, que é o mais delicado: o modo offline.

[10:46] Júlio: Delicado mesmo. Deixa eu dar o contexto. O Grupo Sabor Serrano tem onze restaurantes, a maioria em cidade pequena da serra, e em pelo menos quatro deles o sinal de celular dentro da cozinha é péssimo. O pessoal sai para a calçada para conseguir mandar o pedido. Eles pediram, formalmente, por e-mail, que o app funcione sem internet: o cozinheiro monta o pedido offline e, quando o celular pega sinal, o pedido é enviado sozinho.

[11:18] Mariana: E eles são o nosso maior cliente em número de unidades.

[11:23] Júlio: São. E o diretor de compras deles, o senhor Haroldo, já falou duas vezes que, se a gente resolver isso, ele leva o app para a rede de padarias do cunhado. Não é ameaça, mas é uma oportunidade que eu não queria perder.

[11:41] Diego: Eu entendo a importância, mas preciso ser honesto sobre o tamanho disso. Modo offline não é um botão. A gente teria que guardar o catálogo inteiro no celular, com preço, e o preço muda todo dia de manhã no hortifrúti. Teria que resolver o que acontece quando o pedido montado offline usa um preço que já mudou, ou um produto que acabou no estoque do distribuidor. E a fila de envio precisa ser à prova de duplicidade: se o celular mandar duas vezes, não pode virar dois pedidos.

[12:18] Tatiane: E isso é teste para caramba. Cada um desses cenários vira um caso de teste, e alguns são difíceis de reproduzir.

[12:28] Mariana: Diego, quanto tempo?

[12:29] Diego: Fazendo direito, umas seis semanas de dois desenvolvedores. E isso tirando gente do Pix e da migração do push. Não cabe na 3.2 de jeito nenhum.

[12:41] Priscila: Tem também o design. O usuário precisa entender que o pedido está "na fila" e não "enviado". Se ele achar que mandou e não mandou, o restaurante fica sem mercadoria no dia seguinte. É o pior cenário possível para a gente.

[12:58] Júlio: Concordo que tem que ser bem feito. O que eu preciso é de uma data para dar ao Haroldo. Ele não precisa que seja amanhã, ele precisa saber que vai sair.

[13:12] Mariana: Tá. Então a minha proposta é a seguinte: a gente não faz na 3.2. O modo offline fica para o primeiro trimestre de 2027, como item principal da 3.4, com tempo para desenhar e testar direito. E a gente comunica isso ao Grupo Sabor Serrano já, com a data, em vez de deixar eles esperando sem resposta.

[13:36] Diego: Para mim faz sentido. No primeiro trimestre eu consigo planejar a equipe para isso.

[13:43] Júlio: Eu preferiria antes, mas entendo. Com uma data na mão, eu seguro o Haroldo. O que eu não seguro é silêncio.

[13:52] Priscila: E até lá, uma coisa pequena que ajudaria: a gente poderia salvar o carrinho localmente, para não perder os itens se a internet cair no meio. Não é modo offline, é só não perder o que já foi montado.

[14:09] Diego: Isso é bem mais simples. Talvez caiba numa versão intermediária. Mas não queria prometer agora.

[14:15] Mariana: Vamos anotar como ideia, sem compromisso. Então está decidido: modo offline adiado para o primeiro trimestre de 2027. Eu mesma atualizo o roadmap e escrevo para o Grupo Sabor Serrano explicando a data. Júlio, você quer estar copiado?

[14:32] Júlio: Quero, e quero revisar o texto antes de sair. O Haroldo é sensível com o tom.

[14:39] Mariana: Combinado. Eu atualizo o roadmap e mando o e-mail para eles até quarta, dia 16, com você revisando antes.

[14:47] Júlio: Fechado.

[14:48] Tatiane: Só uma pergunta antes de mudar de assunto: alguém sabe se a confraternização de fim de ano vai ser naquele sítio de novo? Porque o RH mandou uma enquete e eu não sei o que responder.

[15:04] Júlio: Eu votei no sítio. Teve churrasco, teve piscina, foi ótimo.

[15:08] Diego: Eu votei em qualquer lugar que não tenha karaokê.

[15:13] Priscila: Ah, mas o karaokê foi a melhor parte! O Júlio cantando aquela música sertaneja...

[15:19] Júlio: Isso não aconteceu. Não tem prova.

[15:22] Tatiane: Tem vídeo. Está no grupo.

[15:24] Júlio: Eu saí do grupo exatamente por isso.

[15:28] Mariana: Gente, a enquete é com o RH, cada um responde a sua. Vamos voltar. Quinto assunto: onboarding. Priscila.

[15:36] Priscila: Tá. Deixa eu compartilhar. Então, hoje, quando um restaurante novo baixa o app e cria a conta, a primeira coisa que aparece é aquele tutorial em vídeo de quatro minutos. A Tati me passou os números, e eles são bem tristes.

[15:53] Tatiane: São. Só 12% de quem começa o vídeo assiste até o fim. A maioria fecha nos primeiros vinte segundos. E quem pula o vídeo leva, em média, quase o dobro do tempo para fazer o primeiro pedido.

[16:09] Priscila: E isso faz sentido. O dono de restaurante baixa o app às seis da manhã, no meio da correria, para fazer um pedido. Ele não vai assistir a um vídeo. Então a minha proposta é trocar o vídeo por um onboarding guiado de três telas. Primeira tela: escolher os distribuidores que atendem o seu bairro. Segunda: montar uma "lista de sempre", com os itens que o restaurante compra toda semana. Terceira: escolher o horário de entrega preferido. Pronto. Quando ele termina, já está com tudo pronto para fazer o primeiro pedido em um toque.

[16:49] Júlio: Isso é muito bom. A lista de sempre, principalmente. Os clientes que mais compram são justamente os que montaram uma lista de favoritos, e hoje a maioria nem sabe que dá para fazer isso.

[17:04] Diego: Tecnicamente é tranquilo, porque as três coisas já existem no app, só estão espalhadas. É mais trabalho de tela do que de servidor.

[17:14] Júlio: E se o restaurante estiver num bairro onde nenhum distribuidor entrega? Isso acontece bastante nas cidades menores. Hoje ele descobre só na hora de fazer o pedido, e aí desinstala o app.

[17:28] Priscila: Pensei nisso. Na primeira tela, se não aparecer nenhum distribuidor, a gente mostra uma mensagem honesta, dizendo que ainda não atendemos aquela região, e pede o contato para avisar quando passar a atender. Melhor do que deixar a pessoa montar lista à toa.

[17:47] Tatiane: E esse contato vira dado para o comercial. Dá para saber onde tem demanda reprimida.

[17:53] Júlio: Isso é ouro para a gente negociar com distribuidor novo. Gostei.

[17:58] Mariana: E o vídeo? Some de vez?

[18:01] Priscila: Eu deixaria o vídeo na central de ajuda, para quem quiser. Mas ele sai do primeiro acesso.

[18:09] Tatiane: Eu só peço para a gente medir antes e depois. Eu preparo os eventos: quantos completam as três telas, em quanto tempo, e quanto tempo até o primeiro pedido. Aí a gente compara com o vídeo.

[18:24] Mariana: Perfeito. Alguém contra?

[18:26] Diego: Não.

[18:27] Júlio: Não, pelo contrário.

[18:29] Mariana: Então decidido: o onboarding guiado de três telas substitui o tutorial em vídeo no primeiro acesso, e o vídeo vai para a central de ajuda. Priscila, quando você consegue um protótipo navegável para a gente testar com uns dois ou três clientes?

[18:47] Priscila: Eu já tenho os rascunhos. Protótipo navegável, bem feito, para mostrar para cliente... eu diria sexta da semana que vem.

[18:55] Mariana: Sexta da semana que vem é dia 25.

[18:59] Priscila: Isso, dia 25 de setembro.

[19:02] Mariana: Ótimo. Priscila, protótipo do onboarding até 25 de setembro. E aproveitando, antes de ir para o WhatsApp, Tati, você tinha falado de um relatório de abandono mais detalhado?

[19:14] Tatiane: Tinha. O número de 31% de abandono no pagamento é a média geral. Mas eu desconfio que restaurante pequeno e restaurante de rede se comportam muito diferente. Eu queria abrir esse abandono de carrinho por etapa e por porte de restaurante, e cruzar com o método de pagamento que cada um tentou usar. Isso ajuda a gente a saber se o Pix vai resolver ou se tem outra coisa por trás.

[19:44] Diego: Isso seria ótimo para a conversa com a Pagare, inclusive. Se eu souber o volume esperado de Pix, negocio melhor a taxa.

[19:54] Tatiane: Então, o problema é que eu não consigo até sexta. Eu preciso limpar os dados de porte, que estão bagunçados no cadastro. Consigo até terça, dia 22.

[20:06] Diego: Tudo bem, para a Pagare eu uso o número geral mesmo. O detalhado serve para a gente depois.

[20:14] Mariana: Então Tati, relatório de abandono de carrinho por etapa e porte de restaurante até terça, 22 de setembro.

[20:22] Tatiane: Anotado.

[20:23] Júlio: Mariana, antes do WhatsApp, posso puxar um assunto que não está na pauta, mas que tem a ver com o Pix? Prometo que é rápido.

[20:33] Mariana: Pode, mas rápido mesmo.

[20:36] Júlio: Dois distribuidores me perguntaram, na semana passada, se com o Pix a gente vai tirar o boleto. O Hortifrúti Dois Irmãos, principalmente, depende muito do boleto, porque tem cliente grande, de rede, que só paga assim, com prazo de vinte e oito dias. Se a gente tirar, eles perdem esses clientes.

[20:57] Diego: Ninguém falou em tirar o boleto, né?

[21:01] Mariana: Ninguém. O Pix entra como mais uma opção.

[21:05] Tatiane: Mas, se me permitem, eu acho que vale a pena olhar isso com dados no futuro. O boleto é o método com mais pedido caído. Se o Pix pegar, talvez faça sentido o boleto virar uma opção só para quem tem cadastro com prazo, e não para todo mundo.

[21:26] Júlio: Isso eu topo discutir, mas com os distribuidores na mesa. Eles vão querer opinar.

[21:32] Diego: E tecnicamente seria só uma regra de exibição. O boleto continuaria existindo, só não apareceria para quem não tem prazo cadastrado.

[21:41] Mariana: Tá, mas isso não é para hoje. A gente não tem dado de como o Pix vai performar, e eu não quero mudar duas coisas no checkout ao mesmo tempo. Vamos fazer assim: o boleto continua como está. Depois que o Pix estiver rodando há uns dois meses, a Tati traz os números e a gente reabre essa conversa, com o Júlio trazendo a visão dos distribuidores. Mas hoje não está decidido nada sobre o boleto, tá? Júlio, pode tranquilizar o Dois Irmãos.

[22:17] Júlio: Posso dizer que o boleto não sai?

[22:20] Mariana: Pode dizer que não há nenhuma mudança prevista no boleto. É verdade e não promete nada além disso.

[22:28] Júlio: Perfeito. É o que eu precisava.

[22:31] Diego: Já que estamos fora da pauta, deixa eu dar um status rápido da 3.1, que saiu semana passada, porque teve gente perguntando no canal.

[22:41] Mariana: Vai.

[22:42] Diego: O problema do cupom de desconto, aquele que aplicava o desconto duas vezes quando o restaurante voltava do pagamento para o carrinho, está corrigido. Subimos a correção na quinta, e desde então não teve nenhum caso novo. Os pedidos afetados antes da correção, que foram dezessete, o financeiro já ajustou com os distribuidores.

[23:05] Júlio: Confirmo. Eu liguei para os três distribuidores que tiveram pedido afetado e ficou tudo resolvido. Um deles até agradeceu por a gente ter avisado antes de ele perceber.

[23:17] Diego: E a taxa de travamento do app caiu bastante com a 3.1. A gente estava com um problema na tela de catálogo, quando o distribuidor tinha mais de quinhentos produtos, e a tela travava em celular mais antigo. Isso foi resolvido com a paginação. A Tati tem o número exato.

[23:39] Tatiane: Tenho. As sessões com travamento caíram de 2,4% para 0,6% na primeira semana depois da 3.1. Ainda é cedo, mas é uma queda grande. A maior parte dos travamentos que sobraram é em um modelo específico de celular, bem antigo, que alguns restaurantes ainda usam na cozinha.

[23:59] Priscila: É aquele que o pessoal deixa preso na parede, com capinha de plástico, né? Eu vi num restaurante que visitei. Ele fica coberto de farinha.

[24:10] Tatiane: Esse mesmo. Não vale a pena otimizar para ele, na minha opinião. É pouca gente.

[24:16] Diego: Concordo. Se a gente começar a otimizar para celular de dez anos atrás, não faz mais nada.

[24:24] Mariana: Tá. Ninguém está propondo isso, então segue como está. Mais algum status?

[24:29] Priscila: Um rapidinho do design. Eu terminei a revisão de acessibilidade das telas principais, que estava pendente desde a 3.0. O contraste dos botões de confirmar estava abaixo do recomendado, e o tamanho dos textos de preço, muito pequeno para quem lê de longe, na bancada. Os ajustes já estão no sistema de design. Vão entrando nas telas conforme forem sendo mexidas, não precisa de esforço separado.

[24:58] Mariana: Ótimo. Isso eu gosto: melhora sem virar projeto.

[25:01] Tatiane: E só para registrar, a pesquisa de satisfação do trimestre fecha no fim do mês. Até agora a nota média está em 8,1, um pouco acima do trimestre passado. Os comentários negativos são quase todos sobre pagamento e sobre não saber onde está a entrega. Ou seja, exatamente os dois assuntos de hoje.

[25:24] Júlio: Isso é bom sinal. Quer dizer que a gente está atacando o que importa.

[25:30] Mariana: Bom, chega de status. Agora sim, WhatsApp.

[25:34] Mariana: Sexto assunto da pauta: notificação de entrega por WhatsApp. Júlio, com você.

[25:39] Júlio: Então. Isso aqui é o pedido número um dos clientes no suporte, depois do Pix. O restaurante quer saber onde está a entrega. Hoje a gente manda push quando o caminhão sai, mas, como o Diego falou, o push nem sempre chega, e muito cozinheiro nem tem o app instalado: quem tem é o dono. O cozinheiro está na cozinha, com o WhatsApp aberto o dia inteiro. Se a mensagem "seu pedido saiu para entrega" chegasse no WhatsApp, metade das ligações para o suporte acabaria.

[26:15] Tatiane: Metade eu não sei, mas eu olhei: 38% das ligações do suporte no mês passado foram de "onde está meu pedido". É a maior categoria disparada.

[26:27] Diego: Tecnicamente, a gente teria que usar a API oficial do WhatsApp Business, por um provedor. Cada mensagem tem custo, e as mensagens precisam ser de modelos aprovados antes. Não dá para mandar qualquer texto. E o principal: o restaurante precisa autorizar o recebimento. Sem o consentimento, a gente não pode mandar.

[26:49] Priscila: E qual número recebe? O do dono, o do cozinheiro, os dois?

[26:54] Júlio: Isso eu ia perguntar para os clientes. Cada restaurante funciona de um jeito. Em alguns, quem recebe a mercadoria é o gerente; em outros, é o próprio dono.

[27:06] Mariana: Deixa eu fazer uma pergunta importante. A ideia é só status de entrega? Porque eu já ouvi gente do comercial falando em usar o WhatsApp para mandar promoção, oferta do dia...

[27:20] Júlio: Não, não. Eu sou o primeiro a ser contra. Se a gente começar a mandar promoção, o cliente bloqueia o número e perde a notificação de entrega junto. Tem que ser só o status: pedido confirmado, saiu para entrega, entregue.

[27:37] Diego: Concordo. E fica mais barato também, porque são poucas mensagens por pedido.

[27:42] Mariana: Então eu proponho assim: a gente faz a notificação de status da entrega por WhatsApp, só com mensagens de status, nada de marketing, e só para quem autorizar. Antes de desenvolver, a gente valida com os cinco restaurantes do piloto como deve ser esse consentimento e qual número recebe.

[28:03] Tatiane: Qual piloto? O dos cinco restaurantes do centro?

[28:07] Júlio: Isso, os cinco do piloto do centro. São os que já testaram o histórico de preços com a gente. São parceiros, respondem rápido.

[28:17] Mariana: Alguém é contra a notificação por WhatsApp nesses termos?

[28:22] Diego: Nesses termos, não. Só quero ver o custo por mensagem antes de liberar para todo mundo.

[28:29] Priscila: Também não. Eu desenho a tela de autorização depois que o Júlio voltar dos clientes.

[28:35] Mariana: Então fica decidido: notificação de status da entrega por WhatsApp, só status, sem marketing, com consentimento do restaurante. Júlio, você conversa com os cinco restaurantes do piloto sobre o consentimento e sobre qual número deve receber. Até quando?

[28:52] Júlio: Essa semana eu tenho visita no centro na quinta e na sexta. Consigo falar com todos e trazer o resumo na segunda que vem.

[29:02] Mariana: Segunda, dia 21.

[29:04] Júlio: Dia 21 de setembro. Fechado.

[29:07] Diego: Só uma coisa: o Júlio podia perguntar também se eles topam receber pelo número da empresa ou se preferem um número de cada funcionário. Isso muda o modelo de cobrança do provedor.

[29:20] Júlio: Boa. Anoto junto.

[29:22] Mariana: Bom, isso fecha os seis assuntos da pauta. Mas antes de terminar, tem uma coisa que a Tati me pediu para incluir. Tati.

[29:32] Tatiane: É rápido. A 3.2 vai mexer no checkout, com o Pix, na notificação push e no primeiro acesso, com o onboarding. São três áreas sensíveis ao mesmo tempo. Eu queria montar um plano de testes de regressão para a 3.2, cobrindo checkout com os três métodos de pagamento, as notificações e o fluxo de primeiro acesso, para a gente não quebrar o que já funciona. E queria que esse plano estivesse pronto antes de o desenvolvimento acabar, não depois.

[30:06] Diego: Por favor. Na 3.1 a gente descobriu o problema do cupom só em produção.

[30:12] Mariana: Quando você consegue?

[30:14] Tatiane: Considerando o relatório de abandono que eu já me comprometi a entregar no dia 22, eu consigo o plano de testes de regressão até terça, dia 29.

[30:26] Mariana: Dia 29 de setembro. Tati, plano de testes de regressão da 3.2 até 29 de setembro. Fechado.

[30:33] Priscila: Posso aproveitar e jogar uma ideia? Muito cliente pede modo escuro. A cozinha é clara, mas o pessoal do turno da noite reclama da tela muito branca.

[30:45] Diego: Modo escuro agora não, pelo amor de Deus. Não com o Pix, o push e o onboarding na mesma versão.

[30:54] Mariana: Eu concordo com o Diego. Priscila, é uma boa ideia, mas não é para agora. Coloca no quadro de ideias e a gente conversa numa próxima. Não estamos decidindo nada sobre isso hoje.

[31:08] Priscila: Justo. Coloco no quadro.

[31:10] Júlio: Falando em ideia, alguém já testou aquela cafeteria nova na esquina do escritório? Disseram que o pão de queijo é bom.

[31:19] Tatiane: Testei. O pão de queijo é bom, o café é fraco. E demora.

[31:25] Diego: Enquanto a máquina do terceiro andar estiver quebrada, café fraco é melhor que nenhum café.

[31:32] Júlio: Alguém devia ligar para o técnico da máquina.

[31:36] Mariana: Já falei, gente, a máquina é com o facilities. Não é tarefa nossa, ninguém aqui vai ligar para técnico nenhum. Bom, vamos fazer o resumo para fechar, que já estamos quase no horário.

[31:50] Diego: Pode ir, enquanto isso eu vou dando uma olhada numa coisa aqui que me deixou com a pulga atrás da orelha.

[31:59] Mariana: Tá. Então, recapitulando o que decidimos hoje. Um: Pix no checkout da 3.2. Dois: migração das notificações push do PushNow para a Sinalix, também na 3.2. Três: modo offline adiado para o primeiro trimestre de 2027. Quatro: onboarding guiado de três telas no lugar do vídeo. Cinco: notificação de status da entrega por WhatsApp, só status e com consentimento.

[32:25] Mariana: E as tarefas. Diego levanta com a Pagare a taxa e o prazo de liquidação do Pix até sexta, dia 18. Eu atualizo o roadmap e escrevo para o Grupo Sabor Serrano até quarta, dia 16, com o Júlio revisando. Priscila faz o protótipo navegável do onboarding até sexta, dia 25. Tati faz o relatório de abandono de carrinho por etapa e porte até terça, dia 22, e o plano de testes de regressão da 3.2 até terça, dia 29. Júlio conversa com os cinco restaurantes do piloto sobre o consentimento do WhatsApp até segunda, dia 21. E o Diego abre a conta na Sinalix e começa a integração.

[33:11] Priscila: Acho que é isso.

[33:13] Tatiane: Também acho.

[33:14] Diego: Pera, pera. Antes de fechar. Lembram que eu falei que ia dar uma olhada numa coisa? Eu abri o contrato do PushNow aqui enquanto vocês falavam, porque fiquei com a impressão de que a gente tinha assinado alguma fidelidade. E tinha.

[33:32] Mariana: Como assim?

[33:33] Diego: O contrato do PushNow foi renovado em março, por doze meses, com fidelidade. Se a gente cancelar antes de março do ano que vem, paga multa de três mensalidades. Não é uma fortuna, mas é dinheiro jogado fora por uma coisa que a gente pode fazer com calma daqui a seis meses.

[33:55] Júlio: Três mensalidades por nada. Isso o financeiro não vai aprovar fácil.

[34:01] Diego: E tem outra coisa, que é pior. Eu fui ver a documentação do SDK da Sinalix com mais cuidado. Eu tinha falado que era simples, mas não é tão simples assim: o SDK novo exige que a gente atualize a biblioteca de rede do app, e essa é a mesma biblioteca que a integração do Pix com a Pagare usa. Então, se a gente fizer as duas coisas na mesma sprint, eu estou mexendo na mesma peça por dois motivos diferentes ao mesmo tempo. Se der problema no checkout, eu não vou saber se foi o Pix ou a troca do push.

[34:44] Tatiane: Isso é exatamente o tipo de coisa que me tira o sono. Duas mudanças grandes na mesma peça, na mesma versão, e o plano de testes tendo que cobrir as duas combinações.

[34:58] Priscila: E o Pix é a prioridade, né? É o que os clientes pediram.

[35:04] Mariana: É. Se for para escolher, o Pix vem primeiro, sem dúvida.

[35:09] Diego: Então a minha recomendação, agora com essas informações, é a gente desfazer o que decidiu sobre o push. Não migrar para a Sinalix na 3.2. Fica com o PushNow até o fim do contrato, e a gente volta a esse assunto mais perto da renovação, com calma, sem misturar com o Pix.

[35:31] Júlio: Mas e o problema de entrega no Android? Os clientes continuam sem receber.

[35:37] Diego: Continua, mas tem duas coisas que aliviam. Primeiro, a notificação por WhatsApp que a gente acabou de decidir cobre justamente o status da entrega, que é o que mais dói. Segundo, eu consigo mexer na configuração de prioridade das mensagens do PushNow, que hoje está no padrão. Isso não resolve, mas melhora um pouco. É ajuste de configuração, coisa de meia hora, eu faço no dia a dia.

[36:06] Tatiane: Eu continuo medindo a taxa de entrega, de qualquer jeito. Se piorar, a gente vê.

[36:13] Mariana: Tá. Faz sentido para todo mundo? Eu prefiro admitir agora que a gente decidiu rápido demais do que descobrir no meio da sprint.

[36:23] Priscila: Faz sentido.

[36:24] Júlio: Faz. Com o WhatsApp vindo, eu consigo explicar para os clientes.

[36:29] Mariana: Então fica assim, e por favor registrem direito: está revertida a decisão sobre o push. A gente não migra para a Sinalix na 3.2, continua com o PushNow e volta ao assunto perto da renovação do contrato. Diego, você não abre a conta na Sinalix.

[36:48] Diego: Não abro. Ainda bem que eu não tinha pedido o acesso de teste. Ia pedir depois da reunião.

[36:56] Mariana: Ótimo. Então, para ficar claro, o recapitulando que eu fiz há pouco muda num ponto só: tira a Sinalix das decisões e tira a tarefa do Diego de abrir a conta lá. O resto continua igual.

[37:12] Júlio: Perfeito.

[37:13] Diego: Desculpa por embananar o fim da reunião.

[37:16] Mariana: Imagina, Diego. Melhor agora do que daqui a duas semanas. Inclusive, obrigada por ter ido conferir.

[37:23] Priscila: Uma dúvida que ficou, e aí eu paro. A tela de "aguardando pagamento" do Pix: eu faço com o contador regressivo dos trinta minutos ou só com o aviso de que expira?

[37:37] Diego: Com o contador. O restaurante precisa ver quanto tempo falta.

[37:42] Tatiane: E com o botão de copiar o código bem grande. A maioria vai pagar pelo celular, no mesmo aparelho, então o QR Code nem vai ser usado tanto. O copia e cola é que importa.

[37:57] Priscila: Bom ponto. Então copia e cola em destaque e o QR Code embaixo.

[38:03] Júlio: Só cuidado com o texto. Restaurante pequeno às vezes nem sabe o que é "copia e cola". Escreve "copiar código do Pix", que é o que o banco deles mostra.

[38:16] Priscila: Anotado. Isso fica comigo, no fluxo normal.

[38:19] Mariana: Ótimo. Mais alguma coisa? Não? Então, antes de encerrar, eu só queria reforçar uma coisa sobre o prazo da 3.2. A gente não fixou data de lançamento hoje, e não vou fixar agora, porque depende da resposta da Pagare. Assim que o Diego trouxer a taxa e o prazo de liquidação, na sexta, eu monto a proposta de data e trago na próxima reunião.

[38:46] Diego: Faz sentido. Sem a resposta da Pagare eu não consigo estimar com segurança.

[38:52] Júlio: E eu não vou prometer data nenhuma para cliente enquanto isso. Só para o Sabor Serrano, que é sobre o offline, e essa data a gente já tem.

[39:05] Mariana: Exatamente. Para o Sabor Serrano, primeiro trimestre de 2027. Para a 3.2, ainda sem data.

[39:11] Tatiane: Eu vou mandar a gravação e a transcrição no canal, para quem quiser conferir.

[39:18] Mariana: Obrigada, Tati. E alguém faz a ata? Eu faria, mas hoje estou com o dia cheio de entrevistas.

[39:26] Tatiane: Eu passo a transcrição para a ferramenta de resumo e reviso.

[39:31] Mariana: Perfeito. Obrigada, gente. Boa semana para todo mundo.

[39:34] Júlio: Boa semana. E Diego, quarta tem jogo de novo. Desta vez você assiste até o fim.

[39:42] Diego: Só se você prometer não reclamar do juiz.

[39:45] Júlio: Isso eu não posso prometer.

[39:48] Priscila: Tchau, gente!

[39:49] Mariana: Tchau.
