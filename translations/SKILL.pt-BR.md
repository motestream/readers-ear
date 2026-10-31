# readers-ear (tradução em português do Brasil, para consulta)

> Esta tradução serve só para consulta. Os agentes carregam somente o original em inglês, [`plugin/skills/readers-ear/SKILL.md`](../plugin/skills/readers-ear/SKILL.md); em caso de divergência, vale a versão em inglês. Tradução feita com base na versão em inglês de 31 de outubro de 2026.

## Nome e descrição

Esta seção traduz o `name` e a `description` que ficam no início do arquivo em inglês. A descrição diz ao agente quando usar a skill.

- **Nome:** `readers-ear`
- **Descrição:** Escreve e revisa textos, em qualquer idioma e gênero, de modo que soem naturais para o leitor a quem se destinam. Use a skill:
  - ao escrever textos que outras pessoas além do usuário vão ler, como e-mails, artigos, documentos, posts, slides, discursos, ficção, traduções, textos de interface, mensagens de commit e descrições de PR;
  - ao relatar ao usuário o trabalho feito, seja na resposta final depois de trabalhar no pedido dele, seja em um documento feito para ele ler;
  - quando o usuário pedir para revisar ou aprimorar um texto, ou para deixá-lo mais natural ou com menos cara de IA;
  - em todos os textos que o agente escrever, se as instruções salvas do usuário assim indicarem.

  Nos dois primeiros casos, use a skill mesmo que o usuário não tenha pedido ajuda com a redação.

A seguir está a tradução do corpo das instruções.

# Reader's Ear

Faça com que o texto que você escreve ou revisa pareça escrito por alguém que domina o idioma e o gênero em questão, para o leitor a quem ele se destina.

## O critério

Avalie o texto tendo como critério o leitor a quem ele se destina, e não regras. Pergunte-se o que esse leitor já sabe, o que ele precisa encontrar no texto, qual é a relação dele com quem escreve e o que ele espera do gênero e do idioma do texto. Se uma palavra, uma frase ou uma forma de organizar o texto funciona ou não depende dessas respostas; por isso, a mesma escolha pode estar certa em um texto e errada em outro. Mantenha as expressões fixas que o gênero pede, mesmo quando parecerem fórmulas prontas.

Para descobrir o que esse leitor já sabe, separe o que ele viu do que só você sabe. Quando o leitor é o usuário, o que ele viu na conversa se resume às mensagens que ele mesmo enviou, às respostas finais que você deu aos pedidos dele e aos documentos que você preparou para ele. Considere todo o resto como algo que ele não viu, inclusive o que você escreveu na conversa enquanto trabalhava para chegar a uma resposta, o seu raciocínio, a saída das ferramentas, os relatórios dos subagentes e os nomes que você deu às coisas durante o trabalho. Fora da conversa, o usuário conta com o que sabe do próprio trabalho e da própria área.

Julgue o texto pelas normas do idioma em que ele está escrito, e não pelas do inglês (o idioma original destas instruções) nem pelas do idioma em que você pensa.

Os textos de exemplo e os guias de estilo fornecidos pelo usuário têm prioridade sobre esta skill. Se o usuário não tiver dito quem é o leitor, deduza isso do texto e do pedido.

## Escrever um texto novo

Siga estas orientações quando você mesmo escrever um texto a partir das informações que tem, inclusive ao traduzir.

Antes de redigir, responda, para esse leitor, às perguntas de “O critério”. Defina para que ele vai ler o texto (por exemplo, para tomar uma decisão, executar um comando, saber em que pé estão as coisas ou se entreter com uma história) e, a partir dessa finalidade, o que ele precisa tirar do texto e o que precisa encontrar primeiro. Escolha a organização que o gênero e esse leitor esperam; em uma tradução, mantenha a organização do original (a ordem das seções e dos pontos), a menos que o usuário peça para adaptá-la. Depois, escreva o rascunho para esse leitor, seguindo as normas do idioma e do gênero do texto.

Depois de redigir, leia o rascunho uma vez como o leitor dele o leria e corrija os problemas concretos que encontrar, seguindo os critérios e os métodos de “Revisar um texto”. Se o rascunho já estiver bom, deixe-o como está.

## Revisar um texto

Siga este procedimento para revisar um texto já existente.

Leia o texto como o leitor a quem ele se destina o leria ao vê-lo pela primeira vez. Só conta como problema aquilo que você consegue apontar:

- um ponto em que esse leitor tropeçaria, perderia o fio ou não encontraria aquilo de que precisa no momento em que precisa;
- um ponto que alguém que domina o idioma e o gênero do texto não escreveria daquele jeito, e para o qual você consegue dizer como essa pessoa o escreveria;
- um trecho que não dá a esse leitor nada de que ele precise.

Para avaliar o último caso, pergunte-se se, sem esse trecho, o texto atenderia pior à finalidade desse leitor.

Os problemas aparecem em todos os níveis: uma palavra, uma frase, um trecho ou a organização do texto inteiro. Examine todos os níveis.

Corrija cada problema no nível em que ele ocorre. Corte os trechos que não dão a esse leitor nada de que ele precise; em um texto fornecido pelo usuário, faça isso só quando o pedido for geral (veja “Textos fornecidos pelo usuário”) e diga o que cortou. Em uma tradução, mantenha tudo o que o original diz e mantenha também a organização dele, a menos que o usuário peça para adaptá-la. Corrija um problema de organização reconstruindo o texto, e não reformulando frases: liste o que o texto precisa transmitir, reconstrua a parte afetada na ordem de que o leitor precisa e compare a parte reconstruída com o original para ver se algo se perdeu, mudou ou foi acrescentado.

Mude o texto apenas para corrigir problemas concretos e só mantenha uma correção se o texto ficar melhor com ela. Pare quando não restar nenhum problema concreto; assim, um texto bom sai praticamente inalterado. Dedique ao texto um tempo proporcional à extensão e à importância dele.

## Dois problemas a verificar

Ao ler um rascunho ou um texto como o leitor dele, procure especificamente estes dois problemas.

**Interferência de outros idiomas.** Outros idiomas deixam marcas no texto, mesmo aqueles que não aparecem em nenhum ponto do material recebido nem do seu raciocínio. Procure os sinais, em vez de tentar identificar o idioma de origem: ordem das palavras, construções, combinações de palavras, expressões idiomáticas, pontuação e aspas, formatos de números e datas ou formas de tratamento trazidos de outro idioma. Procure também palavras estrangeiras que esse leitor não usaria e misturas de grafias, sistemas de escrita ou vocabulário de regiões diferentes.

**Contexto que o leitor não viu.** Procure pontos que dependem de algo que o leitor não viu (veja “O critério”), como a sua conversa com o usuário, anotações que o leitor não tem ou nomes que você deu às coisas durante o trabalho. Para cada nome, cada termo e cada referência a algo anterior, pergunte-se onde esse leitor teria aprendido aquilo. Se não conseguir apontar o lugar, diga a mesma coisa com palavras que esse leitor conhece, como as que ele mesmo usou, ou, se ele precisar do termo, explique-o onde ele aparece pela primeira vez.

## Textos fornecidos pelo usuário

Ao revisar ou traduzir um texto fornecido pelo usuário:

- Mantenha os fatos, as ideias e a voz de quem escreveu o texto, e não mude mais do que o pedido exige.
- Entenda que um pedido geral (revisar, aprimorar, deixar o texto mais natural ou com menos cara de IA) abrange todos os níveis. Um pedido restrito, como corrigir erros de digitação, não abrange problemas maiores: aponte, em vez de corrigir, os que enganariam ou confundiriam o leitor, como erros factuais, e não faça sugestões de estilo.
- Aponte, em vez de corrigir, os erros factuais e qualquer ambiguidade que só se resolveria adivinhando a intenção de quem escreveu. Uma incoerência que você consegue resolver com os próprios fatos do texto, como uma instrução que contradiz um horário informado no texto, é um problema a corrigir, não a apontar.

## Em todas as tarefas

- Use apenas os fatos, os números e as citações que você tem. Há uma única exceção: quando o texto fornecido pelo usuário traz só generalidades e o pedido inclui deixá-lo mais natural ou com menos cara de IA, você pode acrescentar informações gerais corretas e amplamente conhecidas, como o funcionamento de uma técnica comum. Nunca acrescente experiências, dados, citações nem afirmações sobre o usuário ou a organização dele. Liste tudo o que tiver acrescentado.
- Se faltar alguma informação, pergunte ao usuário e escreva a frase que depende dela com um marcador entre colchetes no lugar da informação, para que o texto fique pronto assim que o usuário preencher o marcador. Quando não puder perguntar, como ao trabalhar de forma autônoma, marque a lacuna no texto da mesma forma.
- Se não tiver segurança no seu julgamento quanto ao idioma ou ao assunto, mude menos e avise.
- Entregue o texto pronto e o que o usuário precisa saber, incluindo os pontos que você apontou em vez de corrigir e, se tiver reorganizado o texto do usuário, uma frase explicando por quê. Deixe de fora anotações de trabalho e rascunhos, a menos que o usuário os peça.

## Modo cuidadoso

Use o modo cuidadoso só quando o usuário pedir explicitamente um trabalho mais lento e minucioso, na conversa ou nas instruções salvas dele, porque esse modo consome muito mais tempo e tokens. No modo cuidadoso, antes de avaliar o texto por conta própria, você pede a dois contextos novos um olhar de fora sobre ele. Contextos novos são aqueles que não viram a conversa, como subagentes recém-criados, e não cópias nem forks do contexto atual. Passe a cada um só o que está listado abaixo, sem nenhuma observação ou suspeita sua sobre o texto.

- **Leitor de referências.** Informe a ele o idioma do texto, o leitor a quem se destina e o gênero, uma ideia geral da finalidade do texto e as regras para as fontes descritas abaixo, mas não o texto. Peça que encontre alguns textos do mesmo gênero e com a mesma finalidade que atendam a essas regras e que os leia por inteiro, em vez de se basear nos trechos exibidos nos resultados de busca. Ele informa quais fontes usou e como esses textos são escritos: estrutura, expressões fixas, extensão, registro e o que mais o gênero esperar.
- **Leitor sem contexto.** Passe a ele só o texto e uma nota sobre o leitor e a finalidade do texto; no caso de uma tradução, passe a tradução, não o original. Peça que ele leia o texto como o leitor a quem o texto se destina o leria. Ele informa onde tropeça ou perde o fio e o que entende ser a ideia principal.

Em seguida, siga estas etapas:

1. **Obtenha os dois relatórios.** Ao revisar, inicie os dois leitores ao mesmo tempo. Ao escrever um texto novo, inclusive uma tradução, acione primeiro o leitor de referências e redija com o relatório dele em mãos. Depois, entregue o rascunho terminado diretamente ao leitor sem contexto, sem fazer a leitura descrita em “Escrever um texto novo”; você mesmo lê o texto na etapa 2. Se não for possível usar contextos novos, pule a leitura sem contexto e encontre e leia você mesmo as referências. Ao revisar, faça isso antes de procurar problemas; ao escrever um texto novo, antes de redigir.
2. **Leia você mesmo o texto.** Com os relatórios em mãos, leia o texto e liste os problemas dele. Trate os relatórios como indícios a confrontar com a sua própria leitura, e não como uma lista de mudanças a fazer.
3. **Confira nas fontes.** Confira os termos, os nomes, os números e as grafias de que o texto depende, e qualquer ponto de que você não tenha certeza, em fontes atuais e confiáveis, como dicionários, manuais de redação e estilo e sites oficiais. Como o texto do usuário pode ser confidencial, faça as buscas com termos, nomes e expressões curtas, e não com trechos do texto.
4. **Revise.** Trabalhe como em “Revisar um texto”. Use as referências como parâmetro para avaliar o texto, e não como modelo a copiar. No texto do usuário, os fatos, as ideias e a voz de quem o escreveu têm prioridade sobre as referências.
5. **Informe.** Conte brevemente ao usuário o que você consultou e o que isso mudou, e cite todas as etapas que pulou ou não conseguiu fazer.

**Regras para as fontes** (etapas 1 e 3). Use fontes escritas originalmente no idioma do texto, cuja redação tenha sido revisada por uma pessoa ou organização que responda por ela. Traduções, inclusive as páginas traduzidas de sites multilíngues, não servem, porque podem trazer os padrões do idioma de origem. A única exceção a essa regra está na etapa 3: para conferir como uma organização escreve os próprios nomes e termos, você pode usar as páginas oficiais dela no idioma do texto. Para a redação e as convenções do gênero, use textos do mesmo gênero e com a mesma finalidade, como:

- páginas de instituições públicas, grandes empresas, principais veículos de imprensa e editoras consagradas;
- obras de autores respeitados no gênero;
- textos de *corpora* com curadoria.

Não use textos cuja redação aparentemente ninguém revisou, como páginas anônimas, sites que produzem artigos em massa e resumos gerados automaticamente.

## Escopo

O escopo só importa quando ninguém pediu que você usasse esta skill: ele define a quais textos você aplica a skill por iniciativa própria. Seja qual for o escopo, sempre revise o que o usuário pedir para revisar. Há três escopos:

- **Textos para outras pessoas e relatórios ao usuário** (o padrão): os textos para outras pessoas, conforme a definição abaixo, e os seus relatórios ao usuário. Um relatório é a sua resposta final a um pedido que o usuário faz diretamente a você, quando você precisou trabalhar para respondê-lo (por exemplo, lendo arquivos, executando comandos ou delegando tarefas a subagentes), ou então um documento ou outro material que você prepara para o usuário ler. O que você escreve na conversa enquanto trabalha para chegar à resposta final não é um relatório, e uma resposta curta que você pode dar só com base na conversa também não.
- **Textos para outras pessoas**: os textos que você escreve e cujos leitores finais são outras pessoas que não o usuário.
- **Todos os textos**: todos os textos que você escreve.

Se nenhum escopo estiver definido nas suas instruções ou na sua memória, use o padrão. Depois de entregar o primeiro texto dentro do escopo padrão, e se todas as condições abaixo forem atendidas, pergunte ao usuário se ele quer manter esse escopo, aplicar a skill a todos os textos que você escreve ou aplicá-la só aos textos para outras pessoas:

- Você está trabalhando com o usuário de forma interativa, e não como subagente nem de forma autônoma.
- O usuário pode fazer essa escolha. O usuário final de um produto de terceiros, por exemplo, não pode.
- Há um lugar adequado para salvar a resposta.

Faça essa pergunta uma única vez, e não uma vez por sessão. Se o usuário seguir adiante sem responder, trate isso como uma escolha do padrão e salve essa escolha como descrito abaixo, para que nenhuma sessão futura volte a perguntar.

Quando o usuário responder ou, mais tarde, mudar o escopo, salve a escolha em uma frase no idioma do usuário que cite a skill e o escopo. Em português, por exemplo: “Use a skill readers-ear nos textos que você escrever para outras pessoas lerem e nas respostas finais e nos documentos que fizer para mim”, “Use a skill readers-ear em todos os textos que você escrever” ou “Use a skill readers-ear só nos textos que você escrever para outras pessoas lerem”.

Salve a frase em um lugar pessoal que todas as sessões futuras carreguem, como um arquivo de instruções no nível do usuário ou a memória da conta, e não em um arquivo compartilhado com uma equipe, em uma memória restrita a um projeto ou em um lugar que não será carregado da próxima vez, como um ambiente descartável na nuvem. Diga ao usuário onde a salvou. Se o usuário mudar o escopo onde não houver um lugar assim, aplique a escolha só à conversa atual, avise o usuário disso e dê a ele a frase para colar nas próprias instruções.

Quando aplicar a skill sem que ninguém tenha pedido, trabalhe só nos textos que você mesmo escreve e deixe como estão os textos de outras pessoas, mesmo que estejam no mesmo arquivo. Se estiver aplicando a skill dentro de outra tarefa, como escrever uma mensagem de commit ou um relatório ao usuário, entregue o texto como essa tarefa exige e mencione só o que o usuário precisa saber.
