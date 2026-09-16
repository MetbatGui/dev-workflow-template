# Dev Workflow Template

> Vertical Slice + XP(TDD) + ADR 기반 개발 워크플로우. Codex/Claude 등 여러 AI 코딩 에이전트가 같은 규칙을 공유하도록 설계됨.

[concenews](https://github.com/MetbatGui/concenews) 프로젝트에서 실제로 여러 Slice를 거치며 다듬어진 프로세스를 추출했다. 언어·스택 무관하게 재사용 가능한 부분만 담았다.

## 담긴 것

| 파일 | 역할 |
|---|---|
| `AGENTS.md` | 에이전트 지침 SSOT. Codex/Claude 공통. TDD·ADR 강제 규칙, 라우팅 표 |
| `CLAUDE.md` | Claude 전용 포인터 (내용 없음, SSOT 이중화 방지) |
| `docs/workflow.md` | 간단 기획 → Spike → ADR → Spec → Plan → Tasks → 구현 전체 흐름 |
| `docs/git-workflow.md` | 브랜치 네이밍, 커밋 컨벤션, PR 크기 원칙, Self-review 계약, 독립 리뷰(Independent Review), merge 정책 |
| `docs/adr-process.md` | ADR 형식·트리거·불변성(immutable)·소급 적용 규칙 |
| `docs/review-standard.md` | PR 리뷰 형식, severity 정의, 처리 주체 규칙 |
| `docs/product-vision.md` | 제품 비전 문서 뼈대 (내용은 프로젝트마다 채움) |
| `docs/decisions/README.md` | ADR 인덱스 뼈대 |
| `docs/architecture/principles/xp.md` | TDD·Simple Design·Self-Review·Sustainable Pace |
| `docs/architecture/principles/ddd.md` | 4계층 아키텍처, 도메인 경계 규칙 |
| `docs/architecture/principles/vertical-slices.md` | Vertical Slice 판단 기준, Spike→Spec 정밀도 규칙 |
| `.github/PULL_REQUEST_TEMPLATE.md` | 근거 요구형 PR 템플릿 (체크만 하고 넘어가는 것 방지) |

## 담기지 않은 것 (의도적으로 제외)

- 특정 스택(Python/pytest/SQLAlchemy 등)에 종속된 구체 설정 — `Justfile`, `pyproject.toml` 같은 건 프로젝트마다 새로 만들어야 한다. 다만 **"게이트 하나로 합성"** 패턴(`just check-branch-green` 이 lint·type·import-boundary·unit·integration 을 순서대로 묶는 것)은 스택 무관하게 재사용할 가치가 있다 — `docs/git-workflow.md`·`workflow.md` 에 그 개념만 남겨뒀다.
- 도메인 콘텐츠(product-vision 내용, Spec/Plan, ADR 본문) — 이건 각 프로젝트가 스스로 채워야 한다.

## 새 프로젝트에 적용하는 법

1. 이 리포를 새 프로젝트 루트에 복사한다(`git clone` 후 `.git` 삭제, 또는 파일만 복사).
2. `docs/product-vision.md` 를 그 프로젝트 내용으로 채운다.
3. `AGENTS.md` 의 "언제 무엇을 볼까" 라우팅 표에 그 프로젝트의 실제 문서 경로를 채운다(현재는 스켈레톤만 있음).
4. 스택에 맞는 로컬 품질 게이트(Justfile 등)를 구성하고 `docs/git-workflow.md`·`AGENTS.md` 에서 참조하는 명령어를 실제 명령으로 바꾼다.
5. 첫 Slice 부터 `docs/workflow.md` 순서(간단 기획 → Spike(필요시) → ADR(트리거 매칭시) → Spec → Plan → 사용자 검토 → 구현)를 따른다.

## 이 템플릿 자체의 원칙

이 템플릿도 여기 담긴 규칙을 따라 관리한다 — 규칙을 바꿀 땐 근거를 ADR 로 남기고, 문서 갱신은 `docs/adr-process.md` 순서를 지킨다.

Co-Authored-By 관례는 각 프로젝트가 정한다(이 템플릿 자체에는 강제하지 않음).
