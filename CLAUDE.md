# 띵귤 채팅매니저 지원서 (gyul-apply)

스트리머 **띵귤** 의 채팅매니저 모집에 제출할 **1페이지 지원서 웹사이트**.
"자주 시청하는 분"이라는 지원 조건을 **7개월치 SOOP 시청 리캡 데이터로 증명**하고,
동시에 웹 풀스택 개발자로서의 역량("기타 부문")을 어필하는 것이 목적.

## 지원자 정보

- 카페 아이디 / 숲(SOOP) 아이디: `mar5924`
- 활동명: 좀놀던괴물
- 채팅매니저 경력: 없음 (시청 데이터 + 개발 역량으로 대체)
- 활동 가능 시간: 평일 20시 이후 · 주말 풀타임
  - 평일 09:00~20:00은 업무 시간이라 활발한 활동 어려움 (지원서에 명시할 것)
  - 업무 전날(다음 날 출근)은 새벽 2시까지 활동 가능, 그 외 저녁·주말은 대부분 가능
- 본업: 웹 풀스택 개발자 (AI 활용 초고속 웹/크롬 익스텐션 개발)
- 운영 중인 사이트: 띵귤 노래책 → https://singgyulsingbook.vercel.app/

## 프로젝트 구조

```
gyul-apply/
├── index.html        # 단일 페이지. HTML + CSS + JS 전부 인라인, 외부 의존성 없음
└── img/              # SOOP 월별 리캡 원본 스크린샷 (증빙)
    ├── 2025-12.webp
    ├── 2026-01.webp  ~  2026-06.webp
```

- **빌드 도구 없음.** 순수 정적 파일. `index.html`을 브라우저로 바로 열면 됨.
- 외부 CDN 폰트는 `SUIT Variable`(가변) **1종**만 사용 (jsdelivr, `sunn-us/SUIT@2`). 아이디만 시스템 monospace.

## 시청 리캡 데이터 (SSOT)

차트·스트릭·통계의 원본은 `index.html` `<script>` 안의 `months` 배열.
**수치를 바꾸려면 이 배열만 고치면** 차트/개근/스탯이 전부 따라감.
`img/`의 스크린샷이 실제 증빙 원본이므로, 배열 수치는 반드시 스크린샷과 일치해야 함.

| 월 | 시청시간 | 점유율 | 순위 | 개근일 |
|------|----------|-------|------|--------|
| 25.12 | 57:06 | 28.1% | 2위 | 15일 (개근X) |
| 26.01 | 99:26 | 22.4% | **1위** | 31일 개근 |
| 26.02 | 95:02 | 22.6% | 2위 | 28일 개근 |
| 26.03 | 129:23 | 31.0% | 2위 | 31일 개근 |
| 26.04 | 109:53 | 23.1% | 2위 | 30일 개근 |
| 26.05 | 169:08 | 19.8% | **1위** | 31일 개근 |
| 26.06 | 123:50 | 19.7% | 2위 | 30일 개근 |

- 누적: **783시간 48분** / 연속 개근 **6개월**(26.01~) / 7개월 연속 TOP 2
- 점유율 = 해당 월 내 전체 SOOP 시청 중 띵귤 방송이 차지한 비율 (충성도 지표, 가장 강력함)

## 페이지 섹션 구성

> **히어로 섹션은 제거됨.** 페이지는 topbar(제목 = `h1.logo` "띵귤 채팅매니저 지원서") 다음 바로 지원 정보로 시작. 섹션 순서는 PRODUCT.md의 **믿음의 사다리**(자주 본다 → 꾸준하다 → 개발 기여 → 시간대 → 연락)를 따른다.

1. **지원 정보** — 상단 **아이디 복사 카드**(`.id-copy`: 카페·숲 통합, mar5924 클릭 복사) + 경력·본업
2. **띵귤 시청 리캡** (그래프 + 증빙 통합 섹션):
   - 월별 막대차트 — **띵귤 월별 시청시간**만 시각화 (`#chart`). 막대 = `transform: scaleX`, 1위인 달(26.01·26.05)은 👑 + 골드 막대, 우측에 시간·점유율 표기
   - `sub-head` 하위: **하루 평균 시청 추이** 인라인 SVG 라인+영역 차트 (`#trend`, 띵귤 기준)
   - `<details class="evidence">` — 리캡 원본 스크린샷 갤러리를 **접이식 증빙**으로 (기본 접힘). 원본엔 다른 채널·일별 기록이 노출되므로 필요 시에만 펼침
3. **기타 부문** — 노래책 사이트(`.btn` "열기 ↗" 버튼, raw URL 미노출) / AI 초고속 개발 / 방송 서포트 툴 제작
4. **활동 가능 시간대** — 평일/주말 24시간 트랙 시각화 (`#avail`, JS 생성). 가능/조건부/업무 3상태
5. **지원 요약** — 담백한 클로징 한 줄(중앙 정렬). 연락 아이디 복사는 지원 정보 카드로 통합 (과장/오글 문구 지양)

> 지원 대상은 띵귤 이므로 차트는 **띵귤 단독**으로 표시한다. (한때 봉준 비교 막대를 넣었으나, 메시지 집중을 위해 제거.) 다른 채널 정보는 증빙 스크린샷 원본에만 존재.

## 활동 가능 시간대 로직

`index.html` 스크립트의 `weekdayState(h)` / `weekendState(h)`:
- 평일: 00~02 조건부(cond, 업무 전날 · 새벽 2시까지), 09~20 업무(work), 20~24 가능(avail), 그 외 휴식
- 주말: 02~08 휴식, 그 외 대부분 가능(avail)

## 디자인 시스템

- **라이트 테마 (감귤/tangerine 컨셉)**. 밝고 따뜻한 톤. CSS 변수(`:root`):
  `--bg`(크림) `--bg-tint` `--surface`(흰색) `--ink`/`--ink-soft`/`--muted`(텍스트)
  `--orange`/`--orange-deep`/`--tangerine`(메인) `--leaf`(개근 초록) `--gold`(1위 강조)
- 배경: 고정 radial-gradient 감귤빛 글로우 여러 겹, 카드는 흰색 + 따뜻한 소프트 섀도(`--shadow*`)
- 폰트: 전체 `SUIT Variable`(가변) **단일 패밀리** — 제목/수치는 `.display`(weight 800), 본문은 기본 굵기, 아이디는 monospace
- 반응형: 720px 이하 스탯 2열, 640px 이하 정보 1열·갤러리 2열
- 접근성: `prefers-reduced-motion` 존중, 라이트박스 ESC 닫기, `aria-label`, `:focus-visible`
- 인터랙션: IntersectionObserver 스크롤 리빌 + 막대 채우기, 숫자 카운트업, 카드 hover lift

## 작업 가이드

- 수치 변경 → `months` 배열 + Hero/`chart-foot`의 하드코딩 요약 문구 함께 갱신
- 새 달 추가 → `img/YYYY-MM.webp` 추가 + `months` 배열 + `files`/`labels` 배열에 추가
- 스타일은 기존 CSS 변수와 컴포넌트 패턴 재사용. 톤(간결·데이터 중심·과장 없음) 유지
- 문구는 한국어, 정중하되 담백하게. "말보다 결과물" 컨셉 유지

## 배포

**GitHub Pages** 사용 (루트 서빙, `.nojekyll` 포함). 상세 절차는 `README.md` 참고.
- Settings → Pages → Deploy from a branch → `main` / `/ (root)`
- `img/`와 `index.html`은 같은 루트에 있어야 이미지가 뜸
- 빌드 스텝 없음. 정적 파일 그대로.

## 브랜치 전략

- `main` — 배포/안정 브랜치 (GitHub Pages 서빙 대상)
- `develop` — 기본(default) 개발 브랜치. 작업은 여기서 하고 안정화되면 `main`으로 머지

## Skills

git 워크플로 스킬이 `.claude/skills/`에 있습니다. (출처: SBKIM9704/claude-commands, `develop→main` 전략에 맞춤)

| Skill | 커맨드 | Purpose |
|-------|--------|---------|
| `commit` | `/commit` | 변경사항을 논리 그룹별로 커밋 (`develop`/`main`이면 feature 브랜치 확인) |
| `branch` | `/branch` | `develop` 최신화 후 feature 브랜치 생성 |
| `pr` | `/pr` | PR 생성 → mergeable 확인 → squash merge |
| `release` | `/release` | `develop` → `main` 릴리즈 (버전 bump · CHANGELOG · 태그) |

### 디자인 · impeccable

디자인 개선용 **impeccable** 스킬이 설치돼 있습니다 (출처: pbakaus/impeccable, `npx impeccable`).
`.claude/skills/impeccable/`에 스킬·레퍼런스(30여 개)·안티패턴 detector가 있고, `/impeccable <command> [target]`으로 호출합니다.

- 주요 커맨드: `/impeccable polish <파일>`(다듬기) · `audit`·`critique`(점검) · `init`(PRODUCT.md·DESIGN.md 생성) · `document`(DESIGN.md) 등
- **PostToolUse hook** (`.claude/settings.local.json`): Edit/Write/MultiEdit 후 UI 파일을 검사해 디자인 안티패턴을 시스템 리마인더로 노출 (로컬 실행, 5초 타임아웃)
- 수동 detector 실행: `node .claude/skills/impeccable/scripts/detect.mjs index.html`
- 컨텍스트 파일: 루트의 `PRODUCT.md`(전략)·`DESIGN.md`(비주얼)를 impeccable이 매 작업 전 참고. `/impeccable init`으로 생성
- 비고: node 22.12+ 권장(현재 20에서도 detector 동작 확인). 슬래시 커맨드는 설치 후 에이전트 재시작 시 로드됨
