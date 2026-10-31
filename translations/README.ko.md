# Reader's Ear

[English](../README.md) · [日本語](README.ja.md) · [简体中文](README.zh-Hans.md) · **한국어** · [Español](README.es.md) · [Français](README.fr.md) · [Deutsch](README.de.md) · [Português (Brasil)](README.pt-BR.md)

Reader's Ear는 AI 에이전트가 어떤 언어, 어떤 장르의 글이든 대상 독자가 자연스럽게 읽을 수 있게 쓰고 고치도록 하는 [Agent Skill](https://agentskills.io)입니다. 피해야 할 단어의 목록 대신, 일하는 방식을 에이전트에게 알려 줍니다. Claude(Claude Code, claude.ai, Claude Desktop, Cowork)는 물론 Codex, Cursor, Gemini CLI, GitHub Copilot 같은 다른 에이전트에도 설치할 수 있습니다.

## 규칙 대신 방법을 택한 이유

이른바 'humanizer' 스킬 가운데 상당수는 규칙을 바탕으로 작동합니다. 여기서 규칙이란 AI가 쓴 티가 나는 단어와 패턴의 목록입니다. 규칙에는 다음과 같은 단점이 있습니다.

- 대개 한 언어를 기준으로 만들어져서 다른 언어에는 들어맞지 않습니다.
- 용도에 따라서는 잘못된 선택을 강요합니다. 계약서나 업무 이메일에 꼭 필요한 표현을 금지하는 경우가 그렇습니다.
- 결과의 상한을 정해 버립니다. 모델이 아무리 좋아져도 출력은 규칙의 수준을 넘지 못합니다.

Reader's Ear는 모델이 이미 어느 언어에서든 좋은 글과 나쁜 글을 가려낼 수 있으며, 부족한 것은 규칙이 아니라 일하는 방식이라고 봅니다. 그래서 이 스킬은 모든 언어에서 통하는 방법만 제공하고 판단은 모델에 맡깁니다. 덕분에 모델이 좋아질수록 결과도 좋아집니다.

## 기능

전체 지침은 [`SKILL.md`](../plugin/skills/readers-ear/SKILL.md)에 있습니다(한국어 번역: [`SKILL.ko.md`](SKILL.ko.md)). 요약하면 다음과 같습니다.

- **새 글 작성**: 에이전트는 새 글을 쓸 때 먼저 누가 읽을지, 그 독자가 이미 무엇을 아는지, 무엇을 하려고 읽는지 파악하고, 첫 초안부터 그 독자를 위해 씁니다. 그런 다음 그 독자가 되어 초안을 한 번 읽고, 찾아낸 문제를 고칩니다.
- **퇴고**: 독자가 읽듯이 글을 읽고, 단어 하나에서 글 전체의 구성까지 어디에 있든 구체적인 문제만 고칩니다. 원래 글의 사실, 요점, 문체는 지키며, 잘 쓴 글은 거의 그대로 돌려줍니다. 사실 오류와 요청한 범위를 넘는 문제는 고치지 않고 지적합니다.
- **놓치기 쉬운 문제**: 쓸 때도 고칠 때도 두 가지를 특히 살핍니다. 하나는 다른 언어의 흔적으로, 그대로 옮겨 온 어순이나 날짜 표기 같은 것입니다. 다른 하나는 에이전트가 사용자와 나눈 대화나 작업하면서 붙인 이름처럼, 독자가 보지 않은 맥락에 기대는 곳입니다.
- **꼼꼼 모드**: 외부의 시각을 끌어들여 더 느리지만 더 철저하게 작업하는 방식입니다. 시간과 토큰이 훨씬 많이 들기 때문에 요청할 때만 씁니다. 에이전트가 직접 글을 판단하기 전에 새 AI 인스턴스(예: 서브에이전트) 두 개가 돕습니다. 하나는 사용자의 글을 보지 않은 채 같은 장르의 참고 글을 모으고, 다른 하나는 사전 정보 없이 글을 읽습니다. 그다음 에이전트는 핵심 표현과 사실을 원래 그 언어로 쓰인 자료(번역문 제외)와 대조해 확인하고 글을 고칩니다. 무엇을 참고했는지, 건너뛴 단계가 있으면 무엇인지도 알려 줍니다.
- **적용 범위**: 기본적으로는 요청이 없어도, 에이전트가 다른 사람을 위해 쓰는 글과 사용자에게 하는 보고에 작동합니다. 여기서 보고란 작업을 거쳐 내놓은 최종 답변과, 사용자가 읽도록 만든 문서를 말합니다. 에이전트가 쓰는 모든 글로 넓히거나, 다른 사람을 위한 글로만 좁힐 수도 있습니다('사용법' 참고).

## 안전성

Reader's Ear는 지침만으로 이루어져 있으며, 스크립트, 훅, MCP 서버는 들어 있지 않습니다. 작업 중인 글 외에 이 스킬이 기록하는 것은 어떤 적용 범위를 골랐는지 적은 문장 하나뿐입니다. 사용자가 적용 범위를 고르거나 바꿀 때, 또는 에이전트가 범위를 물었는데 사용자가 답하지 않았을 때, 에이전트는 이 문장을 개인 지침 파일(예: 사용자 단위 `CLAUDE.md`)이나 계정 메모리에 저장하고 저장한 위치를 알려 줍니다.

꼼꼼 모드에서는 이 밖에도 에이전트가 서브에이전트 같은 새 AI 인스턴스를 띄우고, 웹 페이지 같은 참고 글과 그 밖의 자료를 검색해 읽습니다. 검색어로는 사용자의 글에서 떼어 낸 대목이 아니라 용어, 이름, 짧은 구절만 씁니다.

## 설치

claude.ai와 Claude Code를 모두 쓴다면 먼저 확인할 것이 있습니다. Claude Code는 클라우드 세션에서, 그리고 `/login`으로 claude.ai 계정에 로그인한 터미널 세션(버전 2.1.273 이상)에서 그 계정에 있는 스킬을 불러옵니다. Claude Code를 이렇게 쓰고 있다면 ZIP 업로드만으로 충분합니다. 플러그인까지 설치하면 Claude Code가 같은 스킬을 두 번 불러옵니다.

그렇지 않다면 에이전트를 쓰는 곳에 맞는 방법을 고르세요.

| 사용하는 곳 | 권장 방법 |
| --- | --- |
| 내 컴퓨터에서 쓰는 Claude Code | [Claude Code 플러그인](#claude-code-플러그인) |
| claude.ai, Claude Desktop, Cowork, 웹용 Claude Code | [claude.ai 계정에 ZIP 업로드](#claudeai-claude-desktop-cowork) |
| Codex, Cursor, Gemini CLI, GitHub Copilot 등 다른 에이전트 | [`npx skills`](#다른-에이전트) |

### Claude Code 플러그인

Claude Code 세션에서 다음을 실행합니다.

```
/plugin marketplace add motestream/readers-ear
/plugin install readers-ear@readers-ear
```

첫 번째 명령은 이 저장소를 플러그인 마켓플레이스로 추가합니다. 두 번째 명령은 그 마켓플레이스에서 `readers-ear` 플러그인을 설치합니다. 마켓플레이스와 플러그인의 이름은 같습니다.

Claude Code 2.1.275 이상에서는 명령 하나로 두 단계를 한 번에 처리할 수 있습니다.

```
/plugin install readers-ear --marketplace motestream/readers-ear
```

**업데이트하려면** `/plugin marketplace update readers-ear`를 실행하거나, `/plugin`의 **Marketplaces**에서 이 마켓플레이스의 자동 업데이트를 켭니다.

**팀과 공유하려면** 프로젝트 저장소의 루트에서 터미널을 열고 다음을 실행합니다.

```sh
claude plugin marketplace add motestream/readers-ear --scope project
```

그런 다음 이 명령이 기록한 `.claude/settings.json`을 커밋합니다. Claude Code가 프로젝트 폴더를 신뢰할지 물을 때 수락한 팀원에게는 이 마켓플레이스가 추가되고, 팀원은 거기서 플러그인을 설치할 수 있습니다.

**클라우드 세션**(웹용 Claude Code)은 내 컴퓨터에 설치한 플러그인을 불러오지 않습니다. 클라우드 세션에서는 대신 스킬을 claude.ai에 업로드하거나, 이 저장소를 클론하거나 ZIP으로 내려받은 다음 `plugin/skills/readers-ear/` 폴더를 프로젝트의 `.claude/skills/`에 복사해 커밋합니다.

### claude.ai, Claude Desktop, Cowork

1. 코드 실행이 켜져 있는지 확인합니다. 스킬을 쓰려면 코드 실행이 필요합니다. Free, Pro, Max 요금제에서는 **Settings > Capabilities**에 있습니다. Team 요금제에서는 조직 전체에 코드 실행과 스킬 기능이 기본으로 켜져 있습니다. Enterprise 요금제에서는 소유자가 **Organization settings > Plugins & skills**의 **Policy** 탭에서 둘 다 켜져 있는지 확인합니다.
2. 이 저장소를 ZIP으로 내려받아(GitHub에서 **Code** > **Download ZIP**) 압축을 풉니다.
3. `plugin/skills/readers-ear` 폴더를 새 ZIP으로 압축합니다. ZIP 안에 `readers-ear` 폴더가 있고, 그 안에 `SKILL.md`가 들어 있어야 합니다. 폴더 이름은 `readers-ear` 그대로 두어야 합니다.
4. claude.ai에서 **Customize > Skills**를 열고 **+**를 누른 다음, **Create skill** > **Upload a skill**을 선택하고 ZIP 파일을 고릅니다.

이렇게 올린 스킬은 계정에 속하므로 Claude Desktop과 Cowork에서도 쓸 수 있고, [설치](#설치) 첫머리에서 설명한 조건을 갖추면 Claude Code에서도 쓸 수 있습니다. Enterprise 조직의 소유자는 스킬을 업로드해 모든 구성원에게 배포할 수도 있습니다.

**업데이트하려면** **Customize > Skills**에서 이전 버전을 삭제하고 새 ZIP을 업로드합니다.

### 다른 에이전트

이 방법을 쓰려면 Node.js가 필요합니다. 다음을 실행합니다.

```sh
npx skills add motestream/readers-ear -g
```

`-g`를 붙이면 모든 프로젝트에서 쓸 수 있도록 전역으로 설치되고, 빼면 현재 프로젝트에만 설치됩니다. 이 명령은 내 컴퓨터에 설치된 에이전트를 감지하고 어느 에이전트에 설치할지 묻습니다. 미리 정해 두려면 `-a codex`처럼 `-a`를 붙입니다.

**업데이트하려면** `npx skills update`를 실행합니다.

**GitHub CLI 2.90 이상에서는** 프리뷰 단계인 `gh skill`을 대신 쓸 수도 있습니다.

```sh
gh skill install motestream/readers-ear readers-ear --scope user
```

이 명령은 어느 에이전트에 설치할지 묻습니다. `--agent`로 직접 지정할 수도 있습니다. 업데이트하려면 `gh skill update`를 실행합니다.

**직접 설치하려면** 이 저장소를 클론하거나 ZIP으로 내려받은 다음, `plugin/skills/readers-ear/` 폴더를 에이전트의 스킬 디렉터리(Claude Code라면 `~/.claude/skills/`)에 복사합니다.

## 사용법

Reader's Ear는 에이전트가 다른 사람을 위한 글을 쓰거나 사용자에게 보고할 때 저절로 작동합니다. "이 글 자연스럽게 다듬어 줘"처럼 평소 쓰는 말로 요청하거나, `/readers-ear`로 이름을 불러 실행할 수도 있습니다(Claude Code 플러그인으로 설치했다면 `/readers-ear:readers-ear`).

**꼼꼼 모드**: 에이전트는 사용자가 분명히 요청할 때만 꼼꼼 모드를 씁니다. "시간 들여서 꼼꼼하게 퇴고해 줘"나 "시간 들여서 꼼꼼하게 써 줘"처럼 요청하면 됩니다. 매번 쓰게 하려면 `CLAUDE.md` 같은 저장된 지침에 그렇게 적어 둡니다.

**수정 범위 제한**: "오타만 고쳐 줘"처럼 무엇만 고칠지 에이전트에게 알려 줍니다. 그러면 다른 문제는 고치지 않고 지적합니다.

**적용 범위**: 기본값은 다른 사람을 위한 글과, 에이전트가 사용자에게 하는 보고입니다. 보고란 파일을 읽거나 명령을 실행하는 등 작업을 거쳐 내놓은 최종 답변과, 사용자가 읽도록 만든 문서를 말합니다. 최종 답변에 이르기까지 작업하면서 쓰는 글이나, 대화 내용만으로 할 수 있는 짧은 대답은 들어가지 않습니다. 설정을 저장할 수 있는 대화형 세션에서는 에이전트가 기본값의 범위에 드는 글을 처음 전달한 뒤, 기본값을 유지할지, 에이전트가 쓰는 모든 글에 적용할지, 다른 사람을 위한 글로만 좁힐지 한 번 묻습니다. 사용자가 답하지 않으면 기본값을 유지하고 그 선택을 저장하므로 다시 묻지 않습니다. 나중에 범위를 바꾸려면 에이전트에게 말하면 됩니다. 설정을 저장할 수 없는 곳에서는 묻지 않습니다. 그런 곳에서 범위를 바꿔 달라고 하면 그 변경은 현재 대화에만 적용되고, 에이전트는 이후 세션에도 반영되도록 사용자가 자기 지침에 넣을 문장을 알려 줍니다.

## 테스트 방법

이 스킬을 믿고 쓰기 전에 다음을 확인해 보세요.

- 같은 모델에서 스킬을 쓸 때와 쓰지 않을 때의 출력을 비교합니다. 가능하면 여러 언어로, 그리고 업무 이메일, 계약 조항, UI 문구처럼 정형 표현이 있는 장르로 비교합니다.
- 메모를 주고 다른 사람이 읽을 글을 써 달라고 합니다. 받은 글은 다시 손보지 않아도 그 독자에게 잘 읽혀야 합니다.
- 이미 잘 쓴 글을 주고 퇴고를 요청합니다. 거의 그대로 돌아와야 합니다.
- 사실에는 문제가 없지만 순서를 따라가기 어려운 글을 주고 퇴고를 요청합니다. 사실은 하나도 빠뜨리지 않고 구성을 다시 짜야 합니다.
- 코딩 작업 중에는 에이전트가 쓰는 커밋 메시지, PR 설명, 문서가 나아지는지, 다른 사람이 쓴 기존 글은 건드리지 않는지 확인합니다.
- 여러 단계를 거치는 작업이 끝난 뒤에는, 에이전트의 최종 답변이 작업하면서 지어낸 이름이 아니라 사용자가 아는 말을 쓰는지, 필요 이상으로 길지 않은지 확인합니다.

## 번역

에이전트가 읽어 들이는 것은 영어판 [`SKILL.md`](../plugin/skills/readers-ear/SKILL.md)뿐입니다. 번역은 사람이 읽기 위한 것입니다. 번역과 영어판의 내용이 다르면 영어판을 기준으로 합니다.

| 언어 | README | 스킬 지침 |
| --- | --- | --- |
| 日本語 | [README.ja.md](README.ja.md) | [SKILL.ja.md](SKILL.ja.md) |
| 简体中文 | [README.zh-Hans.md](README.zh-Hans.md) | [SKILL.zh-Hans.md](SKILL.zh-Hans.md) |
| 한국어 | [README.ko.md](README.ko.md) | [SKILL.ko.md](SKILL.ko.md) |
| Español | [README.es.md](README.es.md) | [SKILL.es.md](SKILL.es.md) |
| Français | [README.fr.md](README.fr.md) | [SKILL.fr.md](SKILL.fr.md) |
| Deutsch | [README.de.md](README.de.md) | [SKILL.de.md](SKILL.de.md) |
| Português (Brasil) | [README.pt-BR.md](README.pt-BR.md) | [SKILL.pt-BR.md](SKILL.pt-BR.md) |

## 기여 방법

- `SKILL.md`나 영어판 README가 바뀌면 같은 커밋에서 바뀐 파일의 번역도 고칩니다. 스킬 지침 번역은 맨 위의 날짜도 바꿉니다.
- `SKILL.md`를 바꿨다면 세 개 이상의 언어(그중 하나는 학습 데이터가 적은 언어)로, 프로젝트가 지원하는 모든 모델에서 테스트합니다. 적용 범위를 묻는 질문과 그 답의 저장이 비대화형 실행(`claude -p`)과 클라우드 세션에서 어떻게 동작하는지도 확인합니다.

## 라이선스

Reader's Ear는 [MIT 라이선스](../LICENSE)로 배포됩니다.
