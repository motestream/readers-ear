# Reader's Ear

[English](../README.md) · [日本語](README.ja.md) · [简体中文](README.zh-Hans.md) · [한국어](README.ko.md) · [Español](README.es.md) · [Français](README.fr.md) · [Deutsch](README.de.md) · **Português (Brasil)**

Reader's Ear (`readers-ear`) é uma [Agent Skill](https://agentskills.io) que faz um agente de IA revisar um texto, em qualquer idioma e gênero, até que ele soe natural para o leitor a quem se destina.

## Por quê

A maioria das skills do tipo "humanizer" se baseia em regras: listas de palavras e padrões que soam como IA. Essa abordagem tem três desvantagens:

- As regras costumam ser escritas para um único idioma e não funcionam em outros.
- Regras fixas impõem escolhas erradas para certos fins.
- À medida que os modelos melhoram, as regras passam a ser o que limita o resultado.

Esta skill segue o caminho oposto. Ela parte da premissa de que a IA já é capaz o bastante para distinguir um texto bom de um ruim em qualquer idioma, e de que o que lhe falta não são regras, mas um modo de trabalhar. Por isso, a skill contém apenas princípios que valem em qualquer idioma: julgar o texto do ponto de vista de quem vai lê-lo; encontrar problemas concretos ao reler, a começar pela estrutura; corrigir cada um no nível certo (de uma palavra ao texto inteiro); e parar quando não restar nenhum problema concreto. Todo o resto fica a cargo do modelo; assim, um modelo melhor dá resultados melhores.

## O que ela faz

- **Revisão padrão**: relê o texto como o leitor faria, olhando a estrutura antes das frases, e corrige os problemas que consegue apontar. Quando o que falha é a estrutura, em vez de polir frases, ela lista o que o texto precisa transmitir, reconstrói o texto a partir dessa lista e garante que nenhum fato ou ideia se perdeu. Termina quando não consegue apontar mais nenhum problema; por isso, um texto que já está bom volta praticamente inalterado. O esforço varia conforme a extensão e a importância do texto. Você recebe o texto pronto, os eventuais pontos que ela só assinalou, sem corrigir, e uma breve explicação do que reestruturou.
- **Revisão cuidadosa** (só quando você pede, porque consome bem mais tempo e tokens): antes de o agente formar a própria opinião sobre o texto, duas novas instâncias de IA que não viram a sua conversa (por exemplo, subagentes) trabalham em paralelo. Uma delas procura na web textos do mesmo gênero e com a mesma finalidade, sem ver o seu, e resume como eles são escritos. A outra lê somente o seu texto e uma nota sobre o público e a finalidade, e aponta onde trava. Com os dois relatórios em mãos, o agente procura os problemas, confere os fatos e as formulações mais importantes e revisa o texto. Depois, informa o que consultou e se alguma etapa não pôde ser feita. As referências, como dicionários, corpora e documentos de órgãos públicos e grandes empresas, precisam ter sido escritas originalmente no idioma do texto e ter a redação revisada por uma pessoa ou organização que se responsabilize por ela; quanto às formulações, dá-se preferência a textos anteriores à difusão da IA generativa. Traduções nunca servem de referência, porque podem trazer marcas do idioma de origem.
- **Escopo**: por iniciativa própria, ela só revisa os textos que o agente escreve para outras pessoas. Onde for possível salvar configurações, pergunta a você uma única vez se deve passar a abranger tudo o que o agente escreve e salva a resposta onde as sessões futuras vão carregá-la.

## Instalação

Escolha o método de acordo com onde você vai usar a skill.

| Onde você usa | Método recomendado |
|---|---|
| Claude Code na sua própria máquina | [Plugin](#claude-code) a partir deste repositório |
| claude.ai, Claude Desktop, Cowork ou Claude Code na web | [Upload de um ZIP](#claudeai-claude-desktop-e-cowork) para a sua conta no claude.ai |
| Codex, Cursor, Gemini CLI, GitHub Copilot e outros agentes | [`npx skills`](#outros-agentes) |

Se você usa o claude.ai e o Claude Code, o envio do ZIP basta para os dois, porque o Claude Code carrega as skills da sua conta no claude.ai quando você faz login com ela. Não instale também o plugin, senão o Claude Code vai carregar duas cópias.

### Claude Code

Execute em uma sessão do Claude Code:

```
/plugin marketplace add motestream/readers-ear
/plugin install readers-ear@readers-ear
```

O primeiro comando adiciona este repositório como marketplace de plugins; o segundo instala o plugin `readers-ear` a partir desse marketplace (o marketplace e o plugin têm o mesmo nome). No Claude Code 2.1.275 ou posterior, um único comando faz as duas coisas: `/plugin install readers-ear --marketplace motestream/readers-ear`.

- **Atualizar**: execute `/plugin marketplace update readers-ear` ou ative a atualização automática deste marketplace em **Marketplaces**, no `/plugin`.
- **Compartilhar com uma equipe**: no repositório do seu projeto, execute `claude plugin marketplace add motestream/readers-ear --scope project` e faça o commit do `.claude/settings.json` gerado. Quando o Claude Code perguntar aos colegas se confiam na pasta do projeto, quem responder que sim passa a ter o marketplace e pode instalar o plugin a partir dele.
- **Sessões na nuvem** (Claude Code na web) não carregam os plugins que você instalou na sua própria máquina. Em vez disso, envie a skill para o claude.ai (próxima seção) ou copie `plugin/skills/readers-ear/` para o `.claude/skills/` do seu projeto e faça o commit.

### claude.ai, Claude Desktop e Cowork

Os nomes de menus e botões abaixo são os da interface em inglês.

1. Verifique se a execução de código está ativada. Nos planos Free, Pro e Max, essa opção fica em **Settings > Capabilities**; nos planos Team e Enterprise, um proprietário da organização a ativa, junto com o recurso Skills, em **Organization settings > Plugins & skills**.
2. Baixe este repositório e compacte a pasta `plugin/skills/readers-ear` em um ZIP, de modo que o ZIP contenha `readers-ear/SKILL.md`. A pasta precisa continuar se chamando `readers-ear`.
3. No claude.ai, abra **Customize > Skills**, selecione **+**, depois **Create skill** > **Upload a skill** e escolha o ZIP.

A partir daí, a skill pertence à sua conta, e por isso o Claude Desktop e o Cowork a usam também. O Claude Code (2.1.273 ou posterior) também a carrega quando você faz login com a mesma conta, inclusive nas sessões na nuvem. Para atualizá-la, exclua a versão antiga em **Customize > Skills** e envie o ZIP novo. Os proprietários de organizações Team e Enterprise podem disponibilizar a skill para todos os membros.

### Outros agentes

```
npx skills add motestream/readers-ear -g
```

`-g` instala para a sua conta de usuário; sem essa opção, a instalação vai para o projeto atual. O comando detecta os agentes que você tem e pergunta para quais instalar; para indicar um, acrescente `-a`, como em `-a codex`. Para atualizar, use `npx skills update`.

Com o GitHub CLI 2.90 ou posterior (o `gh skill` está em versão prévia), outra opção é executar `gh skill install motestream/readers-ear readers-ear --scope user`. O comando pergunta para qual agente instalar, ou você pode indicar um com `--agent`. Para atualizar, use `gh skill update`.

Para instalar manualmente, copie `plugin/skills/readers-ear/` para o diretório de skills do seu agente, como `~/.claude/skills/` no Claude Code.

## Uso

- A skill entra em ação sozinha sempre que o agente escreve textos para outras pessoas. Você também pode pedir diretamente ("deixe isto mais natural") ou chamá-la pelo nome: `/readers-ear`, ou `/readers-ear:readers-ear` quando instalada como plugin do Claude Code.
- Para uma revisão cuidadosa, peça explicitamente ("revise isto com calma e cuidado").
- Quando você pede que ela revise o seu texto, ela pode reconstruir a estrutura, se o problema estiver nela. Se quiser manter a estrutura e mudar só detalhes, deixe isso claro no pedido ("corrija só os erros de digitação"); nesse caso, a skill aponta os problemas de estrutura em vez de corrigi-los.
- A skill pergunta uma única vez se deve revisar tudo o que o agente escreve ou só os textos para outras pessoas, e faz isso na primeira vez que for usada em um lugar onde possa salvar a resposta. Para mudar o escopo depois, basta pedir. Se você mudar o escopo em um lugar onde a configuração não pode ser salva, a skill vai aplicá-la só à conversa atual e fornecer uma frase para você acrescentar às suas próprias instruções, para que as próximas sessões a levem em conta.
- **O que ela grava fora da conversa**: só quando você escolhe ou muda o escopo, a skill salva uma frase nas suas instruções pessoais ou na memória da sua conta (por exemplo, no seu `CLAUDE.md` de usuário) e informa onde. Fora do texto em que você está trabalhando, ela não grava mais nada.

## Traduções

O agente carrega apenas o [`SKILL.md`](../plugin/skills/readers-ear/SKILL.md) em inglês. As traduções são para as pessoas lerem; se alguma divergir do inglês, vale o inglês.

| Idioma | README | Instruções da skill |
|---|---|---|
| 日本語 | [README.ja.md](README.ja.md) | [SKILL.ja.md](SKILL.ja.md) |
| 简体中文 | [README.zh-Hans.md](README.zh-Hans.md) | [SKILL.zh-Hans.md](SKILL.zh-Hans.md) |
| 한국어 | [README.ko.md](README.ko.md) | [SKILL.ko.md](SKILL.ko.md) |
| Español | [README.es.md](README.es.md) | [SKILL.es.md](SKILL.es.md) |
| Français | [README.fr.md](README.fr.md) | [SKILL.fr.md](SKILL.fr.md) |
| Deutsch | [README.de.md](README.de.md) | [SKILL.de.md](SKILL.de.md) |
| Português (Brasil) | [README.pt-BR.md](README.pt-BR.md) | [SKILL.pt-BR.md](SKILL.pt-BR.md) |

## Experimente

Antes de confiar na skill, experimente-a com os seus próprios textos:

- Compare o resultado com e sem a skill no mesmo modelo, de preferência em vários idiomas e em gêneros com fórmulas fixas, como e-mails comerciais, cláusulas de contrato e textos de interface.
- Entregue a ela um texto que já esteja bom. Ele deve voltar praticamente inalterado.
- Passe a ela um texto de conteúdo correto, mas mal estruturado, como um relatório com a conclusão perdida no meio do texto, e peça uma revisão. Ela deve reconstruir a estrutura e manter todos os fatos.
- Durante o trabalho de programação, verifique se ela revisa as mensagens de commit, as descrições de PR e a documentação que o agente escreve, sem mexer nos textos que outras pessoas já escreveram.

## Como contribuir

- Ao alterar o `SKILL.md` ou o README em inglês, atualize as traduções correspondentes no mesmo commit, incluindo a data no início de cada tradução da skill.
- Teste as mudanças no `SKILL.md` em pelo menos três idiomas, um deles com poucos dados de treinamento, e com cada modelo a que você pretende dar suporte. Verifique também como a skill faz a pergunta sobre o escopo e salva a resposta em uma execução não interativa (`claude -p`) e em uma sessão na nuvem.

## Licença

Este projeto é distribuído sob a [Licença MIT](../LICENSE).
