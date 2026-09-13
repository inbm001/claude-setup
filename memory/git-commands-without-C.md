---
name: git-commands-without-c
description: "git 은 -C 없이, 커밋 메시지는 파일로 — 허용 팝업을 안 띄우는 방법"
metadata: 
  node_type: memory
  type: feedback
  originSessionId: 52f01e71-a9a7-4667-ad53-e663711a9002
  modified: 2026-09-11T16:29:42.386Z
---

작업 폴더가 이미 저장소이므로 `git -C /경로 commit` 대신 `git commit` 으로 쓴다.
커밋 메시지는 여러 줄을 명령에 넣지 말고, 스크래치패드에 파일로 쓴 뒤 `git commit -F 파일` 로 한다.
웹 페이지를 열 때는 Claude Browser 대신 ego-browser 를 쓴다 ([[use-ego-browser]]).

**Why:** 허용목록 `Bash(git commit:*)` 는 명령 앞부분이 맞아야 통과한다. `git -C …` 와 여러 줄 메시지는
매번 허용 팝업을 띄웠고, 사용자가 2026-09-12 "허용 팝업좀 자제할 수 없나?" 라고 했다.

**How to apply:** git add · commit · log · diff 모두 `git 하위명령` 으로 시작하게 쓴다.
