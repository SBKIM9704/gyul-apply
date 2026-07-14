# 띵귤_ 채팅매니저 지원서

스트리머 **띵귤_** 채팅매니저 모집 지원용 1페이지 웹사이트.
7개월치 SOOP 시청 리캡 데이터를 시각화하고, 웹 풀스택 개발 역량을 함께 소개합니다.

빌드 도구 없이 `index.html` 하나로 동작하는 정적 사이트입니다.

## 로컬에서 보기

`index.html`을 브라우저로 바로 열면 됩니다. (이미지 로딩을 위해 간단한 서버 권장)

```bash
python3 -m http.server 8000
# http://localhost:8000 접속
```

## GitHub Pages 배포

정적 파일뿐이라 GitHub Pages 무료 호스팅으로 바로 올릴 수 있습니다.

### 1) 저장소 만들고 올리기

```bash
# (아직 원격이 없다면) GitHub에서 빈 저장소 생성 후:
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

> 저장소 이름을 `<본인아이디>.github.io`로 만들면 주소가 `https://<본인아이디>.github.io/` 로 더 짧아집니다.

- `.nojekyll` 파일이 포함돼 있어 Jekyll 처리 없이 파일이 그대로 서빙됩니다.
- `img/` 폴더와 `index.html`은 같은 위치(루트)에 있어야 이미지가 정상 표시됩니다.

## 파일 구조

```
gyul-apply/
├── index.html     # 페이지 전체 (HTML/CSS/JS 인라인)
├── img/           # SOOP 월별 리캡 원본 스크린샷 (증빙)
├── .nojekyll      # GitHub Pages용
├── README.md
└── CLAUDE.md      # 프로젝트 컨텍스트 / 작업 가이드
```

## 데이터 수정

시청 수치는 `index.html` `<script>` 안의 `months` 배열이 원본(SSOT)입니다.
이 배열만 고치면 차트·개근 스트릭·통계가 함께 갱신됩니다. (Hero와 `chart-foot`의 요약 문구는 하드코딩이라 함께 수정)
