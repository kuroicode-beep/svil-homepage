## 대상
- 프로젝트: svil-homepage (+ 워크스테이션 드라이버)
- 작업 폴더: C:\Projects\svil-homepage
- 세션 시각: 2026-09-09 21:17 (KST)

## 세션 요약
- 직전 체크포인트(08-06) 이후 증분: 연구소 소개 첫 문단 교체 → 아웃라인 스캔으로 홈페이지 업데이트 후보 선별 → 공지 1호 발행 + 공지 로딩 결함 수정 → NVIDIA/AMD 드라이버 갱신.

## 완료된 작업
- 연구소 소개 첫 문단 5개 언어 교체 — 커밋 `69de4b6`(08-07), svil.dev 반영.
- 공지 1호 발행 — https://blog.svil.dev/svileun-ajig-mandeuleojineun-jungibnida/ (`공지` 태그 신설, 08-30).
- 공지 로딩 결함 수정 — `index.html` `loadNotices()`가 `filter=tag:gongji` 직접 조회(상수 `NOTICE_TAG_SLUG`). 커밋 `f4596d1`(08-30), svil.dev 공지 1건 표시 확인.
- 드라이버 갱신(09-09) — NVIDIA 616.64, AMD 칩셋 8.08.12.551 설치·실측 확인. 설치파일 삭제. 메모리 `driver-silent-install-exit-codes.md` 기록.
- 완료보고서: `docs/reports/report_20260909_공지1호발행_공지로딩수정_드라이버갱신_ClaudeCode.md` (Vault 동기화).

## 진행 중 / 미완료 작업
- **홈페이지 수치·링크 정정 미착수** — 유튜브 513편·12종, 재생목록 카운트 8종 전부 낡음, 신규 재생목록 4종(SVIL 스튜디오·스마트글라스·접근성·AI 워크플로우) 누락, 배포페이지 링크 github.io → `*.svil.dev` 4곳(audio-hotkeys·svil-tarot·smart-alt-tab·txtdrop), SVIL Baduk v0.16.0. **카운트를 숫자로 둘지 "500편+" 절삭 표기로 갈지 소장님 결정 대기.**
- SVIL Converse v0.2.0(private) 홈 노출 여부 판단 대기.
- 블로그 큐레이션 3건 갱신(현재 8월 초 글, 발행 303편).
- **재부팅 대기** — 칩셋 드라이버 마무리. SAW 유휴 시 소장님이 재부팅.
- Realtek 오디오·LAN·WiFi 최신 여부 미확인(Gigabyte 페이지 403) → GIGABYTE Control Center. BIOS F38 최신 여부 미조사.
- 기획 문서(svil-2026-08-37cvp3lmEH) A~E 잔여: OAuth 프로덕션 게시, 제품군 서브페이지.
- `assets/web.zip`(Stitch 원본)·`.claude/`는 커밋 제외 유지.

## 주요 결정사항 / 규칙
- 공지 = Ghost `공지` 태그(slug `gongji`) 직접 필터. 태그 목록 순회 금지(Ghost `limit=all` 100개 절삭, 태그 880개).
- 공지글은 24섹션 발행 규격 대상 아님 → `publish-post.mjs` 대신 MCP `ghost_create_post`로 발행.
- 드라이버 무인 설치는 종료 코드로 판정하지 않고 `nvidia-smi`·레지스트리로 실측.

## 참고 정보
- 아웃라인: 「SVIL 홈페이지 기획」 `/doc/svil-BHmOWUAg46` §13 · 「SVIL 홈페이지 업데이트 기획 (2026-08)」 `/doc/svil-2026-08-37cvp3lmEH` · 「SVIL 프로젝트 현황」 `/doc/svil-1aff3RfvQb`
- Ghost Content 키·백엔드 URL: `index.html` 상수 `GHOST_CONTENT_KEY`·`API_BASE`(변경 없음)
- 유튜브 채널 ID `UCZEkC-EEul7bXAzrJzQpP7w`, 재생목록 12종 ID는 완료보고서 §2 조사 로그 참조(API 재실측 권장)

## 다음 세션 시작 시 할 일
1. 소장님께 재생목록 카운트 표기 방식 확인 → 홈페이지 수치·링크 정정 일괄 커밋·배포
2. 신규 재생목록 4종 추가 + 블로그 큐레이션 3건 교체
3. SVIL Converse 노출 여부 확인
4. 재부팅 여부 확인 → RebootPending 해제 확인
