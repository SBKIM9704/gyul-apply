# Design

띵귤 채팅매니저 지원서 — 단일 정적 페이지(`index.html`, CSS/JS 인라인)의 비주얼 시스템.

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
| `--ink` / `--ink-soft` / `--muted` | `#2c2118` / `#5a4a3b` / `#856a4d` | 본문/보조/흐린 텍스트 (muted는 WCAG AA 4.5:1 확보) |
| `--orange` / `--orange-deep` / `--tangerine` | `#ff7a18` / `#e85d04` / `#ffab3d` | 메인 강조(띵귤) |
| `--leaf` / `--leaf-deep` / `--leaf-soft` | `#3fa34d` / `#2e7d39` / `#eaf6ec` | 개근/긍정 (deep=소형 텍스트 AA용) |
| `--gold` | `#f0a500` | 1위 강조(👑, 골드 막대) |

섀도: `--shadow-sm` · `--shadow` · `--shadow-lg` — 모두 감귤빛(rgba(226,120,20,...)) 계열.

## Typography

- **전체:** `SUIT Variable`(가변, 100–900) **단일 패밀리** — jsdelivr CDN(`sunn-us/SUIT@2`, `woff2-variations`, `font-display: swap`). 본문은 기본 굵기, 제목/수치는 `.display`(weight 800, letter-spacing -.02em).
- **아이디/모노:** `SF Mono, Consolas, monospace` — 카페·숲 아이디 강조.
- 페이지 유일 `h1`은 topbar 로고(`.topbar .logo`, 13px). 섹션 제목은 `h2`(22px).

## Spacing & Radius

- 컨테이너 `.wrap` max-width **880px**, 좌우 패딩 20px.
- 섹션 세로 패딩 40px, 섹션 간 점선 구분(`--line-strong`).
- 반경: 카드/주요 요소 `--radius: 18px`, 소형 요소 6~12px, pill/버튼 999px.

## Components

- **Topbar** — 제목(`h1.logo` "띵귤 채팅매니저 지원서", 페이지 유일 h1) + 날짜. **히어로 섹션은 제거** — 페이지는 topbar 다음 바로 지원 정보로 시작.
- **지원 정보** — 상단 전체폭 **아이디 복사 카드**(`.id-copy`, 카페·숲 통합 · mar5924 클릭 복사, "복사됨 ✓" 피드백, `execCommand` 폴백) + 경력·본업 2열 info 카드.
- **활동 가능 시간대** — 24시간 트랙(평일/주말) 3상태(가능/조건부 빗금/업무) + 범례.
- **시청 리캡** — ① 월별 **막대차트**(띵귤 단독, 1위 달은 골드 막대 + 👑, 우측 시간·점유율) ② **하루 평균 추이** 인라인 SVG 라인+영역 차트 ③ **개근 스트릭** 셀 ④ **접이식 증빙**(`<details>`) 원본 스크린샷 갤러리 + 라이트박스.
- **기타 부문** — 아이콘 스킬 카드 3개 + `.btn`(노래책 열기 ↗).
- **지원 요약** — 담백한 클로징 한 줄(중앙 정렬). 연락 아이디 복사는 지원 정보의 `.id-copy` 카드로 통합. / **footer**.

## Motion

- **스크롤 리빌** — IntersectionObserver로 `.reveal` fade + translateY.
- **막대 채우기** — `.bar`는 `transform: scaleX()` (GPU 가속, layout thrash 회피). 트랙 진입 시 0→목표 비율.
- **추이 라인 드로잉** — SVG `stroke-dashoffset` 애니메이션 + 점/영역 페이드.
- **hover** — 카드/버튼 lift.
- 모든 모션은 `prefers-reduced-motion`에서 정지.

## Layout & Responsive

- 데스크톱 단일 컬럼(중앙 880px).
- `≤640px`: 정보 1열, 갤러리 2열, 막대·시간대 트랙 축소.

## Assets

- `img/ttingtting.png` — 팬 캐릭터 **띵띵이** 마스코트(파비콘 + 카페 공유 OG 이미지. 히어로 제거로 페이지 본문엔 미표시).
- `img/YYYY-MM.webp` — SOOP 월별 리캡 원본 스크린샷(증빙, 접이식).

## Anti-patterns (impeccable)

- detector 클린 상태 유지: `node .claude/skills/impeccable/scripts/detect.mjs index.html`.
- 억제된 오탐: `broken-image`(라이트박스 자리표시자), `numbered-section-markers`(날짜/월 라벨). 인라인 `impeccable-disable`로 명시.
