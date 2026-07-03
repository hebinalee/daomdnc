# 변경 이력 — ㈜다옴디앤씨 소개 웹사이트

> 다옴디앤씨(DAOM D&C Co., Ltd.)의 공식 회사 소개 웹사이트 개발 기록입니다.  
> 단일 페이지(index.html) 구성의 정적 웹사이트로, GitHub Pages를 통해 배포됩니다.

---

## v0.5 — UI 전문화 개선 (2026-07-04)

**목적:** AI 생성 데모 느낌을 제거하고 기업 신뢰도에 맞는 UI로 전면 정제

### 주요 변경
- **폰트:** Google Fonts `Noto Sans KR` (400/500/700) 적용
- **아이콘:** 전체 이모지 → Heroicons 스타일 인라인 SVG로 교체
  - 회사 개요, 사업 분야 카드, 연락처, 파트너십 섹션 전체
- **CEO 카드:** 👤 이모지 → 이니셜 "권" 원형 텍스트 아바타
- **탭 UI:** 사업분야·실적 탭을 세그먼트 버튼 스타일로 변경
- **파트너십 섹션:** 이모지 카드 → `01/02/03/04` 번호 기반 그리드 레이아웃
- **전반적 정제:** border-radius 축소(4px), 여백·타이포그래피 미세조정

### 추가 파일
- `docs/deployment-guide.md` — GitHub Pages + 가비아 DNS 배포 가이드 (daom.co.kr 기준)

---

## v0.4 — 라이브 프리뷰 링크 추가 (2026-05-07)

커밋 `0c3051d`

- README에 raw.githack.com을 통한 라이브 미리보기 링크 추가
- 도메인 구매 전 임시 프리뷰 환경으로 활용

---

## v0.3 — 회사 주소 업데이트 (2026-05-07)

커밋 `d595237`

- 연락처 섹션 주소를 신규 이전지로 변경
  - 인천시 남동구 구월로37번길 10, 109동 1701호

---

## v0.2 — 브랜드 아이덴티티 적용 (2026-05-07)

커밋 `0c4453b`

- 로고 이미지 적용 (`assets/logo-horizontal.png`, `assets/logo-stacked.png`)
- 브랜드 컬러 `#01544A` 기반 색상 체계 수립
- 내비게이션, 히어로, 섹션 강조색 통일

---

## v0.1 — 초기 웹사이트 구축 (2026-05-07)

커밋 `d6303e0`, `2d163ca`

- 단일 HTML 파일(`index.html`) 기반 회사 소개 웹사이트 최초 구축
- 주요 섹션 구성:
  - 히어로 (Hero)
  - 대표이사 인사말 (CEO Message)
  - 회사 개요 (Company Overview)
  - 사업 분야 (Business Areas) — 탭 UI
  - 조직도 (Organization)
  - 파트너십 (Partnership)
  - 주요 실적 (Track Record) — 탭 UI
  - 연락처 (Contact)
- README 및 참고 자료(`references/`) 추가

---

## 배포 계획

| 항목 | 내용 |
|------|------|
| 호스팅 | GitHub Pages (무료) |
| 목표 도메인 | `www.daom.co.kr` |
| 도메인 등록 | 가비아 (gabia.com) |
| SSL | Let's Encrypt (GitHub Pages 자동 제공) |
| 배포 가이드 | [`docs/deployment-guide.md`](./deployment-guide.md) |
