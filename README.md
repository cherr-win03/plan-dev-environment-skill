# plan-dev-environment

AI 코딩 에이전트(Claude Code 기준)가 소프트웨어 개발을 **계획 → 개발 환경 준비 → 구현·검증 → 병합·배포**까지 흔들림 없이 진행하도록 돕는 한국어 스킬입니다.

실제 웹사이트를 여러 AI 세션으로 몇 주 동안 개발·운영하면서 생긴 사고와 교훈을 규칙으로 정리했습니다. 널리 쓰이는 개발 스킬(pstack, Ponytail, Superpowers, gstack, spec-kit)과 비교해 좋은 아이디어도 반영했습니다.

## 무엇을 해 주나

- **계획 단계:** 프로젝트 구조와 실행 방법을 조사합니다. 작업 규모를 나누고(작음·중간·큼), "꼭 필요한가 → 이미 있나 → 표준 기능 → 참고 사례" 순서로 계획을 다듬습니다. 계획서 필수 칸(데이터 모양, 설계안 비교, 작업별 파일, 시험이 놓치는 실패 유형)을 채웁니다.
- **환경 준비:** 원본 작업 트리를 건드리지 않고 워크트리를 나눕니다. 잠금 파일대로 재현 설치하고, 기존 테스트·빌드로 현재 상태를 검증합니다. 워크트리마다 포트·DB·출력을 분리합니다.
- **구현·검증:** 버그는 실패 재현부터 만듭니다. "이번에 새로 돌린 결과"만 완료의 근거로 씁니다. 시험 기준을 몰래 낮추지 않습니다. 리뷰 브리프 형식을 정해 둡니다.
- **병합·배포:** 저장소 성격에 맞춘 통합 방식(PR / main 직접) 정하기, 머리 SHA 고정 병합, 쌓인 PR 병합 순서, 운영 DB 엔진으로 SQL 확인, 배포 절차, 운영 전환(설정·스키마 변경이 동의·서명에 미치는 영향), 외부 API 비용 상한을 다룹니다.
- **여러 세션 운영:** 팀장·부팀장·작업 세션의 역할, 보고 규칙, 검증 층, 위임과 기록 방법을 다룹니다.

작은 수정(한두 줄)에는 쓰지 않도록 되어 있습니다.

## 설치 (Claude Code)

1. 이 저장소를 받습니다.
2. `skills/plan-dev-environment` 폴더를 통째로 `~/.claude/skills/` 아래에 복사합니다(Windows: `%USERPROFILE%\.claude\skills\`).
3. (선택) `references/this-machine.example.md`를 `this-machine.md`로, `project.example.md`를 `project-<이름>.md`로 복사해 자기 환경에 맞게 채웁니다.
4. Claude Code를 다시 열면 계획 모드에서 개발을 시작할 때 자동으로 쓰입니다. 직접 부를 때는 `/plan-dev-environment`.

다른 에이전트(Codex 등)에서 쓸 때는 `SKILL.md`와 `references/`를 그 도구의 스킬·지침 위치에 두고, Claude Code 전용 도구 이름(`EnterWorktree` 등)은 `git worktree`로 바꿔 읽으면 됩니다.

## 구성

```
skills/plan-dev-environment/
  SKILL.md                         본문(언제 쓰는지, 1~5절 절차)
  references/plan-and-verify.md    규모별 절차, 필요성 사다리, 계획서 필수 칸, 구현·완료·리뷰·멈춤 기준
  references/release-gates.md      병합·DB 실엔진·배포·운영 전환·외부 비용·묻기 전 확인
  references/team-lead.md          여러 세션·에이전트 운영
  references/this-machine.example.md   내 PC 도구·함정 양식
  references/project.example.md        프로젝트 위치 안내 양식
```

## 참고한 것

아래 스킬은 설치하거나 문구를 복사하지 않고, 원문을 읽은 뒤 아이디어만 자기 말로 옮겼습니다(모두 MIT 라이선스).

- [obra/superpowers](https://github.com/obra/superpowers): 설계 승인 관문, 계획서 형식, 완료 전 검증, 리뷰 왕복 상한
- [DietrichGebert/ponytail](https://github.com/DietrichGebert/ponytail): 필요성 사다리, 사례 없는 지적 금지
- [garrytan/gstack](https://github.com/garrytan/gstack): 시험 관문 무결성, 시험 0건은 미검증, 배포 뒤 감시
- [github/spec-kit](https://github.com/github/spec-kit): 프로젝트 고정 원칙 점검, 명확화 질문 형식, 병렬 표시
- [cursor/plugins pstack](https://github.com/cursor/plugins/tree/main/pstack): 실행으로 증명, 질문 대신 시제품, 반복 실수의 구조화

## 라이선스

MIT. [LICENSE](LICENSE)를 보세요.
