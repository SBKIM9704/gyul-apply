# Design

띵귤_ 채팅매니저 지원서 — 단일 정적 페이지(`index.html`, CSS/JS 인라인)의 비주얼 시스템.

## Theme

밝고 따뜻한 **감귤(tangerine) 라이트 테마**. 크림빛 배경 위 흰 카드 + 감귤빛 그라데이션 글로우,
따뜻한 톤의 소프트 섀도. 데이터가 주인공이 되도록 장식은 절제한다.

배경은 `body`에 고정된 다중 radial-gradient(감귤빛 글로우 3겹) + 크림 베이스.

## Color

CSS 커스텀 프로퍼티(`:root`)로 관리. 정체성 보존을 위해 기존 hex 값을 그대로 사용한다.

| 토큰 | 값 | 용도 |
|------|-----|------|
| `--bg` | `#fff8f0` | 페이지 배경(크림) |
| `--bg-tint` | `#fff1e0` | 태그·pill 배경 |
| `--surface` | `#ffffff` | 카드 |
| `--surface-2` | `#fff6ec` | 카드 내부 트랙·셀 |
| `--line` / `--line-strong` | `#f4e2cf` / `#eccfae` | 경계선(약/강) |
| `--ink` / `--ink-soft` / `--muted` | `#2c2118` / `#5a4a3b` / `#a08a76` | 본문/보조/흐린 텍스트 |
| `--orange` / `--orange-deep` / `--tangerine` | `#ff7a18` / `#e85d04` / `#ffab3d` | 메인 강조(띵귤) |
| `--leaf` / `--leaf-soft` | `#3fa34d` / `#eaf6ec` | 개근/긍정 |
| `--gold` | `#f0a500` | 1위 강조(👑, 골드 막대) |

섀도: `--shadow-sm` · `--shadow` · `--shadow-lg` — 모두 감귤빛(rgba(226,120,20,...)) 계열.

## Typography

- **디스플레이/제목/수치:** `GmarketSans`(700, 부분 500) — `.display` 클래스. 웹폰트(woff).
- **본문:** `Pretendard Variable` (CDN) — 기본 sans 스택.
- **아이디/모노:** `SF Mono, Consolas, monospace` — 카페·숲 아이디 강조.
- 히어로 h1은 `clamp(31px, 5.6vw, 50px)`로 반응형 스케일.

## Spacing & Radius

- 컨테이너 `.wrap` max-width **880px**, 좌우 패딩 20px.
- 섹션 세로 패딩 40px, 섹션 간 점선 구분(`--line-strong`).
- 반경: 카드/주요 요소 `--radius: 18px`, 소형 요소 6~12px, pill/버튼 999px.

## Components

- **Topbar** — 텍스트 로고 + 날짜.
- **Hero** — `hero-head`(마스코트 + "지원자 · 좀놀던괴물" pill 한 줄) → h1 → 서브카피 → **스탯 카드 4개**(누적 시청/하루 평균/연속 개근/채널 순위). 카드는 좌측 그라데이션 바 + 카운트업 수치.
- **지원 정보** — 2열 info 카드(아이디/경력/본업).
- **활동 가능 시간대** — 24시간 트랙(평일/주말) 3상태(가능/조건부 빗금/업무) + 범례.
- **시청 리캡** — ① 월별 **막대차트**(띵귤_ 단독, 1위 달은 골드 막대 + 👑, 우측 시간·점유율) ② **하루 평균 추이** 인라인 SVG 라인+영역 차트 ③ **개근 스트릭** 셀 ④ **접이식 증빙**(`<details>`) 원본 스크린샷 갤러리 + 라이트박스.
- **기타 부문** — 아이콘 스킬 카드 3개 + `.btn`(노래책 열기 ↗).
- **지원 요약 / footer**.

## Motion

- **스크롤 리빌** — IntersectionObserver로 `.reveal` fade + translateY.
- **막대 채우기** — `.bar`는 `transform: scaleX()` (GPU 가속, layout thrash 회피). 트랙 진입 시 0→목표 비율.
- **추이 라인 드로잉** — SVG `stroke-dashoffset` 애니메이션 + 점/영역 페이드.
- **카운트업** — 히어로 수치 easing 카운트.
- **마스코트** — `bob` 키프레임(위아래 + 살짝 회전).
- **hover** — 카드/버튼 lift.
- 모든 모션은 `prefers-reduced-motion`에서 정지.

## Layout & Responsive

- 데스크톱 단일 컬럼(중앙 880px). 스탯 4열.
- `≤720px`: 스탯 2열.
- `≤640px`: 정보 1열, 갤러리 2열, 그룹 막대·시간대 트랙 축소, 마스코트 56px, 요약 세로 정렬.

## Assets

- `img/ttingtting.png` — 팬 캐릭터 **띵띵이** 마스코트(히어로 + 파비콘).
- `img/YYYY-MM.webp` — SOOP 월별 리캡 원본 스크린샷(증빙, 접이식).

## Anti-patterns (impeccable)

- detector 클린 상태 유지: `node .claude/skills/impeccable/scripts/detect.mjs index.html`.
- 억제된 오탐: `broken-image`(라이트박스 자리표시자), `numbered-section-markers`(날짜/월 라벨). 인라인 `impeccable-disable`로 명시.
