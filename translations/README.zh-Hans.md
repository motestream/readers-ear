# Reader's Ear

[English](../README.md) · [日本語](README.ja.md) · **简体中文** · [한국어](README.ko.md) · [Español](README.es.md) · [Français](README.fr.md) · [Deutsch](README.de.md) · [Português (Brasil)](README.pt-BR.md)

Reader's Ear 是一个 [Agent Skill](https://agentskills.io)（智能体技能），可以让 AI 智能体撰写和修改任何语言、任何体裁的文字，使目标读者读来自然。它不提供禁用词清单，而是给智能体一套工作方法。你可以在 Claude（Claude Code、claude.ai、Claude Desktop 和 Cowork）中安装它，也可以在 Codex、Cursor、Gemini CLI、GitHub Copilot 等其他智能体中安装。

## 为什么提供方法而不是规则

许多“去 AI 味”（humanizer）技能依靠规则工作，也就是一份份听起来有 AI 味的词语和句式清单。规则有以下缺点：

- 规则通常只针对一种语言编写，换成其他语言就不适用。
- 规则会一刀切地强制某些选择，在有些场合就会出错，例如连合同或商务邮件必需的措辞也一并禁用。
- 规则会给效果设上限：无论模型进步多少，输出都不会好过规则本身。

Reader's Ear 的前提是：模型已经能分辨任何语言的文字是好是坏，它缺的不是规则，而是工作方法。因此，本技能只提供一套适用于所有语言的方法，判断则交给模型。这意味着模型越好，效果就越好。

## 功能

完整说明见 [`SKILL.md`](../plugin/skills/readers-ear/SKILL.md)（简体中文译文见 [`SKILL.zh-Hans.md`](SKILL.zh-Hans.md)）。要点如下：

- **撰写**：智能体撰写新文字时，会先弄清谁会读、读者已经知道什么、读它是为了什么，然后从初稿起就为这位读者而写。写完后，它会以这位读者的身份把初稿读一遍，修正发现的问题。
- **修改**：它以读者的身份阅读文字，只改有具体问题的地方，问题出在哪里就改哪里，小到一个词，大到整篇文字的结构。它会保留你原文中的事实、主要观点和文风；本来就写得好的文字，它会几乎原样返回。事实错误和超出你要求范围的问题，它只指出，不修改。
- **容易忽略的问题**：无论是撰写还是修改，它都会特别留意其他语言的痕迹（例如照搬过来的语序或日期格式），以及文字是否依赖读者没有看到过的背景（例如智能体和你之间的对话，或它在工作中给事物起的名称）。
- **仔细模式**：一种更慢、更彻底、会引入外部意见的工作方式。它会耗费多得多的时间和词元（token），因此只在你要求时使用。在智能体自己评判文字之前，会有两个全新的 AI 实例（例如子代理）协助：一个在看不到你的文字的情况下，收集同一体裁的参考文字；另一个在没有任何背景的情况下初读这篇文字。随后，智能体对照原本就用该文字的语言写成的资料（不用译文）核实关键措辞和事实，再修改文字。最后，它会告诉你参考了什么，以及跳过了哪些步骤。
- **适用范围**：默认情况下，即使你不提出要求，它也会处理智能体写给他人的文字和给你的汇报。汇报指智能体处理完你的请求后给出的最终回答，以及它为你制作、供你阅读的文档。你可以把范围扩大到智能体撰写的所有文字，也可以只限于写给他人的文字（见“用法”）。

## 安全性

Reader's Ear 只包含说明文字，不含脚本、hooks 或 MCP 服务器。除了正在处理的文字，它唯一会写入的内容，是记录你所选适用范围的一句话。当你选择或更改适用范围，或者没有回答智能体关于范围的提问时，它会把这句话保存到你个人的指令文件（例如用户级的 `CLAUDE.md`）或账户记忆中，并告诉你保存在哪里。

在仔细模式下，智能体还会启动全新的 AI 实例（例如子代理），并搜索和阅读参考文字及网页等其他资料。搜索时只用术语、名称和短语，不用你的文字中的段落。

## 安装

如果你同时使用 claude.ai 和 Claude Code，请先了解以下情况：在云端会话中，Claude Code 会加载你 claude.ai 账户中的技能；在 2.1.273 或更高版本中，如果你在终端会话中用 `/login` 以该账户登录，Claude Code 也会加载。如果你属于上述任一情况，只需按下文所述把 ZIP 上传到 claude.ai 账户；如果再安装插件，Claude Code 会把本技能加载两次。

否则，请根据使用智能体的环境选择安装方法：

| 使用环境 | 推荐方法 |
| --- | --- |
| 本机上的 Claude Code | [Claude Code 插件](#claude-code-插件) |
| claude.ai、Claude Desktop、Cowork 或网页版 Claude Code | [把 ZIP 上传到你的 claude.ai 账户](#claudeaiclaude-desktop-和-cowork) |
| Codex、Cursor、Gemini CLI、GitHub Copilot 等其他智能体 | [`npx skills`](#其他智能体) |

### Claude Code 插件

在 Claude Code 会话中运行以下命令：

```
/plugin marketplace add motestream/readers-ear
/plugin install readers-ear@readers-ear
```

第一条命令把本仓库添加为插件市场，第二条命令从中安装插件 `readers-ear`。插件市场和插件同名。

在 Claude Code 2.1.275 或更高版本中，一条命令即可完成这两步：

```
/plugin install readers-ear --marketplace motestream/readers-ear
```

**如需更新**，请运行 `/plugin marketplace update readers-ear`，或在 `/plugin` 的 **Marketplaces** 选项卡中为这个插件市场开启自动更新。

**如需与团队共享**，请在项目仓库的根目录打开终端，运行以下命令：

```sh
claude plugin marketplace add motestream/readers-ear --scope project
```

然后提交该命令写入的 `.claude/settings.json`。团队成员在 Claude Code 提示是否信任该项目文件夹时选择信任，Claude Code 就会为他们添加这个插件市场，他们可以从中安装插件。

**云端会话**（网页版 Claude Code）不会加载你在本机上安装的插件。在云端会话中，请改为把技能上传到 claude.ai；或者从本仓库的克隆或下载的 ZIP 中，把 `plugin/skills/readers-ear/` 文件夹复制到项目的 `.claude/skills/` 中并提交。

### claude.ai、Claude Desktop 和 Cowork

1. 技能依赖代码执行，请先确认已开启。使用 Free、Pro 或 Max 套餐时，该选项位于 **Settings > Capabilities**。使用 Team 套餐时，代码执行和技能功能默认为整个组织开启。使用 Enterprise 套餐时，由所有者在 **Organization settings > Plugins & skills** 的 **Policy** 选项卡中确认两者均已开启。
2. 把本仓库下载为 ZIP 文件（在 GitHub 上点击 **Code** > **Download ZIP**）并解压。
3. 把 `plugin/skills/readers-ear` 文件夹压缩成一个新的 ZIP 文件，使 ZIP 中包含一个 `readers-ear` 文件夹，文件夹内有 `SKILL.md`。文件夹名必须保持为 `readers-ear`。
4. 在 claude.ai 上打开 **Customize > Skills**，点击 **+**，再依次点击 **Create skill** > **Upload a skill**，然后选择这个 ZIP 文件。

这样，技能就归属于你的账户，因此 Claude Desktop 和 Cowork 也会使用它；满足[安装](#安装)开头所述的条件时，Claude Code 也会使用。Enterprise 组织的所有者还可以上传本技能，为所有成员统一配置。

**如需更新**，请在 **Customize > Skills** 中删除旧版本，再上传新的 ZIP 文件。

### 其他智能体

此方法需要 Node.js。运行以下命令：

```sh
npx skills add motestream/readers-ear -g
```

加上 `-g` 会全局安装本技能，对你的所有项目生效；不加则只安装到当前项目。该命令会检测本机已安装的智能体，并询问要为哪些智能体安装。如需事先指定，请加上 `-a`，例如 `-a codex`。

**如需更新**，请运行 `npx skills update`。

**使用 GitHub CLI 2.90 或更高版本时**，也可以改用 `gh skill`（目前处于预览阶段）：

```sh
gh skill install motestream/readers-ear readers-ear --scope user
```

该命令会询问要为哪个智能体安装，你也可以用 `--agent` 直接指定。如需更新，请运行 `gh skill update`。

**如需手动安装**，请从本仓库的克隆或下载的 ZIP 中，把 `plugin/skills/readers-ear/` 文件夹复制到智能体的技能目录，例如 Claude Code 的 `~/.claude/skills/`。

## 用法

智能体撰写给他人的文字或向你汇报时，Reader's Ear 会自动启用。你也可以用自己的话提出要求，例如“把这段改得自然一点”，或者用 `/readers-ear` 按名称调用（如果是作为 Claude Code 插件安装的，则为 `/readers-ear:readers-ear`）。

**仔细模式**：只有在你明确要求时（例如“慢慢来，把这段仔细改一改”或“慢慢来，把这篇仔细写好”），智能体才会使用这种模式。如果希望每次都使用，请在保存的指令（例如 `CLAUDE.md`）中写明。

**限制改动范围**：告诉智能体只改什么，例如“只改错别字”。这时，其他问题它只会指出，不会修改。

**适用范围**：默认范围包括写给他人的文字和智能体给你的汇报。汇报指智能体在处理你的请求时做过实际工作（例如读取文件或运行命令）之后给出的最终回答，以及它为你制作、供你阅读的文档。智能体在得出最终回答的过程中写下的内容，以及仅凭对话内容就能给出的简短回复，不在此列。在可以保存设置的交互式会话中，智能体首次在默认范围内交付文字后，会问你一次：是保留默认范围，还是对它撰写的所有文字使用本技能，还是只对写给他人的文字使用。如果你没有回答，它会保留默认范围并保存下来，以后不会再问。之后想更改范围，直接告诉智能体即可。在无法保存设置的环境中，智能体不会询问；如果你在这种环境中要求更改范围，更改只对当前对话有效。智能体会给你一句可加进自己指令的话，加进去之后，以后的会话就能沿用。

## 试用

在正式依赖本技能之前，可以先做以下检查：

- 在同一模型上比较使用和不使用本技能的输出，最好涵盖多种语言，以及商务邮件、合同条款、界面文案等有固定用语的体裁。
- 请智能体根据你的笔记写一段给他人看的文字。交付的文字应当无需再改一轮，就能让读者读得顺畅。
- 给它一段本来就写得好的文字，请它修改。返回的文字应当几乎没有改动。
- 给它一段事实无误、但顺序让人难以理解的文字，请它修改。它应当重新组织这段文字，并保留每一项事实。
- 在编程工作中，确认它会改进智能体撰写的提交信息、PR 描述和文档，而不会改动他人写的现有文字。
- 在需要多个步骤的任务完成后，确认智能体的最终回答用的是你懂的词，而不是它在工作中自己起的名称，并且篇幅没有超出你的需要。

## 译文

智能体只加载英文版 [`SKILL.md`](../plugin/skills/readers-ear/SKILL.md)。译文供人阅读。如果译文与英文版不一致，以英文版为准。

| 语言 | README | 技能说明 |
| --- | --- | --- |
| 日本語 | [README.ja.md](README.ja.md) | [SKILL.ja.md](SKILL.ja.md) |
| 简体中文 | [README.zh-Hans.md](README.zh-Hans.md) | [SKILL.zh-Hans.md](SKILL.zh-Hans.md) |
| 한국어 | [README.ko.md](README.ko.md) | [SKILL.ko.md](SKILL.ko.md) |
| Español | [README.es.md](README.es.md) | [SKILL.es.md](SKILL.es.md) |
| Français | [README.fr.md](README.fr.md) | [SKILL.fr.md](SKILL.fr.md) |
| Deutsch | [README.de.md](README.de.md) | [SKILL.de.md](SKILL.de.md) |
| Português (Brasil) | [README.pt-BR.md](README.pt-BR.md) | [SKILL.pt-BR.md](SKILL.pt-BR.md) |

## 参与贡献

- 修改 `SKILL.md` 或英文版 README 时，请在同一次提交中更新相应的译文，包括每份技能说明译文开头的日期。
- 修改 `SKILL.md` 后，至少要用三种语言测试，其中一种应是训练数据较少的语言，并且要在本项目支持的每个模型上测试。此外，还要检查在非交互式运行（`claude -p`）和云端会话中，询问适用范围和保存回答这两个环节表现如何。

## 许可证

Reader's Ear 采用 [MIT 许可证](../LICENSE)发布。
