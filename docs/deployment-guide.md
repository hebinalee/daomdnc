# 다옴디앤씨 웹사이트 배포 가이드

> 대상 도메인: `www.daom.co.kr`  
> 호스팅: GitHub Pages (무료)  
> 도메인 등록: 가비아 (연 약 2만원)

---

## 전체 흐름

```
[가비아] 도메인 구매 (daom.co.kr)
    ↓
[GitHub] GitHub Pages 활성화
    ↓
[가비아] DNS 레코드 설정
    ↓
[GitHub] 커스텀 도메인 등록 + HTTPS 활성화
    ↓
https://www.daom.co.kr 접속 확인
```

---

## Step 1. 가비아에서 도메인 구매

1. [gabia.com](https://www.gabia.com) 접속 → 로그인
2. 검색창에 `daom.co.kr` 입력 후 검색
3. 사용 가능 확인 후 장바구니 → 결제
   - 가격: 약 22,000원/년 (`.co.kr` 기준)
   - 기간: 최소 1년, 자동 갱신 설정 권장

---

## Step 2. GitHub Pages 활성화

1. GitHub에서 이 저장소(`daom`) 접속
2. **Settings** 탭 클릭
3. 왼쪽 사이드바 **Pages** 클릭
4. **Branch** 항목에서 `master` 선택, 폴더는 `/ (root)` 선택
5. **Save** 클릭
6. 잠시 후 아래 주소로 접속 확인:
   ```
   https://hebinalee.github.io/daom
   ```
   > 사이트가 정상 표시되면 다음 단계 진행

---

## Step 3. 가비아 DNS 설정

1. 가비아 로그인 → **My가비아** → **도메인** → `daom.co.kr` 선택
2. **DNS 정보** 또는 **네임서버/DNS 관리** 클릭
3. **DNS 관리** → **레코드 수정** 진입

### 추가할 레코드

#### A 레코드 4개 (루트 도메인 `daom.co.kr` 연결용)

| 타입 | 호스트 | 값 | TTL |
|------|--------|----|-----|
| A | `@` | `185.199.108.153` | 3600 |
| A | `@` | `185.199.109.153` | 3600 |
| A | `@` | `185.199.110.153` | 3600 |
| A | `@` | `185.199.111.153` | 3600 |

> `@`는 루트 도메인(`daom.co.kr`)을 의미합니다.

#### CNAME 레코드 1개 (`www.daom.co.kr` 연결용)

| 타입 | 호스트 | 값 | TTL |
|------|--------|----|-----|
| CNAME | `www` | `hebinalee.github.io.` | 3600 |

> 값 끝의 점(`.`)을 포함하여 입력하세요.

4. **저장** 클릭

---

## Step 4. GitHub Pages에 커스텀 도메인 등록

1. GitHub 저장소 → **Settings** → **Pages**
2. **Custom domain** 입력란에 아래 입력 후 **Save**:
   ```
   www.daom.co.kr
   ```
3. DNS 전파가 완료되면 **Enforce HTTPS** 체크박스가 활성화됨 → 클릭하여 HTTPS 강제 적용

---

## Step 5. DNS 전파 확인

DNS 전파는 보통 **30분 ~ 최대 24시간** 소요됩니다.

### 확인 방법 (터미널)

```bash
# www 레코드 확인
dig www.daom.co.kr

# 루트 도메인 확인
dig daom.co.kr
```

결과에 `hebinalee.github.io` 또는 GitHub IP(`185.199.x.x`)가 보이면 완료.

### 최종 접속 확인

브라우저에서 아래 주소 접속:
```
https://www.daom.co.kr
```

---

## 비용 요약

| 항목 | 비용 |
|------|------|
| GitHub Pages 호스팅 | 무료 |
| SSL 인증서 (Let's Encrypt) | 무료 |
| 도메인 `daom.co.kr` | 약 22,000원/년 |
| **합계** | **약 22,000원/년** |

---

## 참고: 이후 사이트 업데이트 방법

`index.html` 등 파일 수정 후 `master` 브랜치에 push하면 **자동으로 반영**됩니다. 별도 배포 작업 불필요.

```bash
git add .
git commit -m "feat: 내용 수정"
git push origin master
```

반영까지 보통 **1~2분** 소요.
