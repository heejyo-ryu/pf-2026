# 류희정 포트폴리오 — VERSION 2 (GitHub 공유용 요약본)

GitHub Pages로 공유하기 위한 **요약본**입니다. `index.html` 하나로 완결되는 정적 페이지이며, 외부에서 불러오는 것은 Google Fonts(Noto Sans KR)뿐입니다. 스크린샷과 회사 로고는 base64로 파일 안에 포함돼 있어 별도 이미지 파일이 없습니다.

| 버전 | 용도 | 특징 |
|---|---|---|
| VERSION 1 | 로컬 보관 · 지원서 제출용 | 지표·협업 과정까지 상세 (접고 펼치기) — **GitHub에 올리지 않음** |
| **VERSION 2 (이 폴더)** | **GitHub Pages 공유용** | 구체 수치 없음 · 프로젝트별 문제/접근/결과 요약 · 인쇄 시 A4 3장 |

## 반드시 지켜야 할 조건: 검색 비노출

이 페이지는 검색에 노출되지 않아야 합니다. 아래 조건은 배포 전후로 항상 유지하세요.

1. `index.html`의 `<head>`에 다음 태그가 있어야 합니다. **삭제 금지.**

   ```html
   <meta name="robots" content="noindex, nofollow, noarchive">
   ```

2. 배포 후 확인: 페이지에서 "페이지 소스 보기"를 열어 위 태그가 있는지 확인합니다. 터미널에서는 다음으로 확인할 수 있습니다.

   ```bash
   curl -s https://<깃허브아이디>.github.io/<저장소이름>/ | grep -i noindex
   ```

3. `noindex`는 검색엔진 색인을 막을 뿐 접근 제한이 아닙니다. 무료 계정의 GitHub Pages는 저장소가 public이어야 하고, 주소를 아는 사람은 누구나 열 수 있습니다. 링크는 지원처 등 필요한 곳에만 전달하세요.
4. 저장소 소개(About)의 Website 항목에 Pages 주소를 넣거나, README·프로필에서 이 주소를 링크하지 마세요. 외부 링크가 늘면 검색에 잡힐 가능성이 높아집니다.
5. 저장소를 검색에서 더 가리고 싶다면 저장소 이름을 이력서와 무관한 이름으로 짓는 것도 방법입니다. (예: `pf-2026`)

## 폴더 구성

```
portfolio-v2/
├─ index.html   # VERSION 2 본체 (HTML·CSS·JS·이미지 포함)
├─ .nojekyll    # GitHub Pages가 파일을 가공하지 않고 그대로 서빙하게 하는 빈 파일
└─ README.md    # 이 문서
```

`.nojekyll`이 없다면 빈 파일로 하나 만들어 두세요(`touch .nojekyll`).

> 상세 버전(VERSION 1)의 `index.html`은 이 폴더에 두지 마세요. 이 폴더를 통째로 GitHub에 올리기 때문에, 같이 있으면 상세 내용이 그대로 공개됩니다. VERSION 1은 다른 폴더에 따로 보관하세요.

## 페이지 구성

| 영역 | id | 내용 |
|---|---|---|
| 히어로 | — | 이름, 한 줄 소개, 연락처 |
| 소개 | `#intro` | 1문단 |
| 역할 지도 | `#map` | 프로젝트 × 직무(기획/데이터분석/CX/브랜딩) |
| 경력 | `#career` | 웍스피어, 뱅크샐러드 (회사 로고 포함) |
| 프로젝트 | `#project-1` ~ `#project-6` | 최신순, 각 프로젝트는 **문제 / 접근 / 결과** 3블록 |
| 학력 | `#education` | |

맨 하단(푸터)에는 "더 자세한 내용(구체적인 지표와 협업 과정 등)은 문의해 주세요." 안내와 연락처가 있습니다. 이 문구는 수치를 뺀 요약본이라는 점을 알리는 역할이므로 유지하세요. 인쇄(PDF) 시에는 A4 3장으로 출력되며, 마지막 장 하단에 이 안내 문구만 표시됩니다(연락처는 1쪽 헤더에 있습니다).

- 1쪽: 히어로 · 소개 · 역할 지도 · 경력 · 학력
- 2쪽: 프로젝트 01~03
- 3쪽: 프로젝트 04~06

## 수정할 때 지킬 원칙

- **구체적인 수치를 넣지 않습니다.** 전환율·개선폭·사용률·비용·p값·항목 수 같은 숫자는 쓰지 말고 "상승", "유의하게 개선", "유지"처럼 방향과 결과만 적습니다. (날짜와 재직 기간은 괜찮습니다.)
- 내부 협의 과정의 세부 내용(상대 부서·파트너사와의 구체적 이견, 정책 세부 조건 등)도 이 버전에는 적지 않습니다. 필요하면 VERSION 1에 남겨 둡니다.
- 새 프로젝트를 추가할 때는 `<article class="project" id="project-n">` 블록을 복사하고, `id`, `<!-- PROJECT n -->` 주석, `<span class="proj-num">`, 상단 `<nav class="toc">`, 역할 지도 행을 함께 맞춥니다. 인쇄 페이지 수가 늘 수 있으니 `@media print`의 `#project-1`, `#project-4` 페이지 나눔과 `html{zoom:…}` 값도 확인하세요.
- 프로젝트마다 문제/접근/결과는 `<div class="pf"><h3>…</h3><p>…</p></div>` 형태입니다.
- 스크린샷(`.shot-row`)은 `<img src="data:image/jpeg;base64,…">`를 통째로 교체하면 됩니다. `loading="lazy"`는 쓰지 마세요.
- 이미지에 서비스 내부 정보나 수치가 노출되지 않는지 교체 전에 확인하세요.

## 로컬에서 미리보기

`index.html`을 브라우저로 더블클릭해 열면 됩니다. 빌드나 서버가 필요 없습니다. 우측 하단 **PDF로 저장** 버튼으로 A4 3장 PDF를 만들 수 있습니다. (인쇄 설정에서 "배경 그래픽"을 켜면 화면과 가장 비슷하게 나옵니다.)

## 배포 (GitHub Pages)

### Claude CLI로 배포하기

`portfolio-v2` 폴더에서 Claude CLI를 실행한 뒤 아래 요청을 그대로 붙여넣으세요. 사전 조건은 `git`과 `gh`(GitHub CLI) 설치, 그리고 `gh auth login` 완료입니다.

```text
이 폴더(portfolio-v2)를 GitHub Pages로 배포해줘.
1. 먼저 index.html에 <meta name="robots" content="noindex, nofollow, noarchive"> 태그가 있는지 확인해. 없으면 배포하지 말고 알려줘.
2. 폴더에 index.html, .nojekyll, README.md 외의 파일(특히 상세 버전 포트폴리오)이 없는지 확인해.
3. git init, 첫 커밋 "portfolio: version 2", 브랜치 main, 태그 v2 생성
4. gh로 public 저장소 생성(이름: portfolio) 후 main과 v2 태그를 push. 저장소 설명(description)과 Website 항목은 비워 둬.
5. GitHub Pages를 main 브랜치 / (root)로 활성화
6. 배포 URL이 열리면 소스에 noindex 태그가 포함돼 있는지 curl로 확인하고, URL을 알려줘.
index.html은 수정하지 마.
```

### 직접 명령어로 하기

```bash
cd portfolio-v2
git init
git add .
git commit -m "portfolio: version 2"
git branch -M main
git tag -a v2 -m "VERSION 2 (GitHub 공유용 요약본)"

gh repo create portfolio --public --source=. --remote=origin --push
git push origin v2

gh api --method POST -H "Accept: application/vnd.github+json" \
  repos/:owner/portfolio/pages \
  -f "source[branch]=main" -f "source[path]=/"
```

웹 화면에서 켜려면 저장소의 Settings → Pages → Build and deployment에서 Source를 "Deploy from a branch", Branch를 `main`, 폴더를 `/ (root)`로 선택하고 Save를 누릅니다. 최초 활성화 후 1~3분 뒤 `https://<깃허브아이디>.github.io/portfolio/`에서 열립니다.

배포 주소 확인:

```bash
gh api repos/:owner/portfolio/pages --jq .html_url
```

## 버전 관리

| 버전 | 태그 | 내용 |
|---|---|---|
| VERSION 1 | `v1` | 상세 버전 (로컬 보관, GitHub 미공개) |
| VERSION 2 | `v2` | GitHub 공유용 요약본: 수치 제거, 문제/접근/결과 요약, 인쇄 A4 3장, noindex 적용 |

수정해 새 버전을 낼 때:

```bash
git add .
git commit -m "portfolio: version 2.1"
git tag -a v2.1 -m "VERSION 2.1"
git push && git push origin v2.1
```

push하면 Pages가 자동으로 다시 배포됩니다.

## 공개 전 체크리스트

- [ ] `noindex` 메타 태그가 있다
- [ ] 폴더에 상세 버전(VERSION 1) 파일이 없다
- [ ] 본문에 구체적인 수치(%, 배, p값 등)가 없다
- [ ] 스크린샷에 내부 정보나 수치가 보이지 않는다
- [ ] 푸터·헤더의 연락처가 공개해도 되는 정보다
- [ ] 맨 하단에 "더 자세한 내용은 문의해 주세요" 안내가 있다
- [ ] 저장소 설명(description)과 Website 항목이 비어 있다
