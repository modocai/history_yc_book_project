# AGENTS.md

## Purpose

이 리포는 AI 기반 book publishing workflow의 작업 기록, 번역본, 제출용 문서를 관리한다.  
모든 기여자는 아래 원칙을 기본값으로 따른다.

## Non-Negotiables

- 사실 기반으로만 작성한다. 로그/대화/결과를 추측으로 보강하지 않는다.
- 긴 대화/로그를 재구성할 때는 시간 흐름과 맥락을 깨지 않는다.
- 제출 문서의 공개 참조 링크는 기본적으로 이 리포(`modocai/history_yc_book_project`) 기준으로 작성한다.
- private 저장소 링크를 넣을 때는 반드시 `(private)` 표기를 붙인다.
- 보안 정보(토큰, 비밀키, 개인 인증정보)는 커밋하지 않는다.
- 파일명은 짧고 명확하게 유지하며, 가능하면 공백을 쓰지 않는다.
- **모든 작업은 반드시 `git commit` 후 `git push`까지 완료한다.**

## Working Rules

- 작업 시작 전 현재 상태를 확인한다: `git status`, 필요한 경우 `git pull`.
- 변경은 목적 단위로 작게 나눈다(문서 편집, 링크 수정, 번역 반영 등).
- 결과 문서를 수정할 때는 아래 순서를 우선한다.
  - 왜 시작했는지(문제 정의)
  - 핵심 아이디어(해결 방식)
  - 실행 로그/증거(타임라인)
  - 원본 파일/링크(참조)
- “잘했다/보여주기” 같은 자기평가 문구보다, 검증 가능한 사실과 결과를 우선한다.

## Quality Checklist (Before Commit)

- 링크가 실제로 열리는지 확인한다(공개 링크는 HTTP 200 기준).
- 문서 내 섹션 순서가 자연스럽고 번호가 연속인지 확인한다.
- 중복 문단/중복 로그를 제거했는지 확인한다.
- 원문 보존이 필요한 블록(코드, 명령어, 경로, URL)은 변형하지 않았는지 확인한다.

## Git Rules

- 커밋 메시지는 변경 의도를 한 줄로 명확히 작성한다.
  - 예: `docs: reorder submission sections and add style transcript link`
  - 예: `docs: move repository links to footer and mark private repo`
- 푸시 후 최신 커밋 해시를 공유하고, 핵심 변경 파일 경로를 함께 기록한다.

