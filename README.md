# 포유스퀘어 (FOR YOU SQUARE) — 기업 홈페이지

`BUSINESS CONSULTING & TOTAL SERVICE`
2027년 기업 자금·경영 컨설팅 회사 홈페이지입니다. 빌드 도구 없이 동작하는 정적 페이지입니다.

## 폴더 구성

```
for-you-square/
├── index.html                  # 홈페이지 (단일 파일: HTML + CSS + JS)
├── assets/
│   ├── logo-horizontal.png     # 가로 로고 (투명 배경)
│   ├── logo-vertical.png       # 세로 로고 (투명 배경)
│   ├── favicon.png             # 256×256 (마크 타일)
│   ├── favicon-32.png          # 32×32
│   └── apple-touch-icon.png    # 180×180
├── .nojekyll                   # GitHub Pages에서 assets/ 등을 그대로 서빙
└── README.md
```

## 로고

원본 사진(`attachments/2026-11-25/1141-28cd886e22df444780e4d60f3ac7c470.jpg`)에서 두 로고를 잘라내고,
오프화이트 배경을 알파 채널로 제거했습니다.

- 단색 영역은 브랜드 색 그대로(불투명), 가장자리는 배경→로고색으로 알파를 계산해 안티에일리어싱을 유지했습니다.
- 원본 해상도 그대로 저장했습니다. (가로 1070×265, 세로 401×675)

## 페이지 구성

1. **헤더** — 스크롤 시 그림자, 모바일 햄버거 메뉴
2. **히어로** — "2027년 기업 자금과 경영 로드맵, 포유스퀘어가 함께 설계합니다" + 12월 결산 D-day 카드(자동 계산)
3. **지표** — 4개 핵심 서비스 / 6개 인증 분야 / 3단계 절차 / 1:1 전담
4. **핵심 서비스** — 운전자금 · 시설자금 · 기업인증 · 재무·신용관리 + 추가 토탈 서비스 4종
5. **2027 자금전략** — 11~12월 → 상반기 타임라인, 12월 결산 전 체크포인트 7항목
6. **상담 사례** — 익명 처리한 3건 (제조업 / 도소매업 / 서비스업)
7. **진행 절차** — 무료 진단 → 전략·서류 설계 → 신청·사후관리
8. **FAQ** — 아코디언 8문항 (`aria-expanded` 지원)
9. **무료 상담 신청** — FormSubmit 연동
10. **푸터** — 상호·대표·사업자등록번호·연락처·이메일·주소

## 상담 신청 폼

- 수신 주소: `realoio@naver.com` (FormSubmit)
- `fetch` AJAX로 전송하고, CORS·네트워크 문제로 실패하면 자동으로 일반 `<form>` POST로 전환합니다.
  일반 POST 방식은 `?submitted=1`로 되돌아와 완료 화면을 보여줍니다.
- **최초 1회 FormSubmit 활성화가 필요합니다.** 실제 신청이 한 번 들어오면 `realoio@naver.com`으로
  "Confirm your email" 메일이 오고, 그 안의 링크를 눌러야 이후 접수가 정상 전달됩니다.
- 스팸 방지를 위해 `_honey` 허니팟 필드와 `_captcha: false`를 사용합니다.

## 배포

GitHub Pages를 쓰는 경우, 저장소 루트에 이 폴더의 내용을 올리면 됩니다. `.nojekyll` 파일이 포함되어 있습니다.

```bash
git init
git add .
git commit -m "포유스퀘어 홈페이지"
git branch -M main
git remote add origin <저장소 주소>
git push -u origin main
```

`Settings → Pages → Source: Deploy from a branch → main / (root)` 로 설정하면
`https://<계정>.github.io/<저장소>/` 에서 열립니다.

## 게시 전 확인해 주세요

- **상담 사례의 구체적 수치·성과**는 일반적인 예시로 작성했습니다. 실제 실적과 다르면 수정이 필요합니다.
- 상담 사례의 업종·지역·규모 표기는 예시이며, 실제 고객사 정보로 바꿔도 됩니다.
- FAQ의 처리 기간(인증 1~4개월, 심사 2주~2개월 등)은 일반적인 기준입니다. 실제 진행 기준과 다르면 조정해 주세요.
- 무료 상담 가능 시간(평일 09:00–18:00)은 임의로 넣은 값입니다. 실제 운영 시간으로 바꿔 주세요.
- 대표자 개인 휴대전화 번호(010-9439-8802)가 그대로 노출됩니다. 회사 대표번호가 따로 있다면 교체를 권합니다.

## 브라우저 지원

최신 Chrome / Edge / Safari / Firefox, iOS·Android 기본 브라우저.
`IntersectionObserver`, CSS Grid, `backdrop-filter`를 사용하며, 모션 감소 설정(`prefers-reduced-motion`)을 존중합니다.
