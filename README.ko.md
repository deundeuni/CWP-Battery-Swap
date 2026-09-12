> **다국어 공개 안내:** 본 문서는 동일 내용의 한/영 이중 공개 문서입니다. v3.4 2026-09-13 (영문 버전: [README.md](README.md))  
> **Original Authority Notice:** 본 기술 명세의 법적·공학적 판단 최상위 기준은 한글 원본(`README.ko.md`)에 귀속되며, 영문본은 보조 참조용으로만 기능한다. (PHILOSOPHY.ko.md is authoritative original)

# CWP-Battery-Swap v3.4 - 핫스왑을 위한 차동 감속 도킹 메커니즘 및 회전형 교환 스테이지 (범용 중량물 페일세이프 도킹 플랫폼의 배터리 적용 실시예)

* **공개 일자:** 2026-09-13 (초안 2026-08-20, v0.2.1 2026-08-22, v3.0 2026-08-22, v3.1 2026-08-22, v3.2 2026-08-23, v3.3 2026-08-23, v3.4 2026-09-13)
* **작성자:** deundeuni (System Architect / Natural Person Inventor)
* **라이선스:** CERN-OHL-S v2 (하드웨어/도면) | CC BY-SA 4.0 (문서/설명)
* **공개 목적:** 방어적 공개 / 선행기술(Prior Art) 등록 - 독점 특허화 방지 및 권리 침해 위험 완화
* **검색 키워드:** EV 배터리 교환, 핫스왑, CWP, 차동 감속, 저충격 도킹, 시소 지렛대 원리, 원심력, 자전거 기어비 60T/61T 0.016rpm, 우주 도킹, ESS, 물류로봇, 드론, V홈 U홈 C홈 T홈 더브테일 핀소켓, 홈 정렬, 스왑랙, 회전형 스테이지, EPM 마그네틱 클램핑, 롤링 셀프 얼라인, Groove Alignment, Swap-Rack, Rotary Battery Swapping Stage, Low-impact docking, Differential reduction, EPM Clamping, Rolling Self-Align, 범용 중량물 도킹, Heavy Payload Docking Platform, Off-Grid Fail-Safe Coupling, 노지 중량 모듈 정밀 도킹

---

## 0. 설계자 노트 (Designer's Note)

전기차가 충전하는 동안 기다리는 시간이 너무 아까웠다. 배터리를 교체식으로 하면 시간을 아낄 수 있지 않을까? 그런데 무거운 배터리를 꽂는 순간 충격이 크면 차가 망가질 텐데, 시소처럼, 자전거 기어처럼 천천히 맞물리면 되지 않을까? 라는 생각에서 시작됨.

이 고민과 조합의 방향은 전적으로 설계자 본인(deundeuni)이 한 것이며, AI는 계산과 정리 과정에서 도구로 활용됨.

* **AI 활용 공개:** 초안 작성, 내용 정리 및 시각화 도면 작성, 기술 검토 및 문서 형식화는 범용 생성형 AI 시각화 및 텍스트 정제 도구를 활용함. 핵심 아이디어 착안, 조합 결정, 최종 판단은 모두 설계자 본인이 수행.

---

### 0.1 착안 배경 및 공공 기술 조합 (Public Domain Combination)

본 방식은 새로 만든 원천 기술이 아니며, 100년 이상 공개된 표준 기술들의 조합적 활용임.

* **시소 / 지렛대 원리** (표준 역학)
* **원심력 / 회전 안정성** (표준 물리)
* **자전거 기어비** (표준 기계요소: 60T/61T -> 0.016rpm 예시)(원리: N/(N+1) 차동, N은 모든 자연수)
* **우주 도킹 시스템** (표준 도킹 메커니즘)
* **V홈/U홈 및 더브테일/핀-소켓 정렬** (표준 기계요소: 선반 센터, 금형 가이드, 서랍 레일)

---

### 0.2 조합 예시 (일례, 한정 없음)

본 조합이 어떻게 동작할 수 있는지에 대한 이해를 돕기 위한 단순한 일례이며, 순서나 수치가 바뀌어도 본 선행기술에 속함. (본 예시의 '전기차/배터리'는 중량 모듈러 주택, 재난 대피소, 농기계 모듈, 물류 파렛트 등 500kg 이상 모든 중량물 및 이동체로 치환 가능함)

1. **접근:** 전기차(또는 중량 모듈 이송체)가 교체 스테이션에 우주 도킹처럼 정렬하여 접근
2. **하중 분산:** 시소/지렛대 원리로 배터리(또는 중량 모듈) 무게 분산 지지
3. **저속 접합 (보조 c문항):** 차동 기어비(예: 60T/61T)로 상대속도를 저속(예: 0.016rpm 수준)으로 감속시켜 충격 완화 도킹 (EV 배터리 팩, 모듈러 주택 유닛, 재난 대피소 모듈, 농기계 페이로드, 물류 파렛트 등 500kg 이상 모든 중량 모듈 공통 적용)
4. **정렬 고정:** 홈 구조로 위치를 구속하여 도킹 정밀도 확보

---

### 0.3 홈 정렬 및 스왑랙 구조 (Groove Alignment & Swap-Rack)

* **양측면 홈 방식 (Both-side groove):** 배터리/중량 모듈 양 측면 홈과 본체 대응 홈 결합으로 2축 동시 구속, 고정밀 정렬.
* **단측면 홈 방식 (One-side groove):** 한쪽만 구속하고 반대쪽은 유격(여유 공간)을 두어 1축 구속 및 조립 오차 흡수, 고속 교환.
* **스왑랙 분리형 메커니즘 (Swap-Rack / Module-Rack):** 단측면 인출(One-side out) -> 이송(Transfer) -> 양측면 삽입(Both-side in) 순서로 탈착, 충전 및 보관·점검은 스테이션 내부에서 분리 수행.
* **저충격 가압 메커니즘 (공통):** 일정 오프셋 구간(예: 약 100mm 전)부터 서서히 지그시 누르는 방식으로 충격 최소화 지향.
* **형상 및 수치 범위 비한정 선언 (핵심):** 본 문서에 기술된 모든 홈 형상(V홈, U홈, C홈, T홈, 더브테일, 핀-소켓 등 암수 결합 가이드 전반), 기어비(60T/61T 등), 속도(0.016rpm 등), 거리(100mm 등), 구동 방식(모터/공압/유압/수동/지렛대), 개수(8슬롯 등)는 이해를 돕기 위한 일례이며, 형태 변형, 수치 변경, 구동원 변경을 포함한 모든 유사 응용은 본 선행기술의 범위에 속함.

---

### 0.4 회전형 교환 스테이지 결합 예시 (Rotary Swapping Stage)

본 도킹 메커니즘은 회전형 스테이션과 결합될 수 있다.

* **구성:** 중앙 회전 허브 베어링 어셈블리, 회전 플랫폼, 양측면 레버 메커니즘(피벗/리니어 액추에이터), 양측면 도킹 홈(자동정렬 챔퍼 홈).
* **동작:** 회전(Rotation) -> 정렬(Alignment) -> 충격 완화 도킹(Docking) -> 잠금(Lock) 순서로 자동 교환.
* **비한정:** 슬롯 수, 플랫폼 형상, 회전 방향(CW/CCW), 레버 구조가 바뀌어도 동일 기술로 간주함.

---

## 1. 핵심 개념

배터리 교체 시 충격 최소화를 위한 차동 감속 도킹 구조 및 이를 활용한 회전형 교환 시스템. (범용 중량물 모듈 페일세이프 도킹 메커니즘의 대표적 실시예)

### 1.1 방어 논리 (Defensive Logic)
본 방식은 누구나 생각할 수 있는 공공 기술의 조합임을 명시하여, 특정 기업/국가의 독점 특허화를 방지하고 자유 사용을 지원하는 것을 목적으로 함. 본 문서 자체가 선행기술임.

### 1.2 적용 범위 (Application Scope)
본 구조는 배터리 스왑에 한정되지 않으며, 중량 모듈러 주택, 재난 대피소, 농기계 모듈, 물류 파렛트 등 500kg 이상 중량물의 노지 정밀 도킹에 범용으로 적용 가능하다. EV, ESS, 물류로봇, 드론, 선박, 항공우주, 건설·농업용 중장비 모듈 등 중량물 페이로드 착탈이 필요한 전 분야를 포괄한다. 공개된 산업 동향을 바탕으로 설계자가 정의한 넓은 상위 범주이며, 명시된 예시에 한정되지 않는다.

---

## 2. 도면 (Figures) - 무치수 광역 버전

[회전형 배터리 교환 스테이지 - 기술 개략도]

![fig1](https://private-user-images.githubusercontent.com/319694809/639891656-4e1d2ffb-7aef-4e30-a1d1-65091c850691.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3ODc0MDEyMTMsIm5iZiI6MTc4NzQwMDkxMywicGF0aCI6Ii8zMTk6OTQ4MDkvNjM5ODkxNjU2LTRlMWQyZmZiLTdhZWYtNGUzMC1hMWQxLTY1MDkxYzg1MDY5MS5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotRGF0ZT0yMDI2MDgyMlQxMjE1MTNaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT1lNDRjNGYwMzgzZmE0ZGJlZDBlZDI4ODAxYzZkZDAwNzVjMWZkMGU5ZGI3YmU0NTkyMTM1ZmNjMmY0YTdkYzFmJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCZyZXNwb25zZS1jb250ZW50LXR5cGU9aW1hZ2UlMkZwbmcifQ.biSpUMSEH0Kr6RbZR05__584EpbRhMPORUqlXqvXJWo)

* **도면 비고:** 본 도면의 모든 치수, 각도, 수량은 예시이며 범위를 한정하지 않음. 기능적 구조(회전, 홈 정렬, 레버 잠금)만이 본 공개의 핵심임.

**주의 (AI 시각화 면책 조항):** 본 도면의 메커니즘 개념은 설계자(deundeuni)가 독자적으로 고안했습니다. 첨부된 이미지는 이해를 돕기 위해 범용 AI 시각화 도구를 활용하여 생성된 개념적 시각화 예시일 뿐이며, 기존의 특정 상용 제품이나 타인의 등록 특허 도면을 복제한 것이 아닙니다.

---

## 3. 한계, 보증 부인 및 면책

본 문서는 방어적 공개를 위한 기술적 개념 개시이며, 어떠한 보증도 없이 있는 그대로(AS-IS) 제공됩니다.

1. **보증 부인:** 특정 목적 적합성, 상품성, 안전성, 제품화를 보증하지 않습니다.
2. **책임 제한:** 본 문서의 사용, 구현, 응용으로 인한 직접·간접 손해, 사고, 손실에 대해 작성자(deundeuni)는 어떠한 법적 책임도 지지 않습니다.
3. **제3자 권리 비보증:** 본 문서가 제3자의 특허, 상표, 저작권 등 권리를 침해하지 않음을 보증하지 않으며, 권리 조사는 구현자의 책임입니다.
4. **법규·안전·인증 책임:** 각 국가의 법규, 전기·소방·안전 기준, 인증 획득 및 안전 검증 책임은 전적으로 구현자에게 있습니다.

---

## 3.5 시스템 연계 (System Integration) - CWP 3대 하드웨어 연계 및 생존 아키텍처

본 차동 감속 도킹 메커니즘은 CWP 하드웨어 3대 메커니즘 및 상위 생존 아키텍처와 유기적으로 결합되어 무중단 생존 지향형 교환 스테이션으로 동작할 수 있다.

* **기구적 셀프 얼라인 정렬 (`CWP-Rolling-Self-Align-Battery-Swap-System`):** V-홈 및 캐스터 수동/자율 정렬 메커니즘(A/B/C/S 타입)과 결합하여 진입 시 치수 오차(예: ±5mm 이상)를 물리적으로 흡수하고 정밀 도킹 구역으로 유도함.
* **차동 감속 저충격 도킹 (`CWP-Battery-Swap` - 본 기술):** N/(N+1) 차동 기어비(예: 60T/61T) 및 회전형 스테이지를 통해 접합 상대속도를 극저속(예: 0.016rpm 수준)으로 감속시켜 완충 도킹을 수행함.
* **전자기 클램핑 및 안전 체결 (`CWP-Clamping-Battery-Swap-System`):** 범용 EPM(Electro-Permanent Magnet) 마그네틱 클램핑 모듈, 이중 핀 고정 및 3중 쿠션 구조와 결합하여 정밀 도킹 후 무전력 영구자석 고정 및 비상시 안전 해제를 지향함. (배터리 팩 및 500kg 이상 범용 중량 모듈 페일세이프 고정 적용)
* **물리적 비상 이탈 (`0.1ms HW Intercept` / `LAST-LIGHT` 연계):** 화재·정전 등 비상 상황 발생 시 0.1ms 억제 신호에 의해 차동 클러치 및 EPM 클램프가 Release되어 수동 및 무전력 이탈이 가능함.
* **연산적 제어 생존 (`chiplet-apu-multi-system-survival-architecture`):** 분산 관제(CCS) 및 칩렛 다중 제어 아키텍처와 연계하여 관제 칩렛 하나가 고장나더라도 배터리 교환 제어 로직이 지속 동작하도록 구성함.

---

## 4. 공개 증명 (Prior Art Proof & Timestamp)

* **Git Commit SHA:** GitHub 저장소의 불변 커밋 해시(Commit Hash) 및 커밋 이력이 최초 공개 시점(2026-08-20)을 법적으로 입증함.
* **Canonical Gateway:** `somamoa.ai.kr` 최상위 거점 관문을 통한 무결성 레저 결합.
* **Prior Art Status:** 본 명세서는 깃허브 공개 커밋 시점을 기준으로 소방·안전·전기차 산업 표준 상의 독점 특허화를 방어하는 선행기술(Prior Art) 자격을 가짐.

---

## 5. 버전 이력

* **v0.1 (2026-08-20):** 초안
* **v0.2.1 (2026-08-22):** 차동 감속 도킹 개념 공개
* **v3.0 (2026-08-22):** 회전형 스테이지 결합, 무치수 도면 추가, 비한정 선언 강화
* **v3.1 (2026-08-22):** AI 시각화 면책 조항 명시 및 도면 업데이트
* **v3.1.1 (2026-08-23):** AI 도구 활용 내역 범용 명칭으로 정제 및 면책 조항 보강
* **v3.2 (2026-08-23):** 면책 조항 정교화(보증 부인, 책임 제한, 제3자 권리 비보증, 법규·안전 책임 전가 4대 조항), 라이선스 중복 표기 제거, 버전 표기 일치화
* **v3.3 (2026-08-23):** CWP 3대 핵심 하드웨어 메커니즘(CWP-Rolling-Self-Align, CWP-Battery-Swap, CWP-Clamping) 상호 연계 체계 명시 및 출처 정보 통합
* **v3.4 (2026-09-13):** 범용 중량물 페일세이프 도킹 플랫폼으로의 상위개념 적용 범위 명시 확장 (모듈러 주택, 재난 대피소, 농기계 모듈, 물류 파렛트 등 500kg 이상 노지 중량물 정밀 도킹 분야 포괄), 0.2항 조합 예시 보조 c문항(저속 접합) 및 3.5항 연계 c문항(EPM 클램핑) 치환 가능성 명시 보강, 부제 및 검색 키워드 확장, 특정 AI 기업·모델명 배제 및 범용 명칭(도구)으로의 익명화 정제 적용

---

## 6. 라이선스

* **라이선스:** CERN-OHL-S v2 (하드웨어/도면), CC BY-SA 4.0 (문서/도면) - 상업적 이용 가능, 단 개작시 동일 라이선스로 공개해야 함
* **구버전(v3.1 이하):** CC BY 4.0으로 영구 공개됨
* **상업적 이용 안내:** 상업적 제조/판매 모두 가능함. CWP 부분을 개선한 도면만 같은 라이선스로 공개하면 되며, 귀사의 다른 비밀 설계까지 공개할 필요는 없음.

---

## 7. 실리보호 (Practical Protection)

* **원안 우선 원칙:** 본 명세서의 법적·기술적 해석은 한국어 원본(`README.ko.md`)을 최우선 기준으로 적용하며, 영문본 및 기타 언어 번역본은 참고용으로만 기능한다.
* **범위 포괄성:** 본 문서에 기술된 기어비, 감속 수치, 홈 구조, 구동 방식, 슬롯 개수 등은 광범위한 선행기술 선점을 위한 예시로서 상위개념으로 포괄 적용된다.
* **사업화 내용 분리:** 본 백서 원안에는 Pure Open Source 및 선행기술 개시 내용만을 포함하며, 독자적인 수익 모델 및 사업화 세부 실행안은 별도 기술 문서로 분리 관리한다.

---

## 8. 출처 및 기록 (Sources & Records)

* **소마모아 생태계 저장소 및 학술 식별자 (Ecosystem Repositories & DOIs)**
  * 상위 범용 생존 아키텍처 & APU 연산 제어기 (`chiplet-apu-multi-system-survival-architecture`) — GitHub: `deundeuni / chiplet-apu-multi-system-survival-architecture` | CERN Zenodo DOI: `10.5281/zenodo.22374987` (https://doi.org/10.5281/zenodo.22374987)
  * 재난 피난 유도 & 보조 인프라 (`LAST-LIGHT`) — GitHub: `deundeuni / LAST-LIGHT` | CERN Zenodo DOI: `10.5281/zenodo.22373189` (https://doi.org/10.5281/zenodo.22373189)
  * 극지 해양 희생장갑 (`MAX-LIFE-ICE-BELT`) — GitHub: `deundeuni / MAX-LIFE-ICE-BELT` | CERN Zenodo DOI: `10.5281/zenodo.22373686` (https://doi.org/10.5281/zenodo.22373686)
  * CWP 배터리 교환 도킹 (`CWP-Battery-Swap`) — CERN Zenodo DOI: `10.5281/zenodo.22373538` (https://doi.org/10.5281/zenodo.22373538)
  * CWP 전자기 클램핑 (`CWP-Clamping-Battery-Swap-System`) — CERN Zenodo DOI: `10.5281/zenodo.22373722` (https://doi.org/10.5281/zenodo.22373722)
  * CWP 롤링 셀프얼라인 (`CWP-Rolling-Self-Align-Battery-Swap-System`) — CERN Zenodo DOI: `10.5281/zenodo.22373704` (https://doi.org/10.5281/zenodo.22373704)
  * 최상위 거점 관문 및 메인 저장소 (`soma-moa`) — GitHub: `deundeuni / soma-moa` | 관문 도메인: `somamoa.ai.kr`

* **국제 기술 표준 및 참조 규격 (International Technical Standards)**
  * ISO 7010 / ISO 16069 — Graphical symbols, Safety colours and Safety Way Guidance Systems (SWGS)
  * Bluetooth SIG Specification — Auracast / LE Audio Broadcast Specifications
  * IEEE 802.15.4z / UWB Standard — Ultra-Wideband Positioning and Ranging Standards
  * ISO 8501 — Surface Cleanliness and Preparation Standards for Steel Substrates
  * IMO AFS Convention & EU MSFD — International Convention on the Control of Harmful Anti-fouling Systems & Marine Strategy Framework Directive
  * Classification Society Ice Class Rules — 한국선급(KR), DNV, ABS 극지 운항 아이스벨트 구조 규격

* **공지기술 원용 및 학술적 배경 (Public Domain Prior Art & Physics)**
  * Béla Barényi (1951) — Automotive Passive Safety Architecture (Crumple Zone & Sacrificial Structural Sacrifice)
  * Public Domain Kinematics & Clamping — N/(N+1) Differential Reduction, Electro-Permanent Magnet (EPM) Control Logic

* **법적 근거 및 선사용권 규정 (Legal Statutes & Precedents)**
  * 대한민국 특허법 제103조 — 선사용에 의한 통상실시권
  * 미국 특허법 35 U.S.C. §273 — Defense to Infringement Based on Prior Commercial Use
  * 대한민국 「소방시설 설치 및 관리에 관한 법률」 및 「건축법」 — 법정 유도 설비 및 비상 전력 기준

* **선행기술 증명 고지 (Defensive Prior Art Statement):** 본 명세서에 개시된 기술적 사상, 도안 및 참조 표준 연계 구조는 GitHub 불변 커밋 해시(Commit Hash) 및 CERN Zenodo / DataCite 글로벌 학술 레지스트리에 타임스탬프 기록이 등재되어 있습니다. 이는 제3자의 사적 독점 특허화 위험을 완화하고, 전 세계 특허 심사 시 공공 영역의 선행기술(Prior Art)로 참조되어 신규성 및 진보성 논박 근거로 활용 가능하도록 돕는 것을 지향합니다.

* **비의도적 생략 및 예시적 미한정 고지 (Non-Intentional Omission & Non-Exhaustive Disclaimer):** 본 명세서에 인용되거나 열거된 기술 표준, 공지 원리, 법령 및 관련 저장소 목록은 이해를 돕기 위한 예시적 서술이며 전면적·고착적 한정을 의미하지 않습니다. 작성자의 주관적 한계나 인지적 착오로 인해 특정 세부 규격, 관련 산업 표준, 후속 개정안 또는 균등 선행기술의 명시가 누락되거나 누적 생략되었을 수 있으나, 이는 의도적인 은폐나 배척이 아닙니다. 개시된 상위 기술 사상과 연결되는 모든 파생 표준, 개정 규격, 균등 기구 및 공지기술 조합은 본 방어적 공개 백서의 선행기술 포괄 범주에 포함된 것으로 간주합니다.

