# Lawform 정적 사이트 (GitHub Pages · 완전 무료)

이미지 한 장만 보여주는 정적 웹사이트입니다.  
**호스팅 비용이 나오지 않도록 AWS(S3/CloudFront)는 사용하지 않습니다.**  
무료인 [GitHub Pages](https://pages.github.com/) + 블루웹 DNS로 배포합니다.

저장소: https://github.com/lawform0511/lawform.kr

준비물:
- `index.html`
- `main-image.png`
- GitHub 계정 `lawform0511` (이미 연결됨)
- 블루웹에 등록된 도메인 `lawform.kr`

비용 안내:
- GitHub Pages 호스팅: **무료**
- HTTPS 인증서: GitHub가 **무료**로 발급
- AWS 계정/S3/CloudFront: **만들지 마세요** (유료로 과금될 수 있음)
- 도메인(`lawform.kr`) 연장 비용만 블루웹에서 원래대로 유지됩니다

---

## 1. 파일이 GitHub에 올라가 있는지 확인

1. https://github.com/lawform0511/lawform.kr 에 접속합니다.
2. 아래 파일이 보이는지 확인합니다.
   - `index.html`
   - `main-image.png`
   - `CNAME` (내용: `lawform.kr`)
3. 없으면 이 폴더에서 GitHub에 푸시합니다.

---

## 2. GitHub Pages 켜기 (무료 호스팅)

1. 저장소에서 **Settings**를 클릭합니다.
2. 왼쪽 메뉴에서 **Pages**를 클릭합니다.
3. **Build and deployment** → **Source**에서 **Deploy from a branch**를 선택합니다.
4. Branch를 `main`으로 선택합니다.
5. 폴더를 `/ (root)`로 선택합니다.
6. **Save**를 클릭합니다.
7. 잠시 후 같은 화면에 `https://lawform0511.github.io/lawform.kr/` 같은 주소가 보이면 배포된 것입니다.
   - 커스텀 도메인을 연결하면 나중에 `https://lawform.kr`로 접속합니다.

---

## 3. GitHub에 커스텀 도메인 등록

1. 저장소 **Settings → Pages**로 이동합니다.
2. **Custom domain**에 `lawform.kr`을 입력합니다.
3. **Save**를 클릭합니다.
4. DNS 반영 후 GitHub가 도메인을 확인합니다.
5. 확인이 끝나면 **Enforce HTTPS** 체크박스를 켭니다. (무료 HTTPS)

참고:
- `www.lawform.kr`도 같이 쓰려면 DNS에 www 레코드를 추가하면, GitHub Pages가 보통 apex ↔ www 리다이렉트를 처리합니다.

---

## 4. 블루웹 DNS에서 기존 공사 중(호스팅) 레코드 제거

목표: 블루웹 공사 중 페이지가 더 이상 나오지 않게 하기

1. 블루웹 관리자에 로그인합니다.
2. `lawform.kr` **DNS 관리**로 이동합니다.
3. 블루웹 웹호스팅을 가리키던 기존 레코드를 삭제합니다.
   - `@` / `lawform.kr`의 기존 A 레코드
   - `www`의 기존 A 또는 CNAME 레코드
4. 공사 중 페이지용 레코드가 남아 있으면 모두 제거합니다.

---

## 5. 블루웹 DNS를 GitHub Pages로 연결 (무료)

GitHub 공식 안내 IP를 사용합니다.  
참고: [GitHub Docs - Custom domain](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site)

### 루트 도메인 `lawform.kr` (A 레코드 4개)

호스트/이름을 `@` 또는 빈 값으로 하고, 아래 IP를 각각 A 레코드로 추가합니다.

| 유형 | 호스트 | 값 |
|------|--------|-----|
| A | `@` | `185.199.108.153` |
| A | `@` | `185.199.109.153` |
| A | `@` | `185.199.110.153` |
| A | `@` | `185.199.111.153` |

### www 도메인 (CNAME 1개)

| 유형 | 호스트 | 값 |
|------|--------|-----|
| CNAME | `www` | `lawform0511.github.io` |

저장 후 DNS 반영까지 수분~수 시간이 걸릴 수 있습니다.

---

## 6. lawform.kr 접속 확인

1. 브라우저에서 `https://lawform.kr` 접속을 확인합니다.
2. `https://www.lawform.kr` 접속도 확인합니다.
3. 화면에 `main-image.png` 한 장만 보이는지 확인합니다.
4. 예전 블루웹 공사 중 페이지가 보이면:
   - DNS가 아직 반영 중이거나
   - 기존 블루웹 레코드가 남아 있는 경우입니다.
5. 필요하면 시크릿 창에서 다시 확인합니다.
6. GitHub **Settings → Pages**에서 **Enforce HTTPS**가 켜져 있는지도 확인합니다.

임시 확인용(도메인 연결 전):
- `https://lawform0511.github.io/lawform.kr/`

---

## 7. 파일을 수정했을 때 업데이트 방법 (무료)

AWS 재업로드/캐시 무효화는 필요 없습니다.

1. 이 폴더에서 `index.html` 또는 `main-image.png`를 수정합니다.
2. GitHub에 다시 푸시합니다.
3. 1~2분 뒤 사이트에 반영됩니다.
4. 안 보이면 브라우저 강력 새로고침(Ctrl+F5)을 합니다.

---

## 로컬 확인 방법

1. 이 폴더에 `main-image.png`가 있는지 확인합니다.
2. `index.html`을 브라우저로 엽니다.
3. 이미지가 가운데 표시되는지 확인합니다.

---

## 절대 하지 말 것

- AWS S3 / CloudFront / Route 53 생성
- 유료 호스팅 상품 구매
- Access Key, 비밀번호를 코드에 넣기
