# Reader's Ear

[English](../README.md) · [日本語](README.ja.md) · **简体中文** · [한국어](README.ko.md) · [Español](README.es.md) · [Français](README.fr.md) · [Deutsch](README.de.md) · [Português (Brasil)](README.pt-BR.md)

Reader's Ear（`readers-ear`）是一个[Agent Skill](https://agentskills.io)（智能体技能），让 AI 智能体反复修改任何语言、任何体裁的文字，直到目标读者读来自然为止。

## 为什么做这个技能

大多数“去 AI 味”（humanizer）类技能靠规则来改文字：一份份带有 AI 味的词语和句式清单。这样做有三个代价：

- 规则通常只针对一种语言编写，换了语言就不管用。
- 固定的规则会强制做出在某些场合并不恰当的取舍。
- 模型越来越强，规则反而成了上限。

本技能反其道而行之。它的前提是：AI 已经足够聪明，能分辨任何语言的文字好坏；它缺的不是规则，而是修改的方法。因此，本技能只保留在任何语言中都成立的原则：以读者为准来评判文字，从结构入手，通过重读找出具体问题，按问题的大小来改（小到一个词，大到整体结构），不再有具体问题时就停下。其余的都交给模型，所以模型越好，效果就越好。

## 功能

- **标准修改**：像目标读者那样重读文字，先看结构，再看句子，修改能具体指出的问题。如果问题出在结构上，它不会只去打磨句子，而是列出文字要传达的内容，据此重组，并检查有没有遗漏事实或要点。指不出问题就停下，所以本来就写得好的文字会几乎原样返回。投入多少精力，视文字的长度和重要程度而定。你会拿到改好的文字，以及它只指出而未修改的地方（如有）；如果调整了结构，还会附上简短说明。
- **仔细修改**（会多花不少时间和 token，因此仅在你要求时进行）：在智能体对文字形成自己的看法之前，先让两个没看过当前对话的全新 AI 实例（例如子智能体）同时工作。一个不看你的文字，上网查找体裁和用途相同的文字，总结其写法；另一个只读你的文字和一段写明读者与用途的备注，报告读起来卡住的地方。随后，智能体参考这两份报告找出问题，核对关键措辞和事实，再进行修改。最后，它会告诉你参考了什么，以及有哪些步骤没能做到。参照的资料包括词典、语料库，以及公共机构和大型企业的网页等，须以与你的文字相同的语言原创，措辞经个人或机构审核并由其负责；在措辞方面，优先参照生成式 AI 普及之前的文字。译文可能带有源语言的痕迹，因此绝不用作参照。
- **适用范围**：未经要求，它只修改智能体写给他人看的文字。在能保存设置的环境中，它会问你一次是否把范围扩大到智能体写的所有文字，并把你的回答保存在以后的会话都会加载的地方。

## 安装

请根据使用本技能的场景选择安装方法。

| 使用环境 | 推荐方法 |
|---|---|
| 自己电脑上的 Claude Code | 从本仓库安装[插件](#claude-code) |
| claude.ai、Claude Desktop、Cowork 或网页版 Claude Code | 把 [ZIP 上传](#claudeaiclaude-desktop-和-cowork)到你的 claude.ai 账户 |
| Codex、Cursor、Gemini CLI、GitHub Copilot 等其他智能体 | [`npx skills`](#其他智能体) |

如果你同时使用 claude.ai 和 Claude Code，只需上传 ZIP，两边就都能用上：用同一账户登录时，Claude Code 会加载你 claude.ai 账户中的技能。不要再安装插件，否则 Claude Code 会加载两份。

### Claude Code

在 Claude Code 会话中运行：

```
/plugin marketplace add motestream/readers-ear
/plugin install readers-ear@readers-ear
```

第一条命令把本仓库添加为插件市场；第二条命令从这个插件市场安装插件 `readers-ear`（插件市场与插件同名）。在 Claude Code 2.1.275 或更高版本中，一条命令即可完成这两步：`/plugin install readers-ear --marketplace motestream/readers-ear`。

- **更新**：运行 `/plugin marketplace update readers-ear`，或在 `/plugin` 的 **Marketplaces** 中为这个插件市场开启自动更新。
- **与团队共享**：在你项目的仓库中运行 `claude plugin marketplace add motestream/readers-ear --scope project`，并提交该命令写入的 `.claude/settings.json`。团队成员只要在 Claude Code 询问是否信任该项目文件夹时选择信任，即可使用这个插件市场，并从中安装插件。
- **云端会话**（网页版 Claude Code）不会加载你在自己电脑上安装的插件。请改为把技能上传到 claude.ai（见下一节），或把 `plugin/skills/readers-ear/` 复制到你项目的 `.claude/skills/` 中并提交。

### claude.ai、Claude Desktop 和 Cowork

1. 确认已开启代码执行。Free、Pro 和 Max 套餐的用户可以在 **Settings > Capabilities**（界面名称按英文版写出，下同）中开启；Team 和 Enterprise 套餐则由组织所有者在 **Organization settings > Plugins & skills** 中将它与 Skills 一并开启。
2. 下载本仓库，把 `plugin/skills/readers-ear` 文件夹压缩成 ZIP 文件，使 ZIP 中包含 `readers-ear/SKILL.md`。文件夹名必须保持为 `readers-ear`。
3. 在 claude.ai 上打开 **Customize > Skills**，点击 **+**，再依次点击 **Create skill** > **Upload a skill**，然后选择这个 ZIP 文件。

上传后，技能就归属于你的账户，因此 Claude Desktop 和 Cowork 也会使用它。用同一账户登录时，Claude Code（2.1.273 或更高版本）也会加载它，云端会话也不例外。如需更新，先在 **Customize > Skills** 中删除旧版本，再上传新的 ZIP 文件。Team 和 Enterprise 组织的所有者可以为全体成员统一配置该技能。

### 其他智能体

```
npx skills add motestream/readers-ear -g
```

加上 `-g` 会为你的用户账户安装，不加则安装到当前项目。该命令会检测你已有的智能体，并询问要为其中哪些智能体安装；如需指定，可加上 `-a`，例如 `-a codex`。用 `npx skills update` 更新。

使用 GitHub CLI 2.90 或更高版本（`gh skill` 尚处于预览阶段）时，也可以改为运行 `gh skill install motestream/readers-ear readers-ear --scope user`。该命令会询问要为哪个智能体安装，你也可以用 `--agent` 直接指定。用 `gh skill update` 更新。

如需手动安装，把 `plugin/skills/readers-ear/` 复制到智能体的技能目录，例如 Claude Code 的 `~/.claude/skills/`。

## 用法

- 智能体撰写给他人看的文字时，本技能会自动启用。你也可以直接提出要求（“把这段改得自然些”），或按名称调用：`/readers-ear`；作为 Claude Code 插件安装时则为 `/readers-ear:readers-ear`。
- 需要仔细修改时，请明确提出（“慢慢来，仔细修改这段”）。
- 请它修改你的文字时，如果问题出在结构上，它可能会调整结构。如果你想保留结构、只改细节，请在要求中说明（例如“只改错别字”）。这时，结构上的问题它只会指出，不会修改。
- 首次在可以保存设置的环境中运行时，它会问你一次：是修改智能体撰写的所有文字，还是只修改给他人看的文字。之后想更改范围，直接说即可。如果你在无法保存设置的环境中更改范围，本技能只会在当前对话中应用这一更改，并给你一句话，供你加到自己的指令中，让以后的会话也能沿用。
- **在对话之外写入的内容**：只有在你选择或更改适用范围时，本技能才会把这一设置写成一句话，保存到你个人的指令文件或账户记忆中（例如用户级的 `CLAUDE.md`），并告诉你保存位置。除此之外，它只改动你正在处理的文字，不会写入别的地方。

## 翻译

智能体只加载英文的 [`SKILL.md`](../plugin/skills/readers-ear/SKILL.md)。译文供人阅读；如与英文版不一致，以英文版为准。

| 语言 | README | 技能说明 |
|---|---|---|
| 日本語 | [README.ja.md](README.ja.md) | [SKILL.ja.md](SKILL.ja.md) |
| 简体中文 | [README.zh-Hans.md](README.zh-Hans.md) | [SKILL.zh-Hans.md](SKILL.zh-Hans.md) |
| 한국어 | [README.ko.md](README.ko.md) | [SKILL.ko.md](SKILL.ko.md) |
| Español | [README.es.md](README.es.md) | [SKILL.es.md](SKILL.es.md) |
| Français | [README.fr.md](README.fr.md) | [SKILL.fr.md](SKILL.fr.md) |
| Deutsch | [README.de.md](README.de.md) | [SKILL.de.md](SKILL.de.md) |
| Português (Brasil) | [README.pt-BR.md](README.pt-BR.md) | [SKILL.pt-BR.md](SKILL.pt-BR.md) |

## 试用

在依赖本技能之前，先用你自己的材料试一试：

- 在同一模型上比较使用和不使用本技能的输出，最好涵盖多种语言，以及商务邮件、合同条款、界面文案等有固定用语的体裁。
- 给它一段本来就写得很好的文字，它应当几乎原样返回。
- 给它一段内容没有问题、但结构有问题的文字（例如结论埋在中间的报告），请它修改。它应当调整结构，同时保留所有事实。
- 在编程工作中，确认它会润色智能体撰写的提交信息、PR 描述和文档，而不会改动他人写的现有文字。

## 参与贡献

- 修改 `SKILL.md` 或英文版 README 时，请在同一次提交中更新相应的译文，包括每份技能译文开头的日期。
- 对 `SKILL.md` 的修改，至少要用三种语言测试（其中一种是训练数据较少的语言），并在你打算支持的每个模型上测试。此外，还要检查在非交互式运行（`claude -p`）和云端会话中，询问适用范围和保存设置这两个环节表现如何。

## 许可证

本项目采用 [MIT 许可证](../LICENSE)发布。
