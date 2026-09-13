---
name: use-ego-browser
description: "화면·문서 확인은 ego-browser 작업 공간에서 — Harmoniq 공간 이름은 \"harmoniq 화면과 문서\""
metadata: 
  node_type: memory
  type: feedback
  originSessionId: 9a071a87-2c0c-4e0c-9108-15ae3f5a186f
  modified: 2026-09-11T17:11:59.508Z
---

브라우저로 무언가 열거나 확인할 때는 ego-browser 를 쓴다(2026-09-05 지시).
Harmoniq 작업은 `harmoniq 화면과 문서` 라는 작업 공간을 계속 재사용한다 —
매번 새로 만들지 않는다.

**Why:** 사용자가 그 공간에 탭을 띄워 놓고 직접 본다. 새 공간을 만들면 보던
탭이 남의 창에 생긴다.

**How to apply:**
- `useOrCreateTaskSpace('claude')` 로 시작한다 (2026-09-12 다시 만든 19번. 이전 13번 "harmoniq 화면과 문서" 는 닫힘).
- 상시 띄우는 탭 다섯: `#radar` · `#inbox` · `#listen` · `docs/칸반.html` ·
  `docs/문서.html`.
- localhost:9000 이 안 뜨면 개발 서버가 꺼진 것이다. 먼저 켜고 다시 부른다.
- 사용자가 제어를 가져가면 멈춘다. 되찾지 않고 "계속" 을 기다린다.
- 이 공간은 **절대 닫지 않는다.** 일이 끝나면 내가 연 탭만 `closeTab` 으로 닫는다.
  2026-09-12 `completeTaskSpace(13, { keep: false })` 로 공간째 날려 사용자가 보던 탭을 잃었다.
  닫힌 공간은 `listTaskSpaces` 에 안 나와 이름을 되찾을 수 없다.

관련 [[harmoniq-vst-project]]
