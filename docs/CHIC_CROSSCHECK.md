# CHIC 서술 대조 결과 — 수정·교체 후보 목록

> 작성일: 2026-08-05
> 대조 기준: `~/Documents/chic-site/` (CHIC 최종 성과보고서 2023-02-22 기반으로 재구축된 공식 사이트 데이터)
> 대조 대상: 본 저장소 [[data|assets/data.js]]의 CHIC 관련 서술 전체
> 성격: **후보 목록** — 확정·반영은 사용자 판단. 임의 수정하지 않았다.

CHIC 사이트의 데이터는 최종 성과보고서 원문에서 추출된 1차 자료이고, 본 사이트의 CHIC 서술은
2026-07-07 보고서 PDF 분석에서 파생된 2차 요약이다. 아래는 두 층위가 어긋나는 지점이다.

---

## A. 수치·사실 정정 후보

| # | 위치 | 현재 서술 | CHIC 사이트 근거 | 판정 |
|---|------|-----------|------------------|------|
| A-1 | journey.chic.partners | 문체부 장관표창(**2022**) | `outcomes.yaml` a-2021-mcst — 수상일 **2021-01-05** | **오류 확실** |
| A-2 | journey.chic.highlights | 사업화 **23건** | `applications.yaml` — 보고서 원표 23행이나 익산 미륵사지 석등·대구 컨퍼런스 플랫폼이 중복 기재. 고유 사례 **21건** | **정정 권장** |
| A-3 | journey.chic.highlights | 전통문화 특화 **언어모델 NER F1 89.0%** — COLING 2022 발표 | COLING 2022 논문은 `KOCHET: a Korean Cultural Heritage corpus for Entity-related Tasks` (김경민 외) — **코퍼스** 논문이며 F1 89.0 수치는 CHIC 사이트 어디에도 없음 | **재서술 필요** |
| A-4 | kpis[0] · highlights · achievements | 문화유산 애셋 **31,022개** 구축 — 목표(2,600개)의 12배 | CHIC 사이트에 이 수치 없음. 애셋 관련 실측은 **177점 취득 → 129점 애셋화**, 아카이브 **8,353장** 디지털화 | **최우선 확인** (히어로 최상단 KPI) |
| A-5 | journey.chic.period | 2020 – 2022 | 2020.**07** — 2022.**12** (문화체육관광부 문화기술 연구개발 지정과제) | 정밀화 가능 |
| A-6 | journey.chic.funder | 문화체육관광부 · **한국콘텐츠진흥원** | CHIC 사이트 공식 표기는 "문화체육관광부 문화기술 연구개발 지정과제" — KOCCA 병기 없음 | 근거 확인 |
| A-7 | journey.chic.partners | 국립중앙박물관 · 국립무형유산원 실증 | `consortium.yaml` — **7개 기관**: ETRI(주관), 문화유산기술연구소(TRIC), SQI소프트, 한국전통문화대학교, 디캐릭 + 협력 국립중앙박물관·국립무형유산원 | 보강 가능 |
| A-8 | projects.chic-legacy.desc | 제페토·다중접속 VR로 **5개 국립박물관** 공간 재현 | CHIC 결과물 39건 목록에 제페토·5개 박물관 서술 없음. 관련 항목은 "AR/VR 박물관 시범 서비스 — 시범 콘텐츠 **7종**" | 출처 확인 |

**A-4 보충**: 31,022은 본 사이트 히어로의 첫 번째 카운트업 수치이자 성과 대시보드 항목이다
(한/영 각 3곳, 총 6곳). CHIC 사이트가 참조한 최종 성과보고서 절과 본 사이트가 참조한 절이
다를 가능성이 있으므로(예: 파생·변형 애셋 누적 집계 vs 표준 애셋화 실적), 어느 쪽이 공개
표기에 적합한지 판단이 필요하다.

---

## B. 이미지 교체 후보

CHIC 사이트는 실증 결과 이미지 39점(`public/images/results/`)과 실사 사진 5점
(`public/images/photos/`)을 보유한다. 본 사이트의 CHIC 관련 이미지보다 원본에 가깝다.

| # | 현재 | 문제 | 교체 후보 |
|---|------|------|-----------|
| B-1 | `case-metaverse.webp` (CHIC 실증 유산 카드) | **Unity 에디터 화면 그대로** — 상단 툴바, Statistics 오버레이(FPS·CPU·Batches)가 노출된 개발 중 스크린샷 | `photos/exhibition.webp` — 메타버스 박물관 6개 공간을 정리한 완성 화면 |
| B-2 | (없음) | CHIC 대표 키비주얼 부재 | `photos/coexistence-key.webp` — '공존과 지속 / 사유' 반가사유상 키비주얼(정사각, 후광 연출). 새 스타일의 원형 크롭에 적합 |
| B-3 | (없음) | 풀블리드 유산 이미지 부재 | `photos/media-wall.webp` — 인천국제공항 한국문화거리 반가사유상 미디어월 **실사 사진**. [[STYLE_REF_MeokHanji]]의 Heritage Panel(유산 원본 전담) 자리에 최적 |
| B-4 | `field-*.webp` (핵심기술 3분야) | — | `results/3d-scan-detail.webp` (초정밀 스캔 표면), `results/robot-arm-capture.webp` (로봇팔 자동획득) 등 실제 산출물 |
| B-5 | 실증 카드 내부 | — | `results/nl-search.webp` (큐레이터 플랫폼 자연어 검색 실화면, 국립중앙박물관 로고 포함), `results/curation-platform.webp` (시스템 구성도) — 새 스타일의 Functional Image Card 규칙에 부합 |

---

## C. 신규 추가 가능한 검증 수치

`_migration/content-inventory.md`의 연차별 결과물 39건에서 확인된, 본 사이트에 아직 없는 실측값:

- 데이터 속성 **92종** · 관계 **14종** (국립중앙박물관 e-museum 태깅)
- 표준 물리기반 렌더링(PBR) 템플릿 **30종**
- 4× 초해상화 성능 **PSNR 27.421 · SSIM 0.7978**
- 아카이브 디지털화 **8,353장**, 애셋 표준 생성 **177점 취득 → 129점 애셋화**
- AR/VR 박물관 시범 콘텐츠 **7종**, 홀로렌즈2 기반 MR 해설 콘텐츠
- 로봇팔 자동획득장치 — 촬영자 숙련도 편차 해소 목적의 최초 개발 시도
- 국립중앙박물관–ETRI MOU 체결 **2020.10.21**
- 텍스트 데이터 속성 18종 · 이미지 데이터 속성 26종

---

## D. 역방향 지적 — CHIC 사이트 쪽 확인 요망

대조 과정에서 발견한, **CHIC 사이트에 게시 중인 이미지의 문제**다. 본 사이트가 아니라
`chic-site` 저장소의 사안이므로 별도 처리가 필요하다.

1. **`results/knowledge-graph.webp` — 개인 북마크 노출**
   브라우저 창을 통째로 캡처한 이미지로, 북마크바에 내부 자산명이 그대로 읽힌다:
   `CHCS_SQI`, `웹 조각 갤러리`, `HEEKWON_NAS`, `CHIC-Data - Synolo…`, `ARCSP - Synology…`,
   `OnAR - Synology Di…`, `NewstormNas - Syn…`. 공개 사이트 게시물로는 부적절하다.

2. **같은 이미지의 출처 문제**
   해당 화면은 CHIC 산출물이 아니라 **영국박물관 'Museum of the World'**(Google Cultural
   Institute) 페이지다. 하단에 British Museum·Google Cultural Institute 로고가 찍혀 있다.
   벤치마크 참고 화면을 성과 이미지 위치에 쓰고 있다면 캡션 명시 또는 교체가 필요하다.

3. **`results/nl-search.webp` — 경미**
   주소창에 내부 S3 엔드포인트(`chcs-curator-frontend-2022.s3-website.ap-northeast-2…`)와
   우상단 사용자 프로필 사진이 함께 노출된다. 크롭 권장.

---

## 처리 현황 (2026-08-05 갱신)

| 항목 | 상태 | 비고 |
|------|------|------|
| A-1 장관표창 연도 | ✅ 반영 | 2022 → **2021**. 한/영 journey.partners + achievements.awards 총 4곳 |
| A-2 사업화 건수 | ✅ 반영 | 23건 → **21건**. 한/영 journey.highlights + achievements.business 4곳. 파생 정정: achievementSummary 집계 `24+` → **`22+`** (사업화 21 + 기술이전 1) |
| A-4 애셋 31,022개 | ✅ **현행 유지 확정** | 사용자 확인(2026-08-05) — 현재 표기가 맞음. 재검토 불요 |
| B-1 메타버스 카드 이미지 | ✅ 교체 | Unity 에디터 캡처 → CHIC `photos/exhibition.webp`. 16:9 레터박스 가공(원본 배경색 #eee)으로 6개 공간 무손실 수록 |
| B-2 사유 키비주얼 | ✅ 반영 | `assets/img/heritage-sayu.webp` — CHIC 여정 패널 원형 비네트(116px). 후광·얼굴 중심 크롭 |
| B-3 미디어월 실사 | ✅ 반영 | `assets/img/heritage-mediawall.webp` — 실증사례↔연구성과 사이 풀블리드 Heritage Panel 신설 |
| A-3 COLING 서술 | ⬜ 미착수 | 대체 문안 필요 |
| A-5~A-8 | ⬜ 미착수 | 기간 정밀화·funder·참여기관·제페토 출처 |
| C 신규 수치 | ⬜ 미착수 | |
| D CHIC 사이트 이미지 | ⬜ 미착수 | `chic-site` 저장소 작업으로 분리 |

### 함께 반영된 문안 방침 (2026-08-05 사용자 지시)

**미달성 정량 목표는 표기하지 않고, 사진으로 보여줄 수 있는 서술로 쓴다.** ULSOO 여정 카드에 적용:

| 이전 | 이후 |
|------|------|
| 10억 픽셀급 기가스캔 + 0.5µm급 미세 균열 자동 탐지 **(개발 목표)** | 훼손된 표면을 10억 픽셀로 훑어, 육안으로 놓치는 균열의 결까지 그대로 남깁니다 |
| 생성형 AI 결손 복원 — 복원 정확도 **SSIM 95% 목표** | UV·적외선·X선 형광으로 안료 아래 가려진 밑그림과 덧칠의 흔적을 읽어냅니다 |
| Linked Art·CRMsci·CRMdig 기반 복원 전주기 이력 관리 표준화 | 생성형 AI가 결손부를 되살리고, 그 근거와 과정을 국제 표준(Linked Art·CIDOC CRM) 기록으로 남깁니다 |

사실 요소(10억 픽셀, UV·IR·XRF, 생성형 AI, Linked Art·CIDOC CRM)는 모두 보존하고, 미달성
목표 수치(0.5µm, SSIM 95%)와 '(개발 목표)' 표기만 제거했다. 히어로 KPI 4종은 사이트 핵심
지표이므로 그대로 유지.
