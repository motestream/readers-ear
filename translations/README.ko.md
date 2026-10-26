# Reader's Ear

[English](../README.md) · [日本語](README.ja.md) · [简体中文](README.zh-Hans.md) · **한국어** · [Español](README.es.md) · [Français](README.fr.md) · [Deutsch](README.de.md) · [Português (Brasil)](README.pt-BR.md)

Reader's Ear(`readers-ear`)는 어떤 언어, 어떤 장르의 글이든 대상 독자가 자연스럽게 읽을 수 있을 때까지 AI 에이전트가 퇴고하게 하는 [Agent Skill](https://agentskills.io)입니다.

## 만든 이유

이른바 'humanizer' 계열 스킬은 대부분 규칙에 따라 글을 고칩니다. 여기서 규칙이란 AI가 쓴 티가 나는 단어와 표현 패턴의 목록입니다. 이 방식에는 세 가지 문제가 있습니다.

- 규칙은 대개 한 언어를 기준으로 만들어져 있어 다른 언어에서는 통하지 않는다.
- 고정된 규칙은 어떤 용도에서는 잘못된 선택을 강요한다.
- 모델이 좋아져도 결과는 규칙의 수준을 넘어서지 못한다.

이 스킬은 반대로 접근합니다. AI는 이미 어느 언어에서든 글의 좋고 나쁨을 가려낼 만큼 똑똑하며, 부족한 것은 규칙이 아니라 일하는 방식이라고 봅니다. 그래서 이 스킬에는 어느 언어에서나 통하는 원칙만 담았습니다. 독자를 기준으로 판단하고, 구성부터 살펴 구체적인 문제를 찾고, 단어 하나에서 글 전체의 구성까지 문제마다 알맞은 단위로 고치고, 구체적인 문제가 더 없으면 멈춥니다. 나머지는 모델에 맡기므로 모델이 좋아지면 그만큼 결과도 좋아집니다.

## 기능

- **표준 퇴고**: 독자가 읽듯이 글을 다시 읽되 문장보다 구성을 먼저 보고, 구체적으로 짚을 수 있는 문제만 고칩니다. 구성 자체에 문제가 있으면 문장을 다듬는 데 그치지 않고, 글이 전해야 할 내용을 목록으로 적은 다음 그것을 바탕으로 글을 다시 짜고, 빠진 사실이나 요점이 없는지 확인합니다. 남은 문제가 없으면 멈추므로 이미 잘 쓴 글은 거의 그대로 돌아옵니다. 들이는 노력은 글의 길이와 중요도에 따라 달라집니다. 사용자는 완성된 글과 함께, 고치지 않고 지적만 한 부분이 있으면 그 내용을, 구성을 바꿨다면 그 설명도 받습니다.
- **꼼꼼한 퇴고**(시간과 토큰이 훨씬 많이 들므로 요청할 때만): 에이전트가 글에 대한 자기 견해를 굳히기 전에, 사용자와 나눈 대화를 보지 않은 새 AI 인스턴스(서브에이전트 등) 두 개가 동시에 작업합니다. 하나는 퇴고할 글을 보지 않은 채 같은 장르와 목적의 글을 웹에서 찾아 읽고, 그 글들이 어떻게 쓰였는지 정리합니다. 다른 하나는 퇴고할 글과, 독자와 목적을 적은 메모만 받아 읽고 걸리는 곳을 알려 줍니다. 에이전트는 두 보고를 바탕으로 문제를 찾고, 핵심 표현과 사실을 확인한 뒤 고칩니다. 그리고 무엇을 참고했는지, 하지 못한 단계가 있었다면 그것이 무엇인지 알려 줍니다. 참고 자료로는 사전, 말뭉치, 공공 기관과 대기업의 문서처럼 같은 언어로 직접 쓰였고 개인이나 기관이 문구를 확인하고 책임지는 자료만 씁니다. 표현에 관해서는 생성형 AI가 널리 쓰이기 전의 글을 우선적으로 참고합니다. 번역문은 원래 언어의 틀이 남아 있을 수 있어 참고 자료로 삼지 않습니다.
- **적용 범위**: 요청이 없을 때 스스로 퇴고하는 것은 에이전트가 직접 쓰는 글 가운데 다른 사람이 읽을 글뿐입니다. 설정을 저장할 수 있는 환경에서는 에이전트가 쓰는 모든 글로 범위를 넓힐지 사용자에게 한 번만 묻고, 그 답을 이후 세션에서도 읽어 들이는 곳에 저장합니다.

## 설치

스킬을 쓰는 곳에 맞춰 설치 방법을 고르세요. 메뉴 이름은 영어 UI에 표시되는 그대로 적었습니다.

| 사용 환경 | 권장 방법 |
|---|---|
| 자신의 컴퓨터에서 쓰는 Claude Code | 이 저장소에서 [플러그인](#claude-code)으로 설치 |
| claude.ai, Claude Desktop, Cowork, 웹용 Claude Code | claude.ai 계정에 [ZIP 업로드](#claudeai-claude-desktop-cowork) |
| Codex, Cursor, Gemini CLI, GitHub Copilot 등 다른 에이전트 | [`npx skills`](#다른-에이전트) |

claude.ai와 Claude Code를 모두 쓴다면 ZIP 업로드 하나로 둘 다 해결됩니다. 같은 계정으로 로그인하면 Claude Code가 claude.ai 계정에 있는 스킬도 로드하기 때문입니다. 이 경우 플러그인은 설치하지 마세요. 둘 다 설치하면 Claude Code에 같은 스킬이 두 번 로드됩니다.

### Claude Code

Claude Code 세션에서 다음을 실행합니다.

```
/plugin marketplace add motestream/readers-ear
/plugin install readers-ear@readers-ear
```

첫 번째 명령은 이 저장소를 플러그인 마켓플레이스로 추가하고, 두 번째 명령은 그 마켓플레이스에서 플러그인 `readers-ear`를 설치합니다(마켓플레이스와 플러그인의 이름이 같습니다). Claude Code 2.1.275 이상에서는 `/plugin install readers-ear --marketplace motestream/readers-ear` 명령 하나로 두 단계를 한 번에 처리할 수 있습니다.

- **업데이트**: `/plugin marketplace update readers-ear`를 실행하거나, `/plugin`의 **Marketplaces**에서 이 마켓플레이스의 자동 업데이트를 켭니다.
- **팀과 공유**: 프로젝트 저장소에서 `claude plugin marketplace add motestream/readers-ear --scope project`를 실행하고, 이 명령이 기록한 `.claude/settings.json`을 커밋합니다. 이후 Claude Code가 프로젝트 폴더를 신뢰할지 물을 때 팀원이 수락하면, 그 팀원에게도 이 마켓플레이스가 등록되어 거기서 플러그인을 설치할 수 있습니다.
- **클라우드 세션**(웹용 Claude Code)에서는 자신의 컴퓨터에 설치한 플러그인이 로드되지 않습니다. 대신 스킬을 claude.ai에 업로드하거나(다음 절), `plugin/skills/readers-ear/`를 프로젝트의 `.claude/skills/`에 복사해 커밋하세요.

### claude.ai, Claude Desktop, Cowork

1. 코드 실행이 켜져 있는지 확인합니다. Free, Pro, Max 요금제에서는 **Settings > Capabilities**에 있습니다. Team과 Enterprise 요금제에서는 소유자가 **Organization settings > Plugins & skills**에서 스킬 기능과 함께 켭니다.
2. 이 저장소를 내려받아 `plugin/skills/readers-ear` 폴더를 ZIP으로 압축합니다. ZIP 안에 `readers-ear/SKILL.md`가 들어 있어야 하며, 폴더 이름은 `readers-ear` 그대로 두어야 합니다.
3. claude.ai에서 **Customize > Skills**를 열고 **+**를 누른 다음 **Create skill** > **Upload a skill**을 선택해 ZIP을 고릅니다.

이렇게 올린 스킬은 계정에 속하므로 Claude Desktop과 Cowork에서도 쓸 수 있습니다. 같은 계정으로 로그인하면 Claude Code(2.1.273 이상)도 클라우드 세션을 포함해 이 스킬을 로드합니다. 업데이트하려면 **Customize > Skills**에서 이전 버전을 삭제하고 새 ZIP을 업로드합니다. Team과 Enterprise 조직의 소유자는 모든 구성원에게 스킬을 배포할 수 있습니다.

### 다른 에이전트

```
npx skills add motestream/readers-ear -g
```

`-g`를 붙이면 사용자 계정 단위로 설치되고, 빼면 현재 프로젝트에 설치됩니다. 이 명령은 사용 중인 에이전트를 감지한 뒤 어느 에이전트에 설치할지 묻습니다. 특정 에이전트를 지정하려면 `-a codex`처럼 `-a`를 붙입니다. 업데이트는 `npx skills update`로 합니다.

GitHub CLI 2.90 이상에서는 대신 `gh skill install motestream/readers-ear readers-ear --scope user`로 설치할 수도 있습니다. `gh skill`은 미리 보기 단계의 기능입니다. 이 명령도 어느 에이전트에 설치할지 묻는데, `--agent`로 지정할 수도 있습니다. 업데이트는 `gh skill update`로 합니다.

직접 설치하려면 `plugin/skills/readers-ear/`를 에이전트의 스킬 디렉터리(Claude Code라면 `~/.claude/skills/`)에 복사합니다.

## 사용법

- 이 스킬은 다른 사람이 읽을 글을 에이전트가 쓸 때마다 자동으로 작동합니다. "이 글을 자연스럽게 다듬어 줘"처럼 직접 요청하거나 이름으로 부를 수도 있습니다. 이름은 `/readers-ear`이고, Claude Code 플러그인으로 설치했다면 `/readers-ear:readers-ear`입니다.
- 꼼꼼한 퇴고를 원하면 "시간을 들여서 꼼꼼하게 퇴고해 줘"처럼 분명히 요청하세요.
- 글을 퇴고해 달라고 하면, 문제가 구성에 있을 때 스킬이 구성부터 다시 짤 수 있습니다. 구성은 그대로 두고 세부만 고치기를 원하면 "오탈자만 고쳐 줘"처럼 요청하세요. 그러면 구성의 문제는 고치지 않고 지적만 합니다.
- 처음 실행될 때 에이전트가 쓰는 모든 글을 퇴고할지, 다른 사람이 읽을 글만 퇴고할지 한 번 묻습니다. 단, 그 답을 저장해 둘 수 있는 환경에서만 묻습니다. 나중에 범위를 바꾸고 싶으면 그렇게 말하면 됩니다. 설정을 저장할 수 없는 환경에서 범위를 바꾸면, 스킬은 그 설정을 현재 대화에만 적용하고, 이후 세션에도 반영되도록 자신의 지침에 넣을 문장을 알려 줍니다.
- **대화 밖에 기록하는 것**: 적용 범위를 고르거나 바꿀 때만, 그 내용을 한 문장으로 개인 지침 파일이나 계정 메모리(사용자 단위 `CLAUDE.md` 등)에 저장하고 저장 위치를 알려 줍니다. 그 밖에는 작업 중인 글 바깥에 아무것도 기록하지 않습니다.

## 번역

에이전트가 읽어 들이는 것은 영어판 [`SKILL.md`](../plugin/skills/readers-ear/SKILL.md)뿐입니다. 번역은 사람이 읽기 위한 것이며, 영어판과 내용이 다르면 영어판을 기준으로 합니다.

| 언어 | README | 스킬 지침 |
|---|---|---|
| 日本語 | [README.ja.md](README.ja.md) | [SKILL.ja.md](SKILL.ja.md) |
| 简体中文 | [README.zh-Hans.md](README.zh-Hans.md) | [SKILL.zh-Hans.md](SKILL.zh-Hans.md) |
| 한국어 | [README.ko.md](README.ko.md) | [SKILL.ko.md](SKILL.ko.md) |
| Español | [README.es.md](README.es.md) | [SKILL.es.md](SKILL.es.md) |
| Français | [README.fr.md](README.fr.md) | [SKILL.fr.md](SKILL.fr.md) |
| Deutsch | [README.de.md](README.de.md) | [SKILL.de.md](SKILL.de.md) |
| Português (Brasil) | [README.pt-BR.md](README.pt-BR.md) | [SKILL.pt-BR.md](SKILL.pt-BR.md) |

## 시험해 보기

이 스킬을 믿고 쓰기 전에 자신의 글로 먼저 시험해 보세요.

- 같은 모델에서 스킬을 쓸 때와 쓰지 않을 때의 출력을 비교합니다. 가능하면 언어는 여러 가지로 하고, 장르는 비즈니스 이메일, 계약 조항, UI 문구처럼 정형 표현이 있는 것으로 고릅니다.
- 이미 잘 쓴 글을 넣어 봅니다. 거의 그대로 돌아와야 합니다.
- 내용에는 문제가 없지만 구성이 어수선한 글(결론이 중간에 묻힌 보고서 등)을 넣고 퇴고를 요청해 봅니다. 사실을 하나도 빠뜨리지 않고 구성을 다시 짜야 합니다.
- 코딩 작업 중에는 에이전트가 직접 쓰는 커밋 메시지, PR 설명, 문서를 다듬는지, 다른 사람이 쓴 기존 글은 건드리지 않는지 확인합니다.

## 기여하기

- `SKILL.md`나 영어판 README를 바꿀 때는 같은 커밋에서 해당 번역도 고칩니다. 스킬 지침 번역이라면 맨 위의 날짜도 바꿉니다.
- `SKILL.md`의 변경은 세 개 이상의 언어(그중 하나는 학습 데이터가 적은 언어)로, 지원하려는 모든 모델에서 테스트합니다. 적용 범위를 묻는 질문과 답의 저장이 비대화형 실행(`claude -p`)과 클라우드 세션에서 어떻게 동작하는지도 확인합니다.

## 라이선스

Reader's Ear는 [MIT 라이선스](../LICENSE)로 배포됩니다.
