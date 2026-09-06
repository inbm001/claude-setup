# claude-setup

다른 맥에서 같은 답변 스타일과 허용 정책을 재현하기 위한 설정 모음.

## 파일

| 파일 | 놓을 곳 |
|---|---|
| `CLAUDE.md` | `~/.claude/CLAUDE.md` |
| `settings.permissions.json` | 내용의 `permissions` 키를 `~/.claude/settings.json` 에 병합 |
| `modes.md` | 읽기용 — ponytail 켜고 끄기, caveman 을 뺀 이유 |
| `prompts.md` | 읽기용 — 설정 적용 프롬프트, 새 프로젝트 시작 프롬프트 |
| `memory/` | Claude 가 세션 사이에 들고 다니는 것. 놓을 곳은 `memory/README.md` |

`settings.permissions.json` 안의 경로 `/Users/inbm_mini` 는 그 맥의 사용자명으로 바꿀 것.

## 플러그인

```bash
claude plugin marketplace add DietrichGebert/ponytail
```

```bash
claude plugin install ponytail
```

| 플러그인 | 역할 |
|---|---|
| ponytail | 최소 구현 우선. 안 만드는 쪽을 먼저 검토 |

caveman 은 쓰지 않는다. 이유는 `modes.md` 에 있다. 이미 깔았으면 지운다.

```bash
claude plugin uninstall caveman
```

## 적용 순서

1. `CLAUDE.md` 복사
2. `permissions` 병합
3. `memory/` 복사 — 놓을 곳은 `memory/README.md`
4. 플러그인 설치
5. Claude 완전 종료 후 재실행 — 설정은 세션 시작 시 한 번만 읽힘

## 다른 맥에서 이어서 하려면

설정 말고도 받아야 할 것이 있다.

```bash
git clone https://github.com/inbm001/harmoniq-claude
```

```bash
git clone https://github.com/inbm001/progressions
```

`progressions` 는 `harmoniq-claude` 와 **나란히** 두어야 한다. `npm run inbox:pick` 이
`../progressions` 를 본다.

## 주의

- 설정은 세션이 시작될 때 읽힌다. 실행 중인 대화에는 반영되지 않는다.
- `deny` 목록은 지우지 말 것. `sudo`, 강제 푸시, 자격증명 파일 읽기를 막는다.
- `defaultMode: acceptEdits` 는 파일 편집을 자동 승인한다. 신뢰하는 폴더에서만 쓸 것.
