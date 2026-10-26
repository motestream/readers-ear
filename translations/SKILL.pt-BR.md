# readers-ear (tradução em português do Brasil, para consulta)

> Esta tradução serve só para consulta. Os agentes carregam somente o original em inglês, [`plugin/skills/readers-ear/SKILL.md`](../plugin/skills/readers-ear/SKILL.md); em caso de divergência, vale a versão em inglês. Tradução feita com base na versão em inglês de 25 de outubro de 2026.

```yaml
---
name: readers-ear
description: Revisa textos, da estrutura à redação, para que soem naturais ao leitor a quem se destinam, em qualquer idioma ou gênero. Use sempre que escrever textos que serão lidos por outras pessoas além do usuário (e-mails, artigos, documentos, posts, slides, discursos, ficção, traduções, textos de interface), mesmo que o usuário não peça revisão; sempre que o usuário pedir para revisar ou aprimorar um texto, ou para deixá-lo mais natural ou com menos cara de IA; e em todo texto se as instruções salvas do usuário assim indicarem.
---
```

# Reader's Ear

O objetivo é que o texto pareça escrito por alguém que domina o idioma e o gênero em questão, para o leitor a quem ele se destina. A referência é esse leitor, não regras: não se baseie em listas de palavras ou padrões proibidos e mantenha as fórmulas que o gênero ou a convenção exigem. Julgue o texto pelas normas do idioma em que ele está escrito, não pelas do idioma destas instruções (no original, o inglês) nem pelas do idioma em que você pensa. Os textos de exemplo e os guias de estilo do usuário têm prioridade sobre qualquer orientação destas instruções.

## Revisão padrão

Leia o texto como o leitor a quem ele se destina o leria pela primeira vez. Depois, avalie o todo antes das partes: primeiro, o que o texto precisa dizer a esse leitor e se, pelas normas do gênero, a estrutura dele ajuda a dizê-lo (o que vem primeiro, como as partes se agrupam e se ordenam, para que serve cada uma); só então os parágrafos, as frases e as palavras. Frases bem polidas não salvam uma estrutura que não funciona, e reconstruir a estrutura acaba por mudá-las de qualquer forma.

Mude só o que você conseguir apontar como um problema concreto: algo que faria o leitor travar, perder o fio ou não encontrar aquilo de que precisa no momento em que precisa, ou algo que alguém que domina esse idioma e esse gênero não teria escrito assim. Corrija cada problema no nível em que ele ocorre, da palavra ao texto inteiro; às vezes, a solução é cortar. Retocar frase por frase não muda a estrutura. Por isso, quando o problema estiver na estrutura, liste os fatos e as ideias que o texto precisa transmitir e a finalidade dele e, a partir dessa lista, reconstrua o trecho afetado ou o texto inteiro, na ordem e na forma de que esse leitor precisa. Depois, compare o resultado com o original para detectar qualquer fato ou ideia que a reconstrução tenha perdido ou alterado, e qualquer afirmação que tenha acrescentado. Mantenha uma mudança só se ela melhorar o texto, e pare quando não conseguir apontar outro problema. Um texto que já está bom deve sair praticamente inalterado. Ajuste o esforço à extensão e à importância do texto.

Dois tipos de problema passam despercebidos com facilidade. Um é a interferência de outros idiomas que não o do texto, inclusive daqueles que não aparecem nem no material recebido nem no seu raciocínio. Ela se manifesta como marcas de outro idioma na ordem das palavras, nas construções, nas combinações usuais de palavras, nas expressões idiomáticas, na pontuação e nas aspas, nos formatos de números e datas ou nas formas de tratamento; como palavras estrangeiras que esse leitor não usaria; ou como mistura de grafias, sistemas de escrita ou vocabulário de regiões diferentes. O outro é depender de um contexto que o leitor nunca viu, como a sua conversa com o usuário.

Seja qual for o texto que você revisar:

- No texto fornecido pelo usuário, preserve os fatos, as ideias e a voz de quem o escreveu, e não mude mais do que o pedido exige. Aponte os erros ou ambiguidades que afetem o sentido, em vez de corrigi-los. Um pedido geral, como revisar ou aprimorar o texto ou deixá-lo mais natural, inclui a estrutura; um pedido mais restrito, como corrigir erros de digitação ou de gramática, não a inclui; nesse caso, aponte os problemas de estrutura em vez de corrigi-los. Uma tradução mantém a estrutura do original, a menos que o usuário peça para adaptar essa estrutura.
- Não invente fatos, números nem citações para deixar o texto mais concreto; aponte a lacuna ou pergunte.
- Se não confiar no seu julgamento quanto ao idioma ou ao assunto, mude menos e avise.
- Entregue o texto pronto e o que o usuário precisar saber, como os pontos que você só assinalou, sem corrigir. Se tiver reestruturado um texto fornecido pelo usuário, explique em uma ou duas frases o que mudou e por quê. Não inclua suas anotações de trabalho nem rascunhos, a menos que o usuário peça.

## Revisão cuidadosa

Faça esta revisão só quando o usuário pedir explicitamente uma revisão mais lenta e minuciosa do que o normal, porque ela consome bem mais tempo e tokens. Ela acrescenta à revisão padrão leituras externas, feitas antes de você formar a sua própria opinião sobre o texto, para que essa opinião não as influencie. Siga esta ordem:

1. Antes de procurar problemas por conta própria, abra dois contextos novos que não tenham visto a sua conversa, como subagentes recém-criados (não cópias deste contexto); eles podem trabalhar ao mesmo tempo. Não conte a nenhum dos dois o que você observou ou suspeita sobre o texto.
   - Pesquisador de referências: informe o idioma do texto, o público a que ele se destina, o gênero, a finalidade em termos gerais e os critérios de fontes abaixo, mas não entregue o texto. Peça que ele encontre alguns textos do mesmo gênero e com a mesma finalidade que atendam a esses critérios; que leia as páginas em si, e não só os trechos exibidos nos resultados de busca; que liste as páginas usadas; e que resuma como esses textos são escritos: estrutura, fórmulas fixas, extensão, registro e o que mais o gênero exigir.
   - Leitor sem contexto: entregue somente o texto e uma nota sobre o público e a finalidade. Peça que ele leia o texto como esse público leria, aponte onde trava ou perde o fio e diga qual entende ser a ideia principal.
2. Com os dois relatórios em mãos, leia você mesmo o texto e liste os problemas.
3. Confira os pontos que mais importam para o leitor e aqueles de que você tem menos certeza (grafia, pontuação, termos, fatos etc.) em fontes atuais e confiáveis, como dicionários, manuais de redação e estilo e páginas oficiais.
4. Revise como na revisão padrão. Use as referências como parâmetro para avaliar o texto, não como modelo a ser copiado; no texto fornecido pelo usuário, os fatos, as ideias e a voz de quem o escreveu continuam em primeiro lugar.

Critérios para as fontes das etapas 1 e 3: use fontes no idioma do texto cuja redação tenha sido verificada por uma pessoa ou organização que se responsabilize por ela.

- Não use traduções, por melhores que sejam, porque elas podem trazer marcas do idioma de origem. Isso inclui as versões traduzidas de páginas de sites multilíngues.
- Para a forma de dizer e as convenções do gênero, use textos do mesmo gênero e com a mesma finalidade, como as páginas que órgãos públicos, grandes empresas e editoras conceituadas publicam originalmente naquele idioma; os textos de autores reconhecidos no gênero; e os textos reunidos em corpora. Entre essas fontes, os textos mais seguros são os anteriores à difusão da IA generativa (por volta de 2022); textos posteriores também servem quando fica claro que um editor ou uma instituição se responsabiliza por eles.

Se não for possível abrir contextos novos, deixe de lado o leitor sem contexto, busque e leia você mesmo as referências antes de procurar problemas e depois siga a partir da etapa 2.

Conte brevemente ao usuário o que você consultou e o que isso mudou, e diga se alguma etapa não pôde ser feita, como as leituras em contextos novos ou as buscas. Nunca diga que fez uma etapa que pulou.

## Escopo

O escopo define apenas o que você revisa por iniciativa própria; você sempre revisa o que o usuário pedir. Há dois escopos:

- A (padrão): os textos que você escreve e cujos leitores finais são outras pessoas que não o usuário.
- B: todo texto que você escrever.

Se suas instruções ou sua memória não definirem um escopo, use A e, depois de entregar o texto, pergunte uma única vez ao usuário se prefere B. Não faça a pergunta quando essa escolha não couber ao usuário (por exemplo, se ele for o usuário final de um produto de terceiros), quando você estiver trabalhando como subagente ou sem supervisão, ou quando não houver um lugar adequado para salvar a resposta (veja abaixo).

Quando o usuário responder ou, mais tarde, mudar o escopo, registre a escolha em uma frase que cite esta skill e o escopo, escrita no idioma do usuário (por exemplo, "Use a skill readers-ear em todo texto que você escrever." ou "Use a skill readers-ear nos textos que você escrever para outras pessoas lerem."). Salve essa frase em um lugar pessoal que todas as sessões futuras carreguem, como um arquivo de instruções no nível do usuário ou a memória da conta. Não use arquivos compartilhados com uma equipe, memória restrita a um projeto nem lugares onde a frase pode ser salva, mas não será carregada da próxima vez, como um ambiente descartável na nuvem. Diga ao usuário onde a salvou. Se não houver um lugar assim, aplique a escolha só nesta conversa, avise e dê ao usuário a frase, para que ele a cole nas próprias instruções.
