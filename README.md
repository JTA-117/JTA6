# JTA6 by JAY

세계지도에서 나라를 누르면 그 나라에서 정리한 상품 아이디어·이슈·금리 기록을 월별로 보여 주는 포트폴리오 사이트입니다.

## 파일

| 파일 | 내용 |
|---|---|
| `index.html` | 사이트 화면 + 편집 모드 |
| `data.json` | 기록 데이터 (편집 모드나 Claude가 고치는 파일) |
| `world.json` | 세계지도 모양 |
| `countries-ko.json` | 나라 한국어 이름 |

## 1. 인터넷에 올리기 (GitHub Pages, 무료)

1. github.com 가입
2. 오른쪽 위 **+ → New repository** → 이름 `jta6`, **Public** 선택 → Create
3. **Add file → Upload files** → 위 파일 4개(README 포함 가능)를 끌어다 놓고 **Commit changes**
4. 저장소 **Settings → Pages** → Source: **Deploy from a branch**, Branch: **main / (root)** → Save
5. 1~2분 뒤 주소가 생깁니다: `https://내아이디.github.io/jta6/`

> 주소를 `https://내아이디.github.io/`로 짧게 하고 싶으면 저장소 이름을 `내아이디.github.io`로 만드세요.

## 2. 사이트에서 직접 편집하기

1. GitHub **Settings → Developer settings → Personal access tokens → Fine-grained tokens → Generate new token**
   - Repository access: **Only select repositories → jta6**
   - Permissions: **Contents → Read and write**
   - 만료일은 적당히(예: 1년) 설정
2. 사이트 맨 아래 **편집**을 누르거나 주소 끝에 `#edit`를 붙여 엽니다.
3. GitHub 아이디·저장소 이름·토큰을 한 번 입력합니다. github.io 주소에서는 아이디·저장소가 자동으로 채워집니다.
4. 기록 추가·수정·삭제 → **GitHub에 저장** → 1~2분 뒤 사이트에 반영됩니다.

- 토큰은 내 브라우저에만 기억됩니다. 공용 PC에서는 "이 브라우저에 기억하기"를 끄세요.
- 편집 버튼은 누구에게나 보이지만, 토큰이 없으면 저장할 수 없습니다.
- 토큰 없이 고치고 싶으면 **data.json 복사** → GitHub에서 `data.json` 열기 → 연필(편집) → 붙여넣기 → Commit.

## 3. www 주소 붙이기 (선택, 도메인 비용 별도)

1. 가비아·Cloudflare·Namecheap 등에서 도메인 구입 (예: `jta6.kr`, `jta6.com`)
2. 도메인 관리 화면 DNS에 레코드 추가: **CNAME / 이름 `www` / 값 `내아이디.github.io`**
3. 저장소 **Settings → Pages → Custom domain**에 `www.jta6.kr` 입력 → Save → **Enforce HTTPS** 체크
4. DNS 반영까지 몇 분~몇 시간 걸릴 수 있습니다.

## 4. Claude에게 수정 맡기기

claude.ai **설정 → 연결(Connectors)**에서 GitHub를 연결하고 `jta6` 저장소 접근을 허용하면, Claude에게 "JTA6에 11월 한국 기록 추가해줘"처럼 말해서 바로 고칠 수 있습니다.

## data.json 기록 형식

```json
{
  "id": "2026-11-kor-예시",
  "country": ["KOR"],
  "month": "2026-11",
  "type": "idea",
  "status": "final",
  "credit": "개인 작성",
  "title": "제목",
  "summary": "요약",
  "points": ["핵심 포인트 1", "핵심 포인트 2"],
  "table": [{ "label": "국고 3년", "value": "2.85%", "change": "+5bp" }],
  "tableNote": "기준일·출처",
  "meaning": "상품·고객 의미",
  "sources": [{ "label": "출처 이름", "url": "https://..." }]
}
```

- `type`: `idea`(상품 아이디어) · `issue`(이슈) · `rate`(금리·환율)
- `status`: `final`(완성) · `draft`(초안)
- `country`: ISO 3글자 코드 (KOR, USA, FRA, DEU, BRA, JPN, CHN …)
