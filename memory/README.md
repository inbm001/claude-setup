# memory

Claude 가 세션 사이에 들고 다니는 것. 프로젝트마다 따로 쌓인다.

## 놓을 곳

    ~/.claude/projects/<프로젝트 경로를 -로 바꾼 이름>/memory/

예를 들어 `/Users/inbm_mini/harmoniq-claude` 는 이렇게 된다.

    ~/.claude/projects/-Users-inbm-mini-harmoniq-claude/memory/

`MEMORY.md` 가 목차다. 세션이 시작될 때 이 파일만 읽히고, 필요할 때 나머지를
찾아 읽는다.

## 여기 있는 것

| 파일 | 무엇 |
|---|---|
| `korean-terms-not-invented.md` | 한국어 전문 용어를 조립해서 만들지 않는다 |
| `plain-korean-in-replies.md` | 답변도 일반인 말투로 |
| `use-ego-browser.md` | 브라우저는 ego-browser, 작업 공간을 재사용 |
| `kanban-on-push.md` | 푸시할 때 칸반도 고친다 |
| `harmoniq-vst-project.md` | Harmoniq 가 무엇인지 |
| `harmoniq-design-canvas.md` | 화면 캔버스 링크 |

## 주의

경로에 프로젝트 이름이 들어간다. 다른 맥에서 사용자명이 다르면 폴더 이름도
달라진다. 위 규칙대로 만들어 넣는다.
