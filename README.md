# Reader's Ear

**English** · [日本語](translations/README.ja.md) · [简体中文](translations/README.zh-Hans.md) · [한국어](translations/README.ko.md) · [Español](translations/README.es.md) · [Français](translations/README.fr.md) · [Deutsch](translations/README.de.md) · [Português (Brasil)](translations/README.pt-BR.md)

Reader's Ear is an [Agent Skill](https://agentskills.io) that makes an AI agent write and revise prose, in any language and genre, so that the text reads naturally to its intended reader. Instead of lists of words to avoid, it gives the agent a way of working. You can install it in Claude (Claude Code, claude.ai, Claude Desktop, and Cowork) and in other agents such as Codex, Cursor, Gemini CLI, and GitHub Copilot.

## Why a method, not rules

Many "humanizer" skills work from rules: lists of words and patterns that sound like AI. Rules have drawbacks:

- They're usually written for one language and don't carry over to others.
- They force choices that are wrong for some purposes, such as banning a phrase that a contract or a business email needs.
- They cap the results: however much models improve, the output can be no better than the rules.

Reader's Ear assumes that the model can already tell good writing from bad in any language, and that what it lacks is a way of working, not rules. So the skill gives only a method that works in every language and leaves the judgment to the model, which means a better model gives better results.

## What it does

The full instructions are in [`SKILL.md`](plugin/skills/readers-ear/SKILL.md). In short:

- **Writing.** When the agent writes new text, it first works out who will read it, what they already know, and what they're reading it for, then writes for them from the first draft. It reads the draft once as that reader and fixes what it finds.
- **Revising.** It reads the text as its reader would and fixes only concrete problems, wherever they are, from a single word to the organization of the whole text. It keeps your facts, main points, and voice, and returns good text almost unchanged. It points out factual errors and problems beyond what you asked for instead of fixing them.
- **Easy-to-miss problems.** In both writing and revising, it looks in particular for traces of other languages, such as carried-over word order or date formats, and for reliance on context the reader hasn't seen, such as the agent's conversation with you or names it gave things while working.
- **Careful mode.** A slower, more thorough way of working that brings in outside views, used only on request because it costs far more time and tokens. Before the agent judges the text itself, two fresh AI instances (for example, subagents) help: one gathers reference texts of the same genre without seeing yours, and the other reads the text cold. The agent then checks key wording and facts against sources originally written in the text's language (not translations) and revises the text. It tells you what it consulted and any step it skipped.
- **Scope.** By default, it works unprompted on text the agent writes for other people and on its reports to you: the final answer to a request it worked on, and documents it makes for you to read. You can extend it to everything the agent writes, or limit it to text for other people (see Usage).

## Trust

Reader's Ear consists of instructions only, with no scripts, hooks, or MCP servers. Apart from the text being worked on, the only thing it writes is one sentence that records your scope choice. When you choose or change the scope, or leave the agent's question about it unanswered, it saves that sentence to your personal instruction file (for example, a user-level `CLAUDE.md`) or your account memory, and tells you where.

In careful mode, the agent also starts fresh AI instances, such as subagents, and searches for and reads reference texts and other sources, such as web pages. Its searches use terms, names, and short phrases, not passages of your text.

## Install

If you use both claude.ai and Claude Code, check this first: Claude Code loads the skills on your claude.ai account in cloud sessions and, on version 2.1.273 or later, in terminal sessions where you signed in with that account using `/login`. If that's how you use Claude Code, the ZIP upload alone is enough, and installing the plugin as well would make Claude Code load the skill twice.

Otherwise, choose the method for where you use the agent:

| Where you use it | Recommended method |
| --- | --- |
| Claude Code on your own machine | [Claude Code plugin](#claude-code-plugin) |
| claude.ai, Claude Desktop, Cowork, or Claude Code on the web | [ZIP upload to your claude.ai account](#claudeai-claude-desktop-and-cowork) |
| Codex, Cursor, Gemini CLI, GitHub Copilot, and other agents | [`npx skills`](#other-agents) |

### Claude Code plugin

In a Claude Code session, run:

```
/plugin marketplace add motestream/readers-ear
/plugin install readers-ear@readers-ear
```

The first command adds this repository as a plugin marketplace. The second installs the plugin `readers-ear` from it; the marketplace and the plugin share the name.

On Claude Code 2.1.275 or later, one command does both:

```
/plugin install readers-ear --marketplace motestream/readers-ear
```

**To update**, run `/plugin marketplace update readers-ear`, or turn on auto-update for this marketplace under **Marketplaces** in `/plugin`.

**To share it with a team**, open a terminal at the root of the project's repository and run:

```sh
claude plugin marketplace add motestream/readers-ear --scope project
```

Then commit the `.claude/settings.json` it writes. Teammates who accept Claude Code's prompt to trust the project folder get the marketplace and can install the plugin from it.

**Cloud sessions** (Claude Code on the web) don't load plugins installed on your own machine. For those, upload the skill to claude.ai instead, or copy the `plugin/skills/readers-ear/` folder from a clone or ZIP download of this repository into the project's `.claude/skills/` and commit it.

### claude.ai, Claude Desktop, and Cowork

1. Make sure code execution is on, because skills need it. On Free, Pro, and Max plans, it's under **Settings > Capabilities**. On Team plans, code execution and Skills are on by default for the organization. On Enterprise plans, an owner makes sure both are on under **Organization settings > Plugins & skills**, on the **Policy** tab.
2. Download this repository as a ZIP (on GitHub, **Code** > **Download ZIP**) and unzip it.
3. Compress the `plugin/skills/readers-ear` folder into a new ZIP, so that the ZIP contains a `readers-ear` folder with `SKILL.md` inside. The folder name must stay `readers-ear`.
4. On claude.ai, open **Customize > Skills**, select **+**, then **Create skill** > **Upload a skill**, and choose the ZIP.

The skill then belongs to your account, so Claude Desktop and Cowork use it too, and so does Claude Code under the conditions described at the start of [Install](#install). Owners of Enterprise organizations can also upload the skill to provision it for every member.

**To update**, delete the old version in **Customize > Skills** and upload the new ZIP.

### Other agents

This method requires Node.js. Run:

```sh
npx skills add motestream/readers-ear -g
```

`-g` installs the skill globally, for all your projects; without it, the skill goes into the current project only. The command detects the agents installed on your machine and asks which to install for. To choose one in advance, add `-a`, as in `-a codex`.

**To update**, run `npx skills update`.

**With GitHub CLI 2.90 or later**, you can use `gh skill` instead, which is in preview:

```sh
gh skill install motestream/readers-ear readers-ear --scope user
```

It asks which agent to install for, or you can name one with `--agent`. To update, run `gh skill update`.

**To install by hand**, copy the `plugin/skills/readers-ear/` folder from a clone or ZIP download of this repository into the agent's skills directory, such as `~/.claude/skills/` for Claude Code.

## Usage

Reader's Ear starts on its own when the agent writes text for other people or reports to you. You can also ask for it in your own words, for example "Make this sound natural," or invoke it by name with `/readers-ear` (`/readers-ear:readers-ear` if you installed it as a Claude Code plugin).

**Careful mode.** The agent uses it only when you ask for it explicitly, for example: "Take your time and revise this carefully" or "Take your time and write this carefully." To have it used every time, say so in your saved instructions, such as a `CLAUDE.md`.

**Limiting changes.** Tell the agent what to limit itself to, for example: "Just fix the typos." It then points out other problems instead of fixing them.

**Scope.** The default covers text for other people and the agent's reports to you: its final answer to a request it did work for, such as reading files or running commands, and the documents it makes for you to read. It doesn't cover what the agent writes while working toward the final answer, or short replies it can give from the conversation alone. In an interactive session where settings can be saved, the agent asks once, after it first delivers text in the default scope, whether to keep the default, apply the skill to everything it writes, or limit it to text for other people. If you don't answer, it keeps the default and saves that, so it won't ask again. To change the scope later, ask the agent. Where settings can't be saved, the agent doesn't ask; if you ask it to change the scope there, the change applies only to the current conversation, and the agent gives you a sentence to add to your own instructions so that later sessions pick it up.

## Trying it out

Before you rely on it, try these checks:

- Compare output with and without the skill on the same model, ideally in several languages and in genres with set phrases, such as business email, contract clauses, and UI text.
- Ask the agent to write something for other people from your notes. What it delivers should read well for its reader without another round.
- Give it text that's already good and ask for a revision. It should come back almost unchanged.
- Give it text whose facts are sound but whose order is hard to follow, and ask for a revision. It should reorganize the text and keep every fact.
- During coding work, check that it improves the commit messages, PR descriptions, and docs the agent writes, and that it leaves existing text by other people alone.
- After a task that takes several steps, check that the agent's final answer uses words you know rather than names it made up while working, and that it's no longer than you need.

## Translations

The agent loads only the English [`SKILL.md`](plugin/skills/readers-ear/SKILL.md). The translations are for people to read. If a translation differs from the English, the English is authoritative.

| Language | README | Skill instructions |
| --- | --- | --- |
| 日本語 | [README.ja.md](translations/README.ja.md) | [SKILL.ja.md](translations/SKILL.ja.md) |
| 简体中文 | [README.zh-Hans.md](translations/README.zh-Hans.md) | [SKILL.zh-Hans.md](translations/SKILL.zh-Hans.md) |
| 한국어 | [README.ko.md](translations/README.ko.md) | [SKILL.ko.md](translations/SKILL.ko.md) |
| Español | [README.es.md](translations/README.es.md) | [SKILL.es.md](translations/SKILL.es.md) |
| Français | [README.fr.md](translations/README.fr.md) | [SKILL.fr.md](translations/SKILL.fr.md) |
| Deutsch | [README.de.md](translations/README.de.md) | [SKILL.de.md](translations/SKILL.de.md) |
| Português (Brasil) | [README.pt-BR.md](translations/README.pt-BR.md) | [SKILL.pt-BR.md](translations/SKILL.pt-BR.md) |

## Contributing

- When `SKILL.md` or this README changes, update the matching translations in the same commit, including the date at the top of each skill translation.
- Test changes to `SKILL.md` in at least three languages, one of them a language with little training data, and with each model the project supports. Also check how the scope question and the saving of the answer behave in a non-interactive run (`claude -p`) and in a cloud session.

## License

Reader's Ear is released under the [MIT License](LICENSE).
