# ATS Total Service — Landing Page

Sydney 기반 ATS Total Service Pty. Ltd. 공식 랜딩페이지입니다.

- 단일 HTML 파일 (`index.html`) + 로고 + 실제 차량/장비 사진 5장
- 영어/한국어 토글 지원
- 모바일 탭-투-콜 (0416 492 358)
- 의존성 없음 (Google Fonts만 외부 CDN)

---

## 📂 파일 구성

```
ats-landing/
├── index.html              # 메인 페이지 (스타일·스크립트 인라인)
├── logo.png                # 회사 로고
├── CNAME                   # GitHub Pages 커스텀 도메인 설정
├── README.md               # 이 파일
└── images/
    ├── truck.jpg           # Isuzu NLR 트럭 (Hero + Gallery)
    ├── van-trailer.jpg     # 밴 + 트레일러 (Waste 서비스 + Gallery)
    ├── mower-work.jpg      # Toro 4000 작업 현장 (Why Us 사이드바 + Gallery)
    ├── mower-result.jpg    # Toro TimeCutter + 잔디 결과 (Gardening + Gallery)
    └── firstmaint-van.jpg  # First Maint 밴 (계열사 카드 + Gallery)
```

총 사진 용량 약 1.5MB (웹 최적화 완료: 리사이즈 + JPEG quality 80~82 + progressive).

---

## 🚀 GitHub Pages 배포

### 1단계 — 저장소 생성 및 업로드
1. GitHub에서 새 public repository 생성 (예: `ats-landing`)
2. 이 폴더 전체(`index.html`, `logo.png`, `CNAME`, `images/` 폴더 통째로)를 업로드
3. `images/` 폴더가 같이 올라가야 사진이 표시됩니다

### 2단계 — Pages 활성화
1. 저장소 → **Settings → Pages**
2. **Source**: `Deploy from a branch`
3. **Branch**: `main` / **folder**: `/ (root)` → Save
4. 1~2분 후 `https://<username>.github.io/<repo>/` 에서 확인

### 3단계 — atstotal.com.au 도메인 연결

**A. 도메인 등록 사이트(GoDaddy / Crazy Domains 등) DNS 설정에서:**

Apex 도메인 (`atstotal.com.au`) — A 레코드 4개 추가:
```
A    @    185.199.108.153
A    @    185.199.109.153
A    @    185.199.110.153
A    @    185.199.111.153
```

www 서브도메인 — CNAME:
```
CNAME    www    <username>.github.io
```

**B. GitHub Pages 설정에서:**
1. Settings → Pages → **Custom domain**에 `atstotal.com.au` 입력 → Save
2. DNS 전파 완료 후(10분~24시간) **Enforce HTTPS** 체크박스 활성화

> CNAME 파일은 이미 포함되어 있어서 자동 처리됩니다.

---

## 📝 수정 가이드

### 텍스트 수정
모든 다국어 텍스트는 `data-en` / `data-ko` 속성:
```html
<h3 data-en="Cleaning" data-ko="청소">Cleaning</h3>
```

### 전화번호 변경
`index.html`에서 다음을 일괄 변경:
- 표시용: `0416 492 358`
- 링크용 (tel): `tel:+61416492358`

### 이메일 변경
`info@atstotal.com.au` 검색 → 일괄 치환

### 컬러 톤 변경
`<style>` 최상단의 `:root` 변수:
```css
--navy: #1B3A57;
--green: #2D6B3F;
```

### 사진 교체
같은 이름의 파일을 `images/` 폴더에 덮어쓰면 자동 반영. 권장 사양:
- 가로 1200~1600px, JPG progressive, 200~500KB
- 16:9 가로형 권장 (서비스 카드, Why Us 사이드바)
- 4:3 가로형 권장 (Hero, 계열사 카드)

### 추가 사진 넣기
**Cleaning / Painting 카드**에 사진을 추가하려면:
1. 사진을 `images/cleaning.jpg` / `images/painting.jpg`로 저장
2. `<div class="service-photo no-photo">` 부분을 다음으로 교체:
   ```html
   <div class="service-photo">
     <img src="./images/cleaning.jpg" alt="Cleaning service" loading="lazy" />
   </div>
   ```

**First Cleaning Sydney 카드**도 동일한 방식으로 교체 가능.

---

## 🎨 페이지 구성 (9개 섹션)

1. **Nav** — 로고 / 메뉴 / 언어토글 / 전화 CTA
2. **Hero** — 메인 메시지 + Isuzu 트럭 사진 + 신뢰 배지
3. **About** — 회사 소개 + 통계 4개
4. **Services** — Cleaning / Gardening / Waste / Painting 카드
5. **Process** — 1-2-3 단계 (다크 네이비 섹션)
6. **Why Us** — 4개 강점 + Toro 작업 현장 사이드바
7. **Fleet Gallery** — 5장 사진 마소닉 갤러리
8. **Group** — First Cleaning Sydney + First Maintenance 카드
9. **Contact** — 전화 카드 + 회사정보 + 문의 폼

추가: 모바일 화면 우하단에 **플로팅 콜 버튼** (그린, 펄스 애니메이션)
