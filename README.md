<div align="center">

# 🍊 띵귤 채팅매니저 지원서

**스트리머 [띵귤](https://www.sooplive.co.kr/) 채팅매니저 모집 지원용 1페이지 웹사이트**

"자주 시청하는 분"이라는 지원 조건을 7개월치 SOOP 시청 리캡 데이터로 증명하고,
개발로도 방송에 조용히 보탬이 될 수 있음을 담백하게 덧붙였습니다.

<br>

[![Live Demo](https://img.shields.io/badge/Live_Demo-GitHub_Pages-ff7a18?style=for-the-badge&logo=github)](https://sbkim9704.github.io/gyul-apply/)

![HTML5](https://img.shields.io/badge/HTML5-E34F26?logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?logo=javascript&logoColor=black)
![No Build](https://img.shields.io/badge/build-none-lightgrey)
![Dependencies](https://img.shields.io/badge/dependencies-0-brightgreen)
![Deploy](https://img.shields.io/badge/GitHub_Pages-deployed-success?logo=github)

</div>

---

## 📖 목차

- [소개](#-소개)
- [주요 특징](#-주요-특징)
- [기술 스택](#-기술-스택)
- [시작하기](#-시작하기)
- [배포 (GitHub Pages)](#-배포-github-pages)
- [프로젝트 구조](#-프로젝트-구조)
- [데이터 수정 (SSOT)](#-데이터-수정-ssot)
- [디자인 도구 · impeccable](#-디자인-도구--impeccable)
- [브랜치 전략](#-브랜치-전략)
- [감사의 말](#-감사의-말)

---

## 🙋 소개

빌드 도구 없이 `index.html` 파일 **하나**로 동작하는 정적 사이트입니다.
외부 스크립트·프레임워크 없이 순수 HTML/CSS/JS만으로 만들어, 브라우저로 파일을 바로 열면 그대로 동작합니다.

| 항목 | 내용 |
|------|------|
| **활동명** | 좀놀던괴물 |
| **카페 · 숲(SOOP) 아이디** | `mar5924` |
| **누적 시청** | 783시간 48분 (2025.12 ~ 2026.06) |
| **연속 개근** | 6개월 (2026.01~) · 7개월 연속 시청 TOP 2 |
| **노래책 사이트** | https://singgyulsingbook.vercel.app/ |

---

## ✨ 주요 특징

- 📊 **데이터로 증명** — 7개월치 SOOP 월별 리캡을 막대차트·하루 평균 추이 라인차트로 시각화
- 🖼️ **접이식 증빙** — 리캡 원본 스크린샷 갤러리 + ESC로 닫히는 라이트박스 (기본 접힘)
- 🗓️ **활동 가능 시간대** — 평일/주말 24시간 트랙을 3상태(가능·조건부·업무)로 시각화
- 📋 **원클릭 아이디 복사** — 카페·숲 아이디를 클릭 한 번으로 클립보드에 복사
- 🍊 **감귤 라이트 테마** — 따뜻한 tangerine 톤 디자인 시스템, `SUIT Variable` 단일 폰트
- ♿ **접근성** — `prefers-reduced-motion` 존중, `aria-label`, `:focus-visible`, 포커스 트랩
- 🪶 **의존성 0** — 빌드 스텝·프레임워크·번들러 없음. 정적 파일 그대로 서빙

---

## 🧱 기술 스택

- **HTML / CSS / JavaScript** — 모두 `index.html`에 인라인. 프레임워크·번들러 없음
- **[SUIT Variable](https://github.com/sunn-us/SUIT)** — 유일한 외부 CDN 폰트 (jsdelivr)
- **GitHub Pages** — 정적 호스팅
- 인터랙션: `IntersectionObserver` 스크롤 리빌 · CSS `transform` 막대 애니메이션 · 인라인 SVG 차트

---

## 🚀 시작하기

저장소를 받은 뒤 `index.html`을 브라우저로 바로 열면 됩니다.
단, 이미지(`img/`)가 정상 로딩되도록 간단한 로컬 서버 사용을 권장합니다.

```bash
git clone https://github.com/SBKIM9704/gyul-apply.git
cd gyul-apply

# 로컬 서버 실행 (Python 3)
python3 -m http.server 8000
# 브라우저에서 http://localhost:8000 접속
```

> Node가 있다면 `npx serve` 로도 동일하게 띄울 수 있습니다.

---

## 🌐 배포 (GitHub Pages)

정적 파일뿐이라 GitHub Pages 무료 호스팅으로 바로 올릴 수 있습니다.

### 1) 저장소에 올리기

```bash
git add .
git commit -m "띵귤 채팅매니저 지원서"
git branch -M main
git remote add origin https://github.com/<본인아이디>/gyul-apply.git
git push -u origin main
```

### 2) Pages 켜기

1. GitHub 저장소 → **Settings** → 왼쪽 메뉴 **Pages**
2. **Source**: `Deploy from a branch`
3. **Branch**: `main` / 폴더 `/ (root)` 선택 후 **Save**
4. 1~2분 뒤 아래 주소로 공개됩니다:
   `https://<본인아이디>.github.io/gyul-apply/`

> 💡 저장소 이름을 `<본인아이디>.github.io`로 만들면 주소가 `https://<본인아이디>.github.io/` 로 더 짧아집니다.

- `.nojekyll` 파일이 포함돼 있어 Jekyll 처리 없이 파일이 그대로 서빙됩니다.
- `img/` 폴더와 `index.html`은 같은 위치(루트)에 있어야 이미지가 정상 표시됩니다.

---

## 📁 프로젝트 구조

```
gyul-apply/
├── index.html          # 페이지 전체 (HTML/CSS/JS 인라인, 외부 의존성 없음)
├── img/                # 리캡 원본 스크린샷(증빙) + ttingtting.png(마스코트)
│   ├── 2025-12.webp
│   ├── 2026-01.webp  ~  2026-06.webp
│   └── ttingtting.png
├── .nojekyll           # GitHub Pages: Jekyll 처리 스킵
├── PRODUCT.md          # (impeccable) 제품·브랜드 전략 컨텍스트
├── DESIGN.md           # (impeccable) 비주얼 시스템 컨텍스트
├── README.md
├── CLAUDE.md           # 프로젝트 컨텍스트 / 작업 가이드
└── .claude/skills/     # git 워크플로 스킬 + impeccable(디자인)
```

---

## 📊 데이터 수정 (SSOT)

시청 수치의 **단일 원본(Single Source of Truth)** 은 `index.html` `<script>` 안의 `months` 배열입니다.
이 배열만 고치면 **막대차트 · 하루 평균 추이 · 개근 스트릭 · 통계**가 모두 함께 갱신됩니다.

```js
const months = [
  { m: '25.12', h: 57,  min: 6,  pct: 28.1, rank: 2, days: 15, full: false },
  { m: '26.01', h: 99,  min: 26, pct: 22.4, rank: 1, days: 31, full: true  },
  // ...
];
```

| 필드 | 의미 |
|------|------|
| `h` / `min` | 해당 월 띵귤 시청 시간 |
| `pct` | 내 전체 SOOP 시청 중 띵귤 방송 비중 (%) |
| `rank` | 해당 월 내 시청 순위 (1이면 👑 + 골드 막대) |
| `days` / `full` | 접속일 수 / 개근 여부 |

> ⚠️ `img/`의 스크린샷이 실제 증빙 원본이므로, 배열 수치는 반드시 스크린샷과 일치해야 합니다.
> 새 달을 추가할 땐 `img/YYYY-MM.webp` + `months` + `files`/`labels` 배열을 함께 갱신하고,
> `chart-foot`의 하드코딩 요약 문구(누적·점유율·1위 달)도 같이 수정하세요.

---

## 🎨 디자인 도구 · impeccable

디자인 개선을 위해 [impeccable](https://impeccable.style) 스킬을 설치했습니다 (`.claude/skills/impeccable/`).

```bash
# 안티패턴 detector 직접 실행
node .claude/skills/impeccable/scripts/detect.mjs index.html
```

- 에이전트에서 `/impeccable polish index.html`, `/impeccable audit` 등으로 디자인을 다듬을 수 있습니다.
- `/impeccable init`이 루트에 `PRODUCT.md`(전략)·`DESIGN.md`(비주얼)를 만들고, 이후 커맨드가 이를 참고합니다.
- Edit/Write 시 UI 안티패턴을 자동 점검하는 hook이 `.claude/settings.local.json`에 등록돼 있습니다.
- 슬래시 커맨드는 설치 후 에이전트 재시작 시 로드됩니다. (Node 22.12+ 권장)

---

## 🌿 브랜치 전략

| 브랜치 | 역할 |
|--------|------|
| `main` | 배포·안정 브랜치 (GitHub Pages 서빙 대상) |
| `develop` | 기본 개발 브랜치. 작업은 여기서, 안정화되면 `main`으로 머지 |

git 워크플로 스킬(`/commit` · `/branch` · `/pr` · `/release`)이 `.claude/skills/`에 준비돼 있어
`develop → main` 흐름에 맞춰 커밋·PR·릴리즈를 진행할 수 있습니다.

---

## 🙏 감사의 말

- 폰트: [SUIT](https://github.com/sunn-us/SUIT) by sun.us (SIL Open Font License)
- 데이터 출처: SOOP 월별 시청 리캡 (2025.12 ~ 2026.06)

<div align="center">
<br>
<sub>좀놀던괴물 · <code>mar5924</code></sub>
</div>
