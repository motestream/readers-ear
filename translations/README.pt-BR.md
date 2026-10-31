# Reader's Ear

[English](../README.md) · [日本語](README.ja.md) · [简体中文](README.zh-Hans.md) · [한국어](README.ko.md) · [Español](README.es.md) · [Français](README.fr.md) · [Deutsch](README.de.md) · **Português (Brasil)**

Reader's Ear é uma [Agent Skill](https://agentskills.io) que faz um agente de IA escrever e revisar textos, em qualquer idioma e gênero, de modo que soem naturais para o leitor a quem se destinam. Em vez de listas de palavras a evitar, a skill dá ao agente um modo de trabalhar. Você pode instalá-la no Claude (Claude Code, claude.ai, Claude Desktop e Cowork) e em outros agentes, como Codex, Cursor, Gemini CLI e GitHub Copilot.

## Por que um método, e não regras

Muitas skills do tipo “humanizer” partem de regras: listas de palavras e padrões que soam como IA. As regras têm desvantagens:

- Costumam ser escritas para um único idioma e não se aplicam a outros.
- Impõem escolhas erradas para certos fins, como proibir uma expressão que um contrato ou um e-mail corporativo exige.
- Põem um teto nos resultados: por mais que os modelos melhorem, o texto gerado não pode ser melhor do que as regras.

Reader's Ear parte do princípio de que o modelo já sabe distinguir um texto bom de um ruim em qualquer idioma e de que o que lhe falta é um modo de trabalhar, não regras. Por isso, a skill traz apenas um método que funciona em todos os idiomas e deixa o julgamento a cargo do modelo; assim, um modelo melhor dá resultados melhores.

## O que a skill faz

As instruções completas estão no [`SKILL.md`](../plugin/skills/readers-ear/SKILL.md) (há uma tradução para o português em [`SKILL.pt-BR.md`](SKILL.pt-BR.md)). Em resumo:

- **Escrita.** Quando escreve um texto novo, o agente primeiro descobre quem vai lê-lo, o que essa pessoa já sabe e com que objetivo vai ler, e escreve para ela desde o primeiro rascunho. Depois, lê o rascunho uma vez como esse leitor e corrige o que encontrar.
- **Revisão.** O agente lê o texto como o leitor a quem ele se destina o leria e corrige só problemas concretos, onde quer que estejam, de uma única palavra à organização do texto inteiro. Preserva os fatos, as ideias principais e a voz do seu texto, e devolve praticamente inalterado um texto que já está bom. Ele aponta erros factuais e problemas que vão além do que você pediu, em vez de corrigi-los.
- **Problemas que passam despercebidos.** Ao escrever e ao revisar, o agente procura em especial marcas de outros idiomas, como a ordem das palavras ou o formato de datas trazidos de outra língua, e trechos que dependem de um contexto que o leitor não viu, como a conversa do agente com você ou nomes que ele deu às coisas durante o trabalho.
- **Modo cuidadoso.** Um modo de trabalhar mais lento e minucioso, que traz olhares de fora e só é usado quando você pede, porque consome muito mais tempo e tokens. Antes de o agente avaliar o texto por conta própria, duas instâncias de IA recém-criadas (por exemplo, subagentes) ajudam: uma reúne textos de referência do mesmo gênero sem ver o seu texto, e a outra lê o texto sem nenhum contexto prévio. Em seguida, o agente confere as formulações e os fatos mais importantes em fontes escritas originalmente no idioma do texto (e não em traduções) e revisa o texto. Por fim, informa o que consultou e qualquer etapa que tenha pulado.
- **Escopo.** Por padrão, a skill atua, sem que você peça, nos textos que o agente escreve para outras pessoas e nos relatórios que ele faz para você: a resposta final a um pedido em que ele trabalhou e os documentos que prepara para você ler. Você pode ampliar o escopo para tudo o que o agente escreve ou limitá-lo aos textos para outras pessoas (veja “Uso”).

## Segurança

Reader's Ear consiste apenas em instruções, sem scripts, hooks nem servidores MCP. Além do texto em que o agente está trabalhando, a única coisa que a skill salva é uma frase que registra a sua escolha de escopo. Quando você escolhe ou muda o escopo, ou deixa sem resposta a pergunta que o agente faz sobre o escopo, a skill salva essa frase no seu arquivo pessoal de instruções (por exemplo, um `CLAUDE.md` no nível do usuário) ou na memória da sua conta e informa onde salvou.

No modo cuidadoso, o agente também cria novas instâncias de IA, como subagentes, e busca e lê textos de referência e outras fontes, como páginas da web. Nas buscas, ele usa termos, nomes e expressões curtas, e não trechos do seu texto.

## Instalação

Se você usa tanto o claude.ai quanto o Claude Code, confira isto primeiro: o Claude Code carrega as skills da sua conta no claude.ai nas sessões na nuvem e, na versão 2.1.273 ou posterior, nas sessões de terminal em que você fez login com essa conta usando `/login`. Se é assim que você usa o Claude Code, basta enviar a skill em um ZIP para o claude.ai; instalar também o plugin faria o Claude Code carregar a skill duas vezes.

Caso contrário, escolha o método de acordo com onde você usa o agente:

| Onde você usa o agente | Método recomendado |
| --- | --- |
| Claude Code na sua própria máquina | [Plugin do Claude Code](#plugin-do-claude-code) |
| claude.ai, Claude Desktop, Cowork ou Claude Code na web | [Upload de um ZIP para a sua conta no claude.ai](#claudeai-claude-desktop-e-cowork) |
| Codex, Cursor, Gemini CLI, GitHub Copilot e outros agentes | [`npx skills`](#outros-agentes) |

### Plugin do Claude Code

Em uma sessão do Claude Code, execute:

```
/plugin marketplace add motestream/readers-ear
/plugin install readers-ear@readers-ear
```

O primeiro comando adiciona este repositório como marketplace de plugins. O segundo instala o plugin `readers-ear` a partir desse marketplace; o marketplace e o plugin têm o mesmo nome.

No Claude Code 2.1.275 ou posterior, um único comando faz as duas coisas:

```
/plugin install readers-ear --marketplace motestream/readers-ear
```

**Para atualizar**, execute `/plugin marketplace update readers-ear` ou ative a atualização automática deste marketplace na aba **Marketplaces** do `/plugin`.

**Para compartilhar com uma equipe**, abra um terminal na raiz do repositório do projeto e execute:

```sh
claude plugin marketplace add motestream/readers-ear --scope project
```

Depois, faça o commit do `.claude/settings.json` gerado pelo comando. Quando o Claude Code perguntar aos colegas se confiam na pasta do projeto, os que responderem que sim passam a ter o marketplace e podem instalar o plugin a partir dele.

**Nas sessões na nuvem** (Claude Code na web), os plugins instalados na sua própria máquina não são carregados. Para essas sessões, em vez disso, você pode enviar a skill para o claude.ai ou copiar a pasta `plugin/skills/readers-ear/` de um clone ou de um download em ZIP deste repositório para o `.claude/skills/` do projeto e fazer o commit.

### claude.ai, Claude Desktop e Cowork

1. Verifique se a execução de código está ativada, porque as skills precisam dela. Nos planos Free, Pro e Max, essa opção fica em **Settings > Capabilities**. Nos planos Team, a execução de código e o recurso Skills vêm ativados por padrão para a organização. Nos planos Enterprise, cabe a um proprietário da organização garantir que os dois estejam ativados em **Organization settings > Plugins & skills**, na aba **Policy**.
2. Baixe este repositório como ZIP (no GitHub, **Code** > **Download ZIP**) e descompacte-o.
3. Compacte a pasta `plugin/skills/readers-ear` em um novo ZIP, de modo que ele contenha uma pasta `readers-ear` com o `SKILL.md` dentro. O nome da pasta precisa continuar sendo `readers-ear`.
4. No claude.ai, abra **Customize > Skills**, selecione **+**, depois **Create skill** > **Upload a skill** e escolha o ZIP.

A partir daí, a skill pertence à sua conta; por isso, o Claude Desktop e o Cowork também a usam, assim como o Claude Code, nas condições descritas no início da seção [Instalação](#instalação). Os proprietários de organizações Enterprise também podem enviar a skill para disponibilizá-la a todos os membros.

**Para atualizar**, exclua a versão antiga em **Customize > Skills** e envie o novo ZIP.

### Outros agentes

Este método exige o Node.js. Execute:

```sh
npx skills add motestream/readers-ear -g
```

A flag `-g` instala a skill globalmente, para todos os seus projetos; sem ela, a skill é instalada só no projeto atual. O comando detecta os agentes instalados na sua máquina e pergunta para quais instalar. Para escolher um de antemão, acrescente `-a`, como em `-a codex`.

**Para atualizar**, execute `npx skills update`.

**Com o GitHub CLI 2.90 ou posterior**, outra opção é o `gh skill`, que está em versão prévia:

```sh
gh skill install motestream/readers-ear readers-ear --scope user
```

O comando pergunta para qual agente instalar, ou você pode indicar um com `--agent`. Para atualizar, execute `gh skill update`.

**Para instalar manualmente**, copie a pasta `plugin/skills/readers-ear/` de um clone ou de um download em ZIP deste repositório para o diretório de skills do agente, como `~/.claude/skills/` no Claude Code.

## Uso

A skill entra em ação sozinha quando o agente escreve textos para outras pessoas ou relatórios para você. Você também pode acioná-la com um pedido nas suas próprias palavras, como “Deixe este texto mais natural”, ou chamá-la pelo nome com `/readers-ear` (`/readers-ear:readers-ear`, se você a instalou como plugin do Claude Code).

**Modo cuidadoso.** O agente só usa esse modo quando você pede explicitamente, por exemplo: “Sem pressa, revise este texto com cuidado” ou “Sem pressa, escreva isto com cuidado”. Para que ele seja usado sempre, diga isso nas suas instruções salvas, como um `CLAUDE.md`.

**Limitar as mudanças.** Diga ao agente a que ele deve se limitar, por exemplo: “Corrija só os erros de digitação”. Nesse caso, ele aponta os outros problemas em vez de corrigi-los.

**Escopo.** O padrão abrange os textos para outras pessoas e os relatórios do agente para você: a resposta final a um pedido que exigiu trabalho dele, como ler arquivos ou executar comandos, e os documentos que ele prepara para você ler. Não abrange o que o agente escreve enquanto trabalha para chegar à resposta final nem as respostas curtas que ele pode dar só com base na conversa. Em uma sessão interativa em que seja possível salvar configurações, depois de entregar o primeiro texto dentro do escopo padrão, o agente pergunta, uma única vez, se deve manter o padrão, aplicar a skill a tudo o que escreve ou limitá-la aos textos para outras pessoas. Se você não responder, ele mantém o padrão e salva essa escolha, para não perguntar de novo. Para mudar o escopo depois, peça ao agente. Onde não for possível salvar configurações, o agente não faz a pergunta; se você pedir que ele mude o escopo nesse caso, a mudança vale só para a conversa atual, e o agente fornece uma frase para você acrescentar às suas próprias instruções, para que as próximas sessões a levem em conta.

## Como testar

Antes de confiar na skill, faça estes testes:

- Compare o resultado com e sem a skill no mesmo modelo, de preferência em vários idiomas e em gêneros com expressões fixas, como e-mails corporativos, cláusulas de contrato e textos de interface.
- Peça ao agente que escreva algo para outras pessoas a partir das suas anotações. O que ele entregar já deve estar bom para o leitor, sem outra rodada de ajustes.
- Entregue a ele um texto que já esteja bom e peça uma revisão. O texto deve voltar praticamente inalterado.
- Passe a ele um texto com fatos corretos, mas em uma ordem difícil de acompanhar, e peça uma revisão. O agente deve reorganizar o texto e manter todos os fatos.
- Durante o trabalho de programação, verifique se a skill melhora as mensagens de commit, as descrições de PR e a documentação que o agente escreve, e se deixa intactos os textos já existentes de outras pessoas.
- Depois de uma tarefa de várias etapas, verifique se a resposta final do agente usa palavras que você conhece, e não nomes que ele inventou durante o trabalho, e se não é mais longa do que o necessário.

## Traduções

O agente carrega apenas o [`SKILL.md`](../plugin/skills/readers-ear/SKILL.md) em inglês. As traduções são para as pessoas lerem. Se uma tradução divergir do inglês, prevalece o texto em inglês.

| Idioma | README | Instruções da skill |
| --- | --- | --- |
| 日本語 | [README.ja.md](README.ja.md) | [SKILL.ja.md](SKILL.ja.md) |
| 简体中文 | [README.zh-Hans.md](README.zh-Hans.md) | [SKILL.zh-Hans.md](SKILL.zh-Hans.md) |
| 한국어 | [README.ko.md](README.ko.md) | [SKILL.ko.md](SKILL.ko.md) |
| Español | [README.es.md](README.es.md) | [SKILL.es.md](SKILL.es.md) |
| Français | [README.fr.md](README.fr.md) | [SKILL.fr.md](SKILL.fr.md) |
| Deutsch | [README.de.md](README.de.md) | [SKILL.de.md](SKILL.de.md) |
| Português (Brasil) | [README.pt-BR.md](README.pt-BR.md) | [SKILL.pt-BR.md](SKILL.pt-BR.md) |

## Como contribuir

- Quando o `SKILL.md` ou o README em inglês mudar, atualize as traduções correspondentes no mesmo commit, incluindo a data no início de cada tradução da skill.
- Teste as mudanças no `SKILL.md` em pelo menos três idiomas, um deles com poucos dados de treinamento, e com cada modelo compatível com o projeto. Verifique também como se comportam a pergunta sobre o escopo e o salvamento da resposta em uma execução não interativa (`claude -p`) e em uma sessão na nuvem.

## Licença

Este projeto está licenciado sob a [Licença MIT](../LICENSE).
