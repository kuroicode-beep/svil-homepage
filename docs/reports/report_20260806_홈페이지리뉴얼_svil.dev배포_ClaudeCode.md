# SVIL 대표 홈페이지 리뉴얼 완료 보고

- 작성: Claude Code · 2026-08-06
- 프로젝트: svil-homepage (`C:\Projects\svil-homepage`) + svil-home-api (`C:\Projects\svil-home-api`, 신규)
- 라이브: **https://svil.dev** (GitHub Pages + 커스텀 도메인, 2026-08-06 전환)

## 구현 범위

**프론트 (index.html 전면 재작성 + privacy.html 정비)**
- 콘텐츠: 슬로건 "Accessibility creates possibility." / 설립목적·철학(접근성 원칙 한 줄) / 연구 분야 5개(저시력자 앱·워크플로우·콘텐츠·시각장애 연구·교육 커리큘럼, 각 카드에 실측 재생목록·랜딩 링크) / 프로젝트 5그룹(접근성 도구 2종·문화취미 앱 3종·TXT 패밀리 8앱 생태계·Tether·진행중 2건) / 유튜브 재생목록 8종 / 블로그 큐레이션 3건 / 공지 / 문의 폼 / 구글 로그인
- 근거 자료: 아웃라인 「SVIL 홈페이지 기획」·「SVIL 프로젝트 현황」·「05. 연구소소개」, 유튜브 API 실측(@SVIL-LAB 영상 95·재생목록 8), 프로젝트 위키 4종(URL 정본 대조), 외부 링크 20개 전부 HTTP 200 확인
- 디자인: SVIL 표준 블루 토큰(구 골드 폐기) + Stitch 시안 적용(좌측 정렬 대형 히어로·흰색 슬로건 #edf5ff·radius 8px 버튼·프라이머리 로그인·2단 푸터·모노 섹션 라벨). Stitch 원본의 Tailwind CDN·구글폰트는 자체완결 규격 위반이라 배제
- 폰트: LINESeedKR-Rg 실번들(@font-face) — 방문자 미설치 대응. 가독성 버튼(글자 크기 16/18/20px, localStorage)
- i18n: ko(기본)/en/ja/zh/vi 5개 언어, 키 94개 패리티 검증, en 폴백
- 뉴런 배경: accent 토큰 색, 밀도 화면폭 비례 40~90개, 캔버스 0크기 자가복구. **소장님 지정으로 reduced-motion 무관 항상 애니메이션** (다른 모션은 접근성 설정 준수)
- 접근성: skip-link, 포커스 링 #ffd479, 터치타겟 50px, 최소 12px(미달 0 실측), 모바일 375px 가로 스크롤 없음
- 후원 QR: 소장님 지정으로 **대표 홈 제외** — 랜딩/배포 페이지 전용

**백엔드 (svil-home-api v0.1.0, 신규)**
- Express + SQLite. `POST /api/inquiries`(게스트 허용, rate limit 10분 5회 + honeypot) / 구글 OAuth(`/auth/google`) / `GET /api/me` / `GET /api/admin/inquiries`(관리자=kuroicode@gmail.com)
- Railway SVIL-Ghost 프로젝트 동거 배포: https://svil-home-api-production.up.railway.app (`/data` 볼륨, 다중 오리진 CORS: svil.dev + github.io + localhost)
- 구글 OAuth 웹 클라이언트 신규 생성(GCP blogger-svil 프로젝트) — 로그인 리다이렉트 302 검증. ⚠ 동의 화면 테스트 모드 — 일반 방문자 로그인은 프로덕션 게시 필요(기존 백로그와 동일 건)
- 공지사항: 별도 백엔드 없이 **Ghost `공지` 태그 + Content API**(공개 read 키) — 태그 글 발행 시 자동 노출, 현재 0건이라 빈 상태 문구
- 저장소: https://github.com/kuroicode-beep/svil-home-api (main)

## 검증 결과
- i18n 5개 언어 키 패리티 일치, 콘솔 에러 0
- 문의 폼 → Railway DB 실저장 왕복 확인(테스트 문의 1건 잔존), CORS preflight 204(svil.dev 오리진)
- 게스트 401 / 관리자 미로그인 403 / OAuth 미설정 시 503 / honeypot 무시 — 전부 실측
- svil.dev 라이브 반영·CDN 전파 확인(구 키 잔재 0)

## 발견·처리한 이슈
- svil-baduk Pages 404 → GitHub 저장소 링크로 처리
- 라인시드 Bd/Th 미보유 → Rg 단일 굵기 번들(합성 굵기)
- reduced-motion 환경(이 PC 포함)에서 뉴런 배경이 아예 안 그려지던 문제 → 정적 렌더 추가 후, 소장님 지정으로 항상 애니메이션으로 최종 변경
- 홈페이지 정본 URL 변경(svil.dev) → `svil-copyright` 스킬 정본 foot_home 갱신 완료. **기존 배포 페이지들(audio-hotkeys 등) 푸터 홈 링크 백필 필요** (구 주소는 리다이렉트되므로 급하지 않음)

## 남은 것
1. 구글 OAuth 동의 화면 프로덕션 게시 (일반 방문자 로그인 개방 시)
2. og:image 1200×630 자산 제작
3. 배포 페이지들 푸터 foot_home 백필 (svil.dev)
4. 제품군 서브페이지(TXT 패밀리 등) — 기획 문서 로드맵 3단계
5. `assets/web.zip`(Stitch 원본)은 저장소에 커밋하지 않음 — 참고자료로 로컬 유지
