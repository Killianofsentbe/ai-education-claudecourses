# Changelog — Anthropic Academy 한국어 학습 자료

## v2.1.0 — 2026-03-25

### 전체 디자인 통일 (6개 구버전 파일)

구버전 레이아웃으로 남아있던 02, 03, 09, 11, 13, 15번 파일을 01번 기준 신버전 디자인으로 완전 통일.

**변경 전 (구버전)**
- `position: fixed` 사이드바 + 상단 탭바(`top-bar`) 방식
- 파일마다 다른 색상 체계 및 헤더 구조

**변경 후 (신버전 통일)**
- CSS Grid 레이아웃 (`270px 사이드바 + 1fr 콘텐츠`)
- `position: sticky` 헤더(56px) + 사이드바(`top: 56px`)
- 표준 색상 체계 통일 (`--accent: #d97f3a`, `--accent2: #7b6ef6`)
- Anchor 기반 `lesson-nav` 사이드바 (탭바 제거)
- 신버전 헤더 구조 (브레드크럼 + 수강 배지)
- 다크/라이트 토글 버튼 — `quick-links` 영역으로 위치 통일

---

### 버그 수정

#### 02 / 09 / 13번 — nlm-banner 구조 오류
`<main>` 직후에 Academy·NotebookLM 버튼 `<a>` 태그 2개와 `</div>`가 고아 상태로 떠있던 문제 수정.
`nlm-banner` 내부 `nlm-banner-text` 닫힘 이후 올바른 위치에 버튼 재삽입 및 `</div>` 추가.

#### 02 / 09 / 13번 — 좌측 패널 클릭 불가
`showLesson()` 함수 내 `window.scrollTo(0, 0);` 다음 줄에 `});`가 잘못 삽입되어 JS 파싱 오류 발생 → 레슨 패널 전환 전체 불가. 해당 라인 제거.

---

### 콘텐츠 한글화

#### 04번 — AI Fluency: Framework & Foundations 레슨 제목 전면 번역
사이드바 nav 15개 레슨명 및 각 레슨 패널 `<h2>` 제목을 한글로 번역. (총 34개 항목)

| 영어 원문 | 한글 번역 |
|-----------|-----------|
| Introduction to AI Fluency | AI Fluency 소개 |
| Why Do We Need AI Fluency? | AI Fluency가 왜 필요한가? |
| The 4D Framework | 4D 프레임워크 |
| Generative AI Fundamentals | 생성형 AI 기초 |
| Capabilities & Limitations | 기능과 한계 |
| A Closer Look at Delegation | Delegation 심층 탐구 |
| Project Planning & Delegation | 프로젝트 계획과 Delegation |
| A Closer Look at Description | Description 심층 탐구 |
| Effective Prompting Techniques | 효과적인 프롬프팅 기법 |
| A Closer Look at Discernment | Discernment 심층 탐구 |
| The Description-Discernment Loop | Description-Discernment 루프 |
| A Closer Look at Diligence | Diligence 심층 탐구 |
| Conclusion | 마무리 |
| Certificate of Completion | 수료 인증 |
| Additional Activities | 추가 활동 |
| Swap Riddles / Cooperative Crosswords / Word Association | 수수께끼 교환 / 협력 크로스워드 / 단어 연상 |

유지 항목: 4D 핵심 용어(Delegation, Description, Discernment, Diligence), 카드 영어 tc-label, 저작권 표기

---

### 가이드 문서 업데이트 (guide.html)

| 항목 | 변경 전 | 변경 후 |
|------|---------|---------|
| 페이지 수 표기 | COURSE × 13 | COURSE × 15 |
| 강의 탐색 방식 | 탭 방식 | 사이드바 클릭 |
| 배너 버튼 설명 | `⬡ NotebookLM 열기` | `📺 원본 영상` + `⬡ NotebookLM` + 레슨별 개별 링크 |
| 영상 강의 번호 | 01·04·05·08·09·10 | 01·05·06·09·10·11 |
| 테이블 행 번호 | 10~13번이 09~12로 표기 (1씩 밀림) | 정상 수정 |
| 개발자 학습 경로 | 04→05→08→09/10 | 05→06→09→10/11 |
| Claude Code 경로 | → 13 에이전트 스킬 | → 14 에이전트 스킬 → 15 서브에이전트 |

---

## v2.0.0 — 2026-03-25 (당일 이전 세션)

### 신규 기능

#### Anthropic Academy 원본 영상 + NotebookLM 배너 추가 (전체 15개 강의)
모든 강의 페이지 상단에 배너 삽입.
- 기존 배너 있는 파일(01, 03, 06, 12, 15): Academy 버튼 추가
- 배너 없는 파일(02, 04, 05, 07, 08, 09, 10, 11, 13, 14): 배너 신규 삽입
- 배너 구조: `[⬡ 아이콘] [설명 텍스트] [📺 원본 영상 →] [⬡ NotebookLM →]`

#### 레슨별 원본 영상 링크 버튼 추가 (전체 15개 강의)
각 레슨 헤더에 해당 레슨의 Skilljar 개별 URL로 연결되는 `📺 레슨 N 영상 →` 버튼 삽입.
MD 파일의 `> 원본: https://anthropic.skilljar.com/...` 패턴을 파싱하여 레슨번호-URL 매핑.

#### 전체 페이지 다크/라이트 테마 토글
SentBe 디자인 시스템 기반 라이트 테마 CSS 변수 및 토글 버튼 추가.
`localStorage`에 테마 저장, 우측 상단 `quick-links` 영역 내 배치.

### 버그 수정

#### 헤더 겹침 해결
`position: fixed` `home-btn`이 헤더 로고와 동일 위치에 겹치는 문제.
home-btn 제거 + 헤더 로고 텍스트를 `← 강의 목록`으로 변경.

#### 탭바-배너 겹침 해결 (02, 09, 13번)
`<main>` 직후 배너 삽입 시 sticky `top-bar`가 올라오며 배너를 덮는 문제.
배너를 `<div class="content-wrap">` 안으로 이동.

---

## 커밋 이력

| 해시 | 내용 |
|------|------|
| `8083404` | docs: guide.html 전반 업데이트 |
| `52f04b2` | fix: 02/09/13 좌측 패널 JS 문법 오류 수정 |
| `ed3d7dc` | i18n: 04번 강의 레슨 제목·nav 전면 한글화 |
| `084b8e2` | fix: 02/09/13 nlm-banner 구조 오류 수정 |
| `87498d3` | refactor: 6개 구버전 파일 완전 신버전 통일 |
| `d5ba090` | refactor: 전체 레이아웃 통일 + 토글 위치 수정 |
| `afc9a57` | fix: 헤더 겹침 해결 |
| `c718c0b` | feat: 레슨별 원본 영상 링크 버튼 추가 |
| `a9805b5` | fix: 탭바-배너 겹침 해결 |
| `bf16279` | feat: Academy + NotebookLM 배너 추가 |
