# DESIGN.md — 먹과 한지 (Meok & Hanji)
> Korean archive gallery on hanji paper

**Theme:** mixed
**상태:** 2026-08-03 채택 확정 — [[index]]에 전면 적용 완료 (구현 원천). 검토 이력은 [[STYLE_REF_MeokHanji]].
**원전:** [[STYLE_REF_Structured]] (Structured — Renaissance gallery on putty paper)의 한국 문화유산 번안. 원전의 편집 원리(플랫, 하드컷 명암 교차, 세리프 디스플레이, 절제)는 계승하되, 한글 타이포그래피·R&D 사이트 정보 밀도·유산 이미지 자산에 맞게 재설계함 (2026-08-03 작성, 색 명암비 전 조합 실측).

Meok & Hanji는 국가 R&D 문화유산 연구를 기록보관소이자 갤러리로 취급한다: 따뜻한 한지 베이지 캔버스, 먹빛 다크 섹션, 그리고 장식을 전담하는 한국 문화유산 원본 이미지. 타이포그래피가 주인공이다 — 라틴 워드마크(ULSOO)는 극단적 크기와 네거티브 트래킹으로 새긴 듯한 형상을 만들고, 한글 디스플레이는 명조 계열로 같은 목소리를 내되 한글 고유의 규칙(트래킹 억제, 행간 확보)을 따른다. 섹션은 한지(밝음)와 먹(어두움)을 그라디언트 없이 하드컷으로 교차한다. 그림자 없음, 그라디언트 없음, 악센트는 금(金) 단 하나. 원전이 유화로 했던 일을 여기서는 실제 문화유산이 한다 — 은유가 아니라 본질이므로 더 정합적이다.

## Tokens — Colors

| Name | Value | Token | Role |
|------|------|-------|------|
| Hanji (한지) | `#e7e0d2` | `--color-hanji` | 지배적 페이지 캔버스 — 밝은 섹션 전체를 채우는 따뜻한 종이 베이지. 시스템에서 가장 많이 쓰이는 색, 갤러리 벽의 톤을 결정 |
| Meok (먹) | `#171310` | `--color-meok` | 다크 섹션 캔버스 + 밝은 섹션의 본문 텍스트. 순수 #000이 아닌 따뜻한 먹빛 — 실제 먹은 완전한 검정이 아니다 |
| Baekja (백자) | `#f2ede2` | `--color-baekja` | 카드·엘리베이티드 서피스. 한지보다 한 단계 밝아 그림자 없이 미묘한 레이어링을 만든다 |
| Hoebaek (회백) | `#cfc7b4` | `--color-hoebaek` | 헤어라인 보더 전용. 인쇄된 종이의 가장자리처럼 읽혀야 하며 UI 구분선처럼 강해지면 안 됨 |
| Dammuk (담묵) | `#4f4839` | `--color-dammuk` | 뮤트 보조 텍스트. 먹을 물에 푼 농담(濃淡) — 순먹이 과할 때 쓰는 가장 어두운 웜 그레이 |
| Geum (금) | `#d6a452` | `--color-geum` | **시스템의 유일한 채도 악센트.** 다크 섹션의 KPI 숫자·강조 전용. 현행 사이트 `--ulsoo-gold` 승계 (전통색 5종 중 단독 생존) |
| Geum-deep (진금) | `#7d5a1c` | `--color-geum-deep` | 밝은 섹션에서의 금 — Geum 원색은 한지 위에서 명암비 1.72:1로 텍스트 불가하므로, 텍스트 레벨 악센트는 반드시 이 값 사용 |
| Seolbaek (설백) | `#f7f3ea` | `--color-seolbaek` | 먹 섹션 위의 리버스 타입과 흰 스트로크 전용. 대형 서피스로 쓰지 않는다 |

### 명암비 실측 (WCAG, 2026-08-03)

| 조합 | 비율 | 판정 |
|------|------|------|
| Meok on Hanji (본문) | 14.06:1 | AAA |
| Dammuk on Hanji (뮤트) | 6.90:1 | AA+ (원전 Graphite on Putty의 경계선 명암비 문제를 해소) |
| Seolbaek on Meok (다크 본문) | 16.68:1 | AAA |
| Geum on Meok (다크 악센트) | 8.17:1 | AAA |
| Geum-deep on Hanji (라이트 악센트) | 4.77:1 | AA |
| Geum on Hanji | 1.72:1 | **텍스트 금지 — 장식(헤어라인·아이콘)만 허용** |

## Tokens — Typography

### Display Serif — 브랜드 보이스. 이중 규칙 (라틴/한글)

원전의 심장인 세리프 디스플레이는 라틴 전제 설계이므로, 같은 목소리를 두 문자 체계에 맞는 두 규칙으로 나눈다. **이 이중 규칙이 이 번안의 핵심이다.**

**라틴 (워드마크·영문 헤딩):**
- **서체:** Playfair Display (또는 Canela, Tiempos Headline, GT Super)
- **Weights:** 400, 500
- **워드마크 "ULSOO":** `clamp(120px, 24vw, 300px)`, weight 500, letter-spacing -0.03em, line-height 0.84 — 뷰포트 가장자리에서 의도적으로 크롭. 새긴 듯한 단일 형상으로 읽히게 한다
- **영문 섹션 헤딩:** 52–94px, letter-spacing -0.01em, line-height 0.9

**한글 (국문 헤딩·디스플레이):**
- **서체:** Noto Serif KR (또는 조선명조, 마루 부리)
- **Weights:** 400, 600
- **디스플레이:** `clamp(48px, 10vw, 110px)`, letter-spacing -0.01em **이하 금지**, line-height 1.08 **이상 필수** — 한글은 네거티브 트래킹과 압축 행간에서 뭉개진다. 크기가 아니라 여백과 대비로 드라마를 만든다
- **국문 섹션 헤딩:** 34–56px, letter-spacing 0 ~ -0.01em, line-height 1.15

### Utility Sans — 기능 전담 그로테스크 · `--font-sans`
- **서체:** Pretendard (현행 승계 — 한글 최적화 그로테스크, 원전의 Helvetica Now 역할)
- **Substitute:** Inter, Noto Sans KR, system-ui
- **Weights:** 400, 500, 700(숫자 전용)
- **Sizes:** 11, 12, 14, 16, 18, 22px — **11px 미만 금지** (원전의 9px 마이크로 라벨은 한글 가독성 불가로 하한 상향)
- **Role:** 본문, 내비, 버튼, KPI 숫자, 캡션. 디스플레이 임무를 절대 맡지 않는다 (상한 43px)

### Type Scale

| Role | Size | Line Height | Letter Spacing | Token |
|------|------|-------------|----------------|-------|
| micro | 11px | 1.4 | +0.06em (uppercase 라벨) | `--text-micro` |
| body-sm | 14px | 1.6 | 0 | `--text-body-sm` |
| body | 16px | 1.7 | 0 | `--text-body` |
| subheading | 22px | 1.4 | -0.005em | `--text-subheading` |
| heading-sm (serif-ko) | 28px | 1.3 | -0.005em | `--text-heading-sm` |
| heading (serif-ko) | 44px | 1.15 | -0.01em | `--text-heading` |
| display-ko (serif-ko) | clamp(48px, 10vw, 110px) | 1.08 | -0.01em | `--text-display-ko` |
| display-latin (serif-en) | clamp(120px, 24vw, 300px) | 0.84 | -0.03em | `--text-display-latin` |

한글 본문 행간을 원전(1.5)보다 넉넉하게(1.6–1.7) 잡는다 — 한글의 시각적 밀도가 라틴보다 높다. `word-break: keep-all; overflow-wrap: break-word;`는 전 섹션 유지 (13차 작업 확정 사항).

## Tokens — Spacing & Shapes

**Base unit:** 4px
**Density:** compact — 단, R&D 정보 사이트의 밀도 요구를 원전의 마케팅 저밀도보다 우선한다

### Spacing Scale

| Name | Value | Token |
|------|------|-------|
| 4 | 4px | `--spacing-4` |
| 8 | 8px | `--spacing-8` |
| 16 | 16px | `--spacing-16` |
| 24 | 24px | `--spacing-24` |
| 32 | 32px | `--spacing-32` |
| 40 | 40px | `--spacing-40` |
| 56 | 56px | `--spacing-56` |
| 64 | 64px | `--spacing-64` |
| 96 | 96px | `--spacing-96` |

### Border Radius

| Element | Value |
|---------|-------|
| cards | 9px (원전 계승 — 표준값 4/8/12px 회피가 시스템 정체성) |
| links | 2px |
| buttons | 999px (풀 필) |

### Layout

- **Section gap:** 64px — 원전 80px에서 하향 (11차 작업의 섹션 간격 축소 결정 유지)
- **Card padding:** 24px
- **Element gap:** 8px

## Components

### Hero Wordmark
**Role:** 브랜드 디스플레이 — 시스템을 규정하는 요소

"ULSOO"를 **붓글씨(모필) 서체**로, Meok 색, display 스케일 `clamp(110px, 24vw, 300px)`, 미세 기울임(rotate −1.2deg)으로 손으로 쓴 물성을 준다 (2026-08-03 방향 확정 — 세리프 워드마크에서 변경). 항상 화면보다 커 보여야 한다는 원칙은 유지. 한글 부제는 display-ko(명조) 규칙으로 별도 배치 — 붓 워드마크와 한 덩어리로 묶지 않는다.

- **서체: East Sea Dokdo (동해독도체) 확정** — 갈필(渴筆)의 거친 속도감 (2026-08-03 사용자 확정, B안. A안 Nanum Brush Script 기각)
- **붓 서체 규칙:** 네거티브 트래킹 금지(획의 자연 간격 보존), 행간 0.9, weight 400 단일. **붓 서체는 워드마크 전용** — 헤딩·본문·버튼에 사용 금지 (세리프=감정, 그로테스크=기능, 붓=서명이라는 3역 분담)
- 장기적으로는 폰트가 아닌 **실제 붓글씨 레터링(SVG)** 이 최종 지향점 — 폰트는 그 대체재다

### Section Header (이중 언어)
**Role:** 섹션 디스플레이 헤딩

KO 모드: Noto Serif KR 44–56px weight 600, 한글 규칙 적용. EN 모드: Playfair Display 52–94px weight 500, 라틴 규칙 적용. Meok on 한지 / Seolbaek on 먹. 반대편 코너에 11px uppercase 섹션 라벨(`01 — JOURNEY` 형식) 짝지음.

### KPI Stat (카운트업 승계)
**Role:** 검증 수치 표시 (애셋 31,022 · 사업화 23건 등)

숫자는 Pretendard 700, 다크 섹션에서 Geum, 라이트 섹션에서 Meok. 라벨은 11px uppercase Dammuk. 보더·배경 없음 — 원전 Stat Pair의 원리. 카운트업 인터랙션은 현행 유지.

### Pill Action Button
**Role:** 주 CTA — 뷰포트당 하나

Meok 배경, Seolbaek 텍스트, Pretendard 13px, padding 10px 20px, radius 999px, 보더·그림자 없음. 다크 섹션에서는 반전(Seolbaek 배경/Meok 텍스트). **금색 버튼 금지** — 금은 텍스트·숫자 악센트이지 CTA 색이 아니다.

### Ghost Text Link
**Role:** 내비게이션·인라인 링크

텍스트만, 배경 없음, hover 시에만 underline. 현행의 "바로 확인하기 ↗"·"과제 홈페이지 방문 ↗" 링크가 이 컴포넌트로 통일된다.

### Circular Heritage Vignette
**Role:** 피처 이미지 — 원형 크롭

문화유산 이미지의 원형 크롭(~200px), 보더·그림자 없음, serif 캡션 동반. 핵심기술 3분야·연구 여정 패널에 적용. 원전의 Circular Feature Vignette 직계.

### Heritage Panel (원전의 Classical Painting Panel 번안)
**Role:** 풀블리드 분위기 이미지

**르네상스 유화의 자리를 한국 문화유산 원본이 대신한다** — 광개토대왕비, 화성, 진묘 벽화 등. 엣지-투-엣지, 보더·라운드·오버레이 없음. 분위기 전담이며 콘텐츠 자산이 아니다.

### Functional Image Card (원전에 없는 추가 컴포넌트)
**Role:** 연구 결과물 스크린샷의 자리

원전은 "유화 아니면 아무것도"이지만 R&D 사이트는 실증 결과를 보여야 한다. 이원 규칙으로 해소: **풀블리드·원형 크롭 = 유산 원본만 / 연구 스크린샷 = 카드 내부의 기능 이미지로만** (Baekja 카드, 9px radius 내부에 담김). 스크린샷이 분위기 이미지로 승격되는 것을 금지.

### Logo Mark (현행 승계 — 팔레트 원칙의 유일한 예외)
**Role:** 브랜드 마크 — 헤더 좌상단

현행 사이트의 **오방색 붓획 SVG 로고**(navy `#173d7a` · red `#9a2b24` · teal `#249aa4` · gold `#d6a452` · coral `#e45f42`)를 그대로 유지한다 (2026-08-03 확정 — 스타일 개편에서 로고는 불변). "금 단일 악센트" 원칙은 **UI 팔레트**의 규칙이며 로고는 브랜드 아이덴티티로서 예외다 — 은퇴한 전통색들은 로고 안에서만 생존한다. 헤더에서 ~46px, 워드마크 텍스트("ULSOO" 붓 서체 소형 + 영문 부제 10px)와 짝지음. 원전의 "circled 'S' monogram" 자리를 대신하며, "The only graphic mark on the page" 원칙은 동일하게 적용 — 로고 외 그래픽 마크 금지.

### Header (원전에서 의도적으로 이탈)
**Role:** 내비게이션

원전은 "로고 + 링크 1개, 메뉴바 없음"이나, 6섹션 R&D 사이트는 내비와 언어 토글이 기능 요건이다. 절충: 워드마크(소형) + 텍스트 온리 내비(Ghost Link, 보더·배경 없음) + EN 토글. 헤더 배경은 캔버스와 동일색(스크롤 시에도 그림자 없이 헤어라인 보더만). ≤640px 부제 숨김 유지 (13차 작업).

## Do's and Don'ts

### Do
- 한지 섹션과 먹 섹션을 그라디언트 없이 하드컷으로 교차시킬 것 — 깊이는 명암 교차에서 나온다
- 세리프는 문자 체계별 이중 규칙을 반드시 따를 것: 라틴은 압축(행간 0.84, 트래킹 -0.03em), 한글은 확보(행간 ≥1.08, 트래킹 ≥-0.01em)
- 금(Geum)을 유일한 악센트로 유지할 것 — 다크 섹션 숫자·강조에 원색, 라이트 섹션 텍스트에는 Geum-deep
- 풀블리드·원형 이미지는 문화유산 원본만, 연구 스크린샷은 카드 내부로만
- 본문은 Pretendard 14–16px, 행간 1.6–1.7, `keep-all` 유지
- 카드 radius 9px, 버튼 풀 필 — 표준값(4/8/12px) 회피가 시스템 정체성
- 검증 수치(31,022·23건·95% 등)는 표기·단위를 변경하지 말 것 ([[IMPLEMENTATION_SPEC]] §0 절대 규칙 유지)

### Don't
- 금 이외의 채도 색 도입 금지 — 현행 teal(`#249aa4`)·red(`#9a2b24`)·coral(`#e45f42`)은 UI에서 은퇴한다 (**예외: 오방색 붓획 로고 마크** — Logo Mark 컴포넌트 참조)
- 그림자·그라디언트 금지 — 시스템은 완전히 플랫하다
- 한글에 라틴 디스플레이 규칙(네거티브 트래킹·0.84 행간) 적용 금지 — 글자가 뭉개진다
- Geum 원색을 한지 배경 위 텍스트로 사용 금지 (1.72:1 실측) — 장식 요소만 허용
- 세리프로 본문 조판 금지 — 세리프는 순간(모먼트), 산세리프는 시스템
- 11px 미만 텍스트 금지 (원전 9px 하한의 한글 번안)
- 연구 스크린샷·사진을 풀블리드 분위기 이미지로 승격 금지 — 그 자리는 유산 원본의 것

## Surfaces

| Level | Name | Value | Purpose |
|-------|------|-------|---------|
| 0 | Hanji Canvas | `#e7e0d2` | 밝은 섹션 기본 배경 — **한지 질감 오버레이 동반** (아래 질감 규칙) |
| 1 | Baekja Card | `#f2ede2` | 카드·엘리베이티드 서피스 |
| 2 | Seolbaek Base | `#f7f3ea` | 푸터·최상단 밝기 티어 (대형 사용 자제) |
| 3 | Meok Room | `#171310` | 다크 섹션 캔버스 — 성과 대시보드·피처 블록 |

### 한지 질감 규칙 (2026-08-03 개정 — 실제 스캔 이미지 채택)

캔버스는 민무늬 단색이 아니라 **실제 한지의 물성**을 갖는다. 구현은 사용자 제공 한지 스캔(닥나무 섬유 결 실물, 원본 `docs/blank-craft-paper-texture-background-vertical_7190-4606.avif` 493×740)을 **2×2 거울 타일**로 가공한 `assets/img/hanji-texture.webp` (986×1480, 22KB — 좌우·상하 반전 조합으로 반복 이음매 제거):

```css
background-color: var(--hanji);
background-image: url('assets/img/hanji-texture.webp');
background-size: 900px auto;
background-blend-mode: multiply;   /* 스캔 원색을 Hanji 토큰에 정박 */
```

- multiply 블렌드가 스캔의 밝은 원색을 Hanji `#e7e0d2` 톤으로 끌어내려, 텍스처를 바꿔도 팔레트가 흔들리지 않는다
- 질감은 라이트 캔버스 전용 — 먹 룸(다크 섹션)은 무광 먹빛 그대로 둔다
- 텍스트 명암비는 실측 여유(본문 14.06:1, 뮤트 6.90:1) 내에서 안전
- SVG feTurbulence 프로시저럴 노이즈(구 규칙)는 이미지 로드 실패 시 폴백으로만 유지 가능
- "그라디언트·그림자 금지" 원칙과 충돌하지 않는다 — 질감은 엘리베이션이 아니라 재질이다

## Imagery

한국 문화유산 원본 — 비석 탁본, 궁궐·성곽 건축, 고분 벽화, 유물 정밀 촬영. 처리 방식은 원전과 동일: 풀블리드 캔버스형 재현과 원형 크롭, 프레임·보더 없음. **장식의 전량을 유산 이미지가 전담한다** — 추상 그래픽 없음, 스톡 사진 없음. 연구 결과물 스크린샷은 장식이 아닌 증거이므로 카드 내부에만 배치한다(Functional Image Card). 이미지 소스는 [[CONTENT_SPEC]]의 이미지 마스터 목록(보고서 페이지 단위 소스 지정)을 따르고, 저작권 공개 범위 미확정 이미지는 사용 보류.

## Layout

풀블리드 섹션, 하드컷 명암 교차(한지 → 먹 → 한지). 히어로: 한지 캔버스 상단에 작은 타입 클러스터(부제·KPI·CTA), 하단을 거대한 ULSOO 라틴 워드마크가 지배. 6섹션 IA(Hero / 연구 여정 / 핵심기술 / 실증사례 / 연구성과 / 연구진)와 데이터 계층(`data.js`·i18n·검증 수치)은 현행 그대로 유지 — **이 문서는 표현 계층만 교체하는 리스킨 명세다.** 성과 대시보드는 먹 룸(다크 섹션)에 배치해 금색 숫자가 유일한 색으로 빛나게 한다. 섹션 리듬에 넉넉한 수직 여백, 단 섹션 갭은 64px(현행 축소 결정 유지).

## Agent Prompt Guide

### Quick Color Reference
- Background (light): #e7e0d2 (Hanji)
- Background (dark): #171310 (Meok)
- Card surface: #f2ede2 (Baekja)
- Text primary: #171310 on light / #f7f3ea on dark
- Text muted: #4f4839 (Dammuk)
- Border: #cfc7b4 (Hoebaek)
- Accent: #d6a452 (Geum, 다크 섹션 전용) / #7d5a1c (Geum-deep, 라이트 섹션 텍스트)
- Primary action: Meok 필 버튼 (악센트 색 CTA 없음)

### Example Component Prompts

1. **Hero Section**: 풀블리드 #e7e0d2 배경. 상단 좌측 소형 워드마크, 우측 텍스트 내비+EN 토글(Pretendard 12px, #171310, 배경 없음). 중앙 클러스터: 한글 부제(Noto Serif KR 28px weight 600, #171310, 행간 1.3) → KPI 4종 인라인(Pretendard 16px weight 700 숫자 + 11px uppercase 라벨 #4f4839) → 먹색 필 버튼(#171310 배경, #f7f3ea 텍스트, radius 999px). 하단: "ULSOO" Playfair Display clamp(120px,24vw,300px) weight 500, #171310, letter-spacing -0.03em, line-height 0.84, 뷰포트 가장자리 크롭.

2. **Dark Dashboard Section (연구성과)**: 풀폭 #171310 배경. 중앙 헤딩 "연구성과" Noto Serif KR 48px weight 600 #f7f3ea (EN: "OUTCOMES" Playfair 94px letter-spacing -0.01em). 집계 숫자는 Pretendard 700, **#d6a452** — 페이지에서 유일하게 색이 존재하는 순간. 라벨 11px uppercase #f7f3ea 60% 불투명.

3. **Heritage Panel + Floating Card (연구 여정)**: 풀블리드 유산 이미지(보더·오버레이 없음). 중앙에 #171310 카드(radius 9px, padding 24px), 내부에 Seolbaek 세리프 캡션과 Ghost Link "과제 홈페이지 방문 ↗".

4. **실증사례 카드**: #f2ede2 카드, radius 9px, 헤어라인 보더 #cfc7b4. 내부 상단에 연구 스크린샷(기능 이미지 — 카드 밖으로 나가지 않음), 제목 Noto Serif KR 22px, 본문 Pretendard 14px #4f4839, 좌하단 Ghost Link.

## Typographic Philosophy

원전과 동일한 원리 — 드라마는 색과 굵기가 아니라 크기와 트래킹에서 나온다 — 를 계승하되, 그 실행을 문자 체계별로 분리한다. 라틴은 커질수록 조이고(트래킹 -0.03em, 행간 0.84) 한글은 커질수록 지킨다(트래킹 하한 -0.01em, 행간 하한 1.08). 세리프가 모든 감정 노동을, 그로테스크가 모든 기능 노동을 담당하며 둘을 경쟁시키지 않는다. 한/영 토글 시 두 규칙이 교대하는 것이 이 사이트만의 타이포그래피 서명이 된다.

## Similar Brands

- **Aesop** — 절제된 웜 베이지 팔레트 + 세리프 디스플레이 + 갤러리형 제품 프레젠테이션
- **The Met / 국립중앙박물관 e뮤지엄** — 유물 원본 이미지가 장식을 전담하는 풀블리드 사용
- **Framework (framework.so)** — 세리프+그로테스크 페어링과 극단적 크기 대비
- **Structured** — 본 문서의 원전 ([[STYLE_REF_Structured]])

## Quick Start

### CSS Custom Properties

```css
:root {
  /* Colors */
  --color-hanji: #e7e0d2;
  --color-meok: #171310;
  --color-baekja: #f2ede2;
  --color-hoebaek: #cfc7b4;
  --color-dammuk: #4f4839;
  --color-geum: #d6a452;
  --color-geum-deep: #7d5a1c;
  --color-seolbaek: #f7f3ea;

  /* Typography — Font Families */
  --font-serif-latin: 'Playfair Display', 'Canela', Georgia, serif;
  --font-serif-ko: 'Noto Serif KR', 'Nanum Myeongjo', serif;
  --font-sans: Pretendard, Inter, 'Noto Sans KR', system-ui, sans-serif;

  /* Typography — Scale */
  --text-micro: 11px;
  --text-body-sm: 14px;
  --text-body: 16px;
  --leading-body: 1.7;
  --text-subheading: 22px;
  --text-heading-sm: 28px;
  --text-heading: 44px;
  --leading-heading: 1.15;
  --text-display-ko: clamp(48px, 10vw, 110px);
  --leading-display-ko: 1.08;
  --tracking-display-ko: -0.01em;
  --text-display-latin: clamp(120px, 24vw, 300px);
  --leading-display-latin: 0.84;
  --tracking-display-latin: -0.03em;

  /* Spacing */
  --spacing-unit: 4px;
  --section-gap: 64px;
  --card-padding: 24px;
  --element-gap: 8px;

  /* Border Radius */
  --radius-links: 2px;
  --radius-cards: 9px;
  --radius-buttons: 999px;

  /* Surfaces */
  --surface-hanji-canvas: #e7e0d2;
  --surface-baekja-card: #f2ede2;
  --surface-seolbaek-base: #f7f3ea;
  --surface-meok-room: #171310;
}
```

---

## 원전 대비 의도적 이탈 목록 (Deviations)

| # | 원전 규칙 | 본 문서 | 이유 |
|---|-----------|---------|------|
| 1 | 단일 세리프, 트래킹 -3.37px | 라틴/한글 이중 규칙 | 한글은 네거티브 트래킹·압축 행간에서 뭉개짐 |
| 2 | 유화 아니면 아무것도 | 유산 원본(분위기) + 스크린샷(카드 내부) 이원 규칙 | R&D 사이트는 실증 증거 이미지가 기능 요건 |
| 3 | 완전 무채색 | 금(Geum) 단일 악센트 생존 | 현행 전통색 정체성의 최소 승계 + KPI 가독성 |
| 4 | 메뉴바 없음, 링크 1개 | 텍스트 내비 + EN 토글 유지 | 6섹션 정보 사이트의 기능 요건 |
| 5 | 본문 하한 9px | 하한 11px, 본문 14–16px | 한글 가독성·접근성 (Dammuk on Hanji 6.90:1 실측 확보) |
| 6 | Putty `#c4c3b6` | Hanji `#e7e0d2` (더 밝고 따뜻하게) | 원전 뮤트 텍스트 명암비 경계선 문제 해소 + 한지 물성 |
| 7 | 섹션 갭 80px | 64px | 11차 작업의 섹션 간격 축소 결정 유지 |
| 8 | 완전 플랫 단색 서피스 | 한지 질감 오버레이 (노이즈 2겹, 합계 ≤0.15) | 한지의 물성이 컨셉의 본질 — 재질이지 엘리베이션이 아님 (2026-08-03) |
| 9 | 세리프 워드마크 (트래킹 -3.37px) | 붓글씨 워드마크 (모필 서체 또는 SVG 레터링) | 먹·한지 컨셉에서 워드마크는 서명(署名) — 붓이 정체성 (2026-08-03) |
