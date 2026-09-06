---
name: kanban-on-push
description: "푸시할 때마다 칸반을 먼저 고치고, 보고는 두 줄로"
metadata: 
  node_type: memory
  type: feedback
  originSessionId: ddff39d0-fb5c-4c1d-aee5-137285996065
  modified: 2026-09-05T05:55:37.735Z
---

Harmoniq 에서 푸시하기 전에 `docs/kanban.json` 을 그 시점 상태로 고치고
`npm run kanban` 을 돌린다. 보고는 두 줄로 한다.

    푸시했습니다. <범위>
    칸반 수정했습니다. <무엇이 어느 열로>

**Why:** 이틀 동안 안 고쳐서 `지금` 칸에 이미 끝난 카드가 남아 있었다.
푸시에 묶어 두면 잊지 않는다. 칸반 갱신은 3~4k 토큰이라 싸다.

**How to apply:**
- 끝난 카드는 `done` 으로 옮기고 `steps` 를 실제로 한 일로 다시 쓴다.
- 새로 시작한 것은 `now`, 바로 할 수 있는 것은 `next`.
- `npm run kanban` 이 `docs/칸반.html` 을 만든다. 그 파일은 직접 안 고친다.
- 커밋에 칸반 변경을 같이 넣는다.

관련 [[harmoniq-vst-project]]
