## 대상
- 프로젝트: svil-homepage (+ svil-home-api 신규)
- 작업 폴더: C:\Projects\svil-homepage / C:\Projects\svil-home-api
- 세션 시각: 2026-08-06 21:13 (KST)

## 세션 요약
- SVIL 대표 홈페이지 전면 리뉴얼을 기획(아웃라인·유튜브 API·Ghost 실측)부터 라이브 배포까지 완결. 신규 백엔드(svil-home-api) 구축·Railway 배포·구글 OAuth 연동 포함.
- 라이브: **https://svil.dev** (GitHub Pages + CNAME 커스텀 도메인, 세션 중 소장님이 도메인 연결)

## 완료된 작업
- **프론트**: index.html 전면 재작성 + privacy.html 정비. 연구 분야 5개·프로젝트 5그룹(TXT 생태계 8앱 포함)·재생목록 8종·블로그 3건·공지·문의·후원제외·구글 로그인. SVIL 블루 토큰 + Stitch 시안(assets/web.zip, 좌측 히어로·흰 슬로건 #edf5ff·radius 8px·2단 푸터·모노 라벨). 라인시드 Rg 번들, 가독성 버튼(16/18/20px), 5개 언어 i18n 94키 패리티. 뉴런 배경 항상 애니메이션(소장님 지정, reduced-motion 게이트 제거) + 캔버스 0크기 자가복구. main 최종 커밋 `71ab9df`.
- **백엔드**: svil-home-api v0.1.0 (Express+SQLite) — POST /api/inquiries(게스트, rate limit+honeypot) / 구글 OAuth / GET /api/me / 관리자 문의 열람. Railway SVIL-Ghost 동거 `https://svil-home-api-production.up.railway.app` (/data 볼륨, 다중 오리진 CORS svil.dev+github.io). 저장소 https://github.com/kuroicode-beep/svil-home-api (최종 `594f3f1`).
- **구글 OAuth**: GCP `blogger-svil`에 웹 클라이언트 신규 생성(소장님 콘솔 조작 + 화면 읽기로 협업), Railway env 반영, /auth/google 302 검증.
- **공지**: Ghost `공지` 태그 + Content API(공개 read 키, index.html에 내장) — 태그 글 발행 시 자동 노출. 현재 0건.
- **검증**: 외부 링크 20개 HTTP 200, 문의 폼 실저장 왕복, CORS 204, 모바일 375px, i18n 패리티, 12px 미만 폰트 0.
- **문서**: 완료보고서 `docs/reports/report_20260806_홈페이지리뉴얼_svil.dev배포_ClaudeCode.md` (Vault `03_PRJ\svil-homepage\` 동기화), 아웃라인 「SVIL 홈페이지 기획」 §12 append(rev 8).
- **정리**: 워크트리 브랜치 2개(homepage-structure-analysis-9f2b71, planning-session-52ced7) 병합 확인 후 로컬·원격 삭제. `git worktree list` 원본만 남음.

## 진행 중 / 미완료 작업
- **구글 OAuth 동의 화면 테스트 모드** — 일반 방문자 로그인 개방하려면 GCP 콘솔에서 프로덕션 게시 필요(기존 백로그 "Google OAuth 앱 Production 승격"과 동일 건). 현재는 테스트 사용자(소장님)만 로그인 가능.
- og:image(1200×630) 자산 미제작.
- 배포 페이지들(audio-hotkeys 등) 푸터 foot_home을 svil.dev로 백필 필요 — `svil-copyright` 스킬 정본은 갱신 완료, 구 주소는 리다이렉트되므로 급하지 않음.
- 기획 문서 3단계(제품군 서브페이지) 미착수.
- 워크트리 폴더 `C:\Projects\svil-homepage\.claude\worktrees\planning-session-52ced7`가 세션 점유로 삭제 불가 — 세션 종료 후 폴더만 지우면 됨(git 등록은 이미 해제).
- Railway DB에 테스트 문의 2건 잔존(이름 "테스트"/"연동 테스트") — 관리자 열람 화면에서 지워도 무방.

## 주요 결정사항 / 규칙
- **후원 QR 섹션은 랜딩/배포 페이지 전용** — 대표 홈에는 넣지 않는다 (소장님 지정 2026-08-06).
- **뉴런 배경은 reduced-motion과 무관하게 항상 애니메이션** (소장님 지정). 그 외 모션은 접근성 설정 준수.
- **홈페이지 정본 URL = https://svil.dev** — svil-copyright 스킬 foot_home 갱신됨.
- 공지 게시판은 자체 백엔드 대신 Ghost 태그 연동으로 확정. 백엔드는 문의·인증만 담당.
- 백엔드 배치: SAC SQLite가 아닌 신규 서비스로 Railway Ghost 프로젝트 동거(문서 색인과 회원·문의 분리).

## 참고 정보
- 완료보고서(상세): `C:\Projects\svil-homepage\docs\reports\report_20260806_홈페이지리뉴얼_svil.dev배포_ClaudeCode.md`
- 아웃라인 기획 문서: `/doc/svil-BHmOWUAg46` (id 131e707c-0cc6-4c02-84b1-7ebe01042522) §12
- Ghost Content 공개 키는 index.html 상수 `GHOST_CONTENT_KEY`, 백엔드 URL은 `API_BASE`.
- Railway 서비스: SVIL-Ghost 프로젝트 > svil-home-api (env: SESSION_SECRET·GOOGLE_CLIENT_ID/SECRET·DB_PATH=/data/svil-home.db·FRONT_ORIGIN 다중).
- Stitch 참고 원본: `C:\Projects\svil-homepage\assets\web.zip` (커밋 제외, 로컬 참고용).

## 다음 세션 시작 시 할 일
1. (개방 원하면) OAuth 동의 화면 프로덕션 게시 → 일반 회원 로그인 실검증.
2. og:image 제작(1200×630) 후 index.html 메타에 추가.
3. 배포 페이지 푸터 foot_home 백필(svil.dev) — audio-hotkeys/site부터.
4. 기획 3단계 제품군 서브페이지(TXT 패밀리 우선) 착수 여부 소장님 확인.
