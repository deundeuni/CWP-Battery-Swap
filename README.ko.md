> **다국어 공개 안내:** 본 문서는 동일 내용의 한/영 이중 공개 문서입니다. v3.4 2026-09-13 (영문 버전: [README_EN.md](README_EN.md))  
> **Original Authority Notice:** 본 기술 명세의 법적·공학적 판단 최상위 기준은 한글 원본(`README.ko.md`)에 귀속되며, 영문본은 보조 참조용으로만 기능한다. (PHILOSOPHY.ko.md is authoritative original)

# CWP-Battery-Swap v3.4 - 핫스왑을 위한 차동 감속 도킹 메커니즘 및 회전형 교환 스테이지 (범용 중량물 페일세이프 도킹 플랫폼의 배터리 적용 실시예)

* **공개 일자:** 2026-09-13 (초안 2026-08-20, v0.2.1 2026-08-22, v3.0 2026-08-22, v3.1 2026-08-22, v3.2 2026-08-23, v3.3 2026-08-23, v3.4 2026-09-13)
* **작성자:** deundeuni (System Architect / Natural Person Inventor)
* **라이선스:** CERN-OHL-S v2 (하드웨어/도면) | CC BY-SA 4.0 (문서/설명)
* **공개 목적:** 방어적 공개 / 선행기술(Prior Art) 등록 - 독점 특허화 방지 및 권리 침해 위험 완화
* **검색 키워드:** EV 배터리 교환, 핫스왑, CWP, 차동 감속, 저충격 도킹, 시소 지렛대 원리, 원심력, 자전거 기어비 60T/61T 0.016rpm, 우주 도킹, ESS, 물류로봇, 드론, V홈 U홈 C홈 T홈 더브테일 핀소켓, 홈 정렬, 스왑랙, 회전형 스테이지, EPM 마그네틱 클램핑, 롤링 셀프 얼라인, Groove Alignment, Swap-Rack, Rotary Battery Swapping Stage, Low-impact docking, Differential reduction, EPM Clamping, Rolling Self-Align, 범용 중량물 도킹, Heavy Payload Docking Platform, Off-Grid Fail-Safe Coupling, 노지 중량 모듈 정밀 도킹

---

## 0. 설계자 독자 아키텍처 및 선행기술 공개 선언 (Designer's Philosophical Declaration)

전기차가 충전하는 동안 기다리는 시간이 너무 아까웠다. 배터리를 교체식으로 하면 시간을 아낄 수 있지 않을까? 그런데 무거운 배터리를 꽂는 순간 충격이 크면 차가 망가질 텐데, 시소처럼, 자전거 기어처럼 천천히 맞물리면 되지 않을까? 라는 생각에서 시작됨.

본 고민과 기술 조합의 방향성은 전적으로 설계자 자연인(deundeuni)이 한 것이며, 공지된 차동 감속 및 회전형 도킹 메커니즘을 응용하여 범용 중량물 도킹 아키텍처를 정의하였다. 본 시스템은 선행 연구자 및 특허권자들의 공학적 성과를 존중하며, 공지 원리를 구체적 실시예 파라미터 조합으로 응용 개시함을 명시한다.

### 0.1 착안 배경 및 공공 기술 조합 (Public Domain Combination)

본 방식은 새로 만든 원천 기술이 아니며, 100년 이상 공개된 표준 기술들의 조합적 활용임.

* **시소 / 지렛대 원리** (표준 역학)
* **원심력 / 회전 안정성** (표준 물리)
* **자전거 기어비** (표준 기계요소: 60T/61T -> 0.016rpm 예시)(원리: N/(N+1) 차동, N은 모든 자연수)
* **우주 도킹 시스템** (표준 도킹 메커니즘)
* **V홈/U홈 및 더브테일/핀-소켓 정렬** (표준 기계요소: 선반 센터, 금형 가이드, 서랍 레일)

### 0.2 조합 예시 (일례, 한정 없음)

본 조합이 어떻게 동작할 수 있는지에 대한 이해를 돕기 위한 단순한 일례이며, 순서나 수치가 바뀌어도 본 선행기술에 속함. (본 예시의 '전기차/배터리'는 중량 모듈러 주택, 재난 대피소, 농기계 모듈, 물류 파렛트 등 500kg 이상 모든 중량물 및 이동체로 치환 가능함)

1. **접근:** 전기차(또는 중량 모듈 이송체)가 교체 스테이션에 우주 도킹처럼 정렬하여 접근
2. **하중 분산:** 시소/지렛대 원리로 배터리(또는 중량 모듈) 무게 분산 지지
3. **저속 접합 (보조 c문항):** 차동 기어비(예: 60T/61T)로 상대속도를 저속(예: 0.016rpm 수준)으로 감속시켜 충격 완화 도킹 (EV 배터리 팩, 모듈러 주택 유닛, 재난 대피소 모듈, 농기계 페이로드, 물류 파렛트 등 500kg 이상 모든 중량 모듈 공통 적용)
4. **정렬 고정:** 홈 구조로 위치를 구속하여 도킹 정밀도 확보

### 0.3 홈 정렬 및 스왑랙 구조 (Groove Alignment & Swap-Rack)

* **양측면 홈 방식 (Both-side groove):** 배터리/중량 모듈 양 측면 홈과 본체 대응 홈 결합으로 2축 동시 구속, 고정밀 정렬.
* **단측면 홈 방식 (One-side groove):** 한쪽만 구속하고 반대쪽은 유격(여유 공간)을 두어 1축 구속 및 조립 오차 흡수, 고속 교환.
* **스왑랙 분리형 메커니즘 (Swap-Rack / Module-Rack):** 단측면 인출(One-side out) -> 이송(Transfer) -> 양측면 삽입(Both-side in) 순서로 탈착, 충전 및 보관·점검은 스테이션 내부에서 분리 수행.
* **저충격 가압 메커니즘 (공통):** 일정 오프셋 구간(예: 약 100mm 전)부터 서서히 지그시 누르는 방식으로 충격 최소화 지향.
* **형상 및 수치 범위 비한정 선언 (핵심):** 본 문서에 기술된 모든 홈 형상(V홈, U홈, C홈, T홈, 더브테일, 핀-소켓 등 암수 결합 가이드 전반), 기어비(60T/61T 등), 속도(0.016rpm 등), 거리(100mm 등), 구동 방식(모터/공압/유압/수동/지렛대), 개수(8슬롯 등)는 이해를 돕기 위한 일례이며, 형태 변형, 수치 변경, 구동원 변경을 포함한 모든 유사 응용은 본 선행기술의 범위에 속함.

### 0.4 회전형 교환 스테이지 결합 예시 (Rotary Swapping Stage)

본 도킹 메커니즘은 회전형 스테이션과 결합될 수 있다.

* **구성:** 중앙 회전 허브 베어링 어셈블리, 회전 플랫폼, 양측면 레버 메커니즘(피벗/리니어 액추에이터), 양측면 도킹 홈(자동정렬 챔퍼 홈).
* **동작:** 회전(Rotation) -> 정렬(Alignment) -> 충격 완화 도킹(Docking) -> 잠금(Lock) 순서로 자동 교환.
* **비한정:** 슬롯 수, 플랫폼 형상, 회전 방향(CW/CCW), 레버 구조가 바뀌어도 동일 기술로 간주함.

### 0.5 소프트웨어 유틸리티 활용에 관한 명시 (Software Utility Limitation)

본 문서 작성 과정에서 활용된 소프트웨어 및 AI 도구는 설계자가 이미 정의한 기술 조합, 설계 방향, 수치 파라미터를 바탕으로 단순 포맷팅, 문맥 정제, 개념 시각화 출력을 실행한 **수동적 실행 유틸리티(Passive Execution Utility)**에 국한된다. 본 인프라의 모든 설계 의도, 구조적 결합권, 선행기술 공개 권한은 전적으로 설계자 자연인에게 귀속된다.

---

## 1. 핵심 개념 및 적용 범위

배터리 교체 시 충격 최소화를 위한 차동 감속 도킹 구조 및 이를 활용한 회전형 교환 시스템. (범용 중량물 모듈 페일세이프 도킹 메커니즘의 대표적 실시예)

### 1.1 방어 논리 (Defensive Logic)
본 방식은 누구나 생각할 수 있는 공공 기술의 조합임을 명시하여, 특정 기업/국가의 독점 특허화를 방지하고 자유 사용을 지원하는 것을 목적으로 함. 본 문서 자체가 선행기술임.

### 1.2 적용 범위 (Application Scope)
본 구조는 배터리 스왑에 한정되지 않으며, 중량 모듈러 주택, 재난 대피소, 농기계 모듈, 물류 파렛트 등 500kg 이상 중량물의 노지 정밀 도킹에 범용으로 적용 가능하다. EV, ESS, 물류로봇, 드론, 선박, 항공우주, 건설·농업용 중장비 모듈 등 중량물 페이로드 착탈이 필요한 전 분야를 포괄한다. 공개된 산업 동향을 바탕으로 설계자가 정의한 넓은 상위 범주이며, 명시된 예시에 한정되지 않는다.

---

## 2. 도면 (Figures) - 무치수 광역 버전

[회전형 배터리 교환 스테이지 - 기술 개략도]

<img width="1920" height="1280" alt="Fig1_KR_no-dimension" src="https://github.com/user-attachments/assets/0d7b61b0-0b9a-47a0-ab1f-b0a819377305" />

* **도면 비고:** 본 도면의 모든 치수, 각도, 수량은 예시이며 범위를 한정하지 않음. 기능적 구조(회전, 홈 정렬, 레버 잠금)만이 본 공개의 핵심임.

**주의 (AI 시각화 면책 조항):** 본 도면의 메커니즘 개념은 설계자(deundeuni)가 독자적으로 고안했습니다. 첨부된 이미지는 이해를 돕기 위해 범용 AI 시각화 도구를 활용하여 생성된 개념적 시각화 예시일 뿐이며, 기존의 특정 상용 제품이나 타인의 등록 특허 도면을 복제한 것이 아닙니다.

---

## 3. 한계, 보증 부인 및 면책 (Limitation, Disclaimer of Warranties & Liability)

본 문서는 선행기술 개시 및 방어적 공개를 목적으로 작성되었으며, 어떠한 보증도 없이 '있는 그대로(AS-IS)' 제공된다.

1. **보증 부인 (Disclaimer of Warranties):** 특정 목적 적합성, 상품성, 무결성, 제품화 가능성 및 제3자 특허 비침해를 보증하지 않는다.
2. **책임 제한 (Limitation of Liability):** 본 문서의 기술 개시 내용의 활용, 구현, 직접·간접 응용으로 인해 발생 가능한 직접 손해, 간접 손해, 징벌적 손해, 사고 또는 사업적 손실에 대해 작성자(deundeuni)는 법적 책임을 지지 아니한다.
3. **고의성 부인 및 방어적 공개 선언 (Non-willful Infringement Notice):** 본 공개는 미국 특허법상 고의 침해(Willful Infringement / 35 U.S.C. §284 및 관련 판례 법리) 주장에 대한 방어적 거점을 형성하고, 공공 영역(Public Domain)에 선행기술을 명시하여 제3자의 독점적 특허 출원을 방지하기 위한 방어적 개시 조치이며, 타인의 권리를 고의로 침해하려는 의도가 없음을 명시한다.
4. **법규·안전·인증 책임:** 각 국가별 법규, 전기·소방·소음·진동 안전 기준 준수, 인증 획득 및 현장 안전 검증 책무는 전적으로 구현자 및 사업화 주체에게 귀속된다.

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

## 6. 라이선스 및 상업적 이용 안내 (Licensing)

> CERN Open Hardware Licence Version 2 - Strongly Reciprocal (CERN-OHL-S v2)  
> Copyright (c) 2026 deundeuni  
>  
> This hardware design is licensed under CERN-OHL-S v2.  
> You may manufacture and distribute it, even commercially,  
> but if you distribute products based on it, you must also  
> make the modified design files available under the same license.  
>  
> Full text: https://ohwr.org/cern_ohl_s_v2.pdf  
>  
> Documentation and figures: CC BY-SA 4.0  
> https://creativecommons.org/licenses/by-sa/4.0/  

* **상업적 이용 안내:** 상업적 제조/판매 모두 가능함. CWP 부분을 개선한 도면만 같은 라이선스로 공개하면 되며, 귀사의 다른 비밀 설계까지 공개할 필요는 없음.

---

## 7. 실리보호 (Practical Protection)

* **원안 우선 원칙:** 본 명세서의 법적·기술적 해석은 한국어 원본(`README.ko.md`)을 최우선 기준으로 적용하며, 영문본 및 기타 언어 번역본은 참고용으로만 기능한다.
* **범위 포괄성:** 본 문서에 기술된 기어비, 감속 수치, 홈 구조, 구동 방식, 슬롯 개수 등은 광범위한 선행기술 선점을 위한 예시로서 상위개념으로 포괄 적용된다.
* **비의도적 생략 및 예시적 미한정 고지 (Non-Intentional Omission & Non-Exhaustive Disclaimer):** 본 명세서에 인용되거나 열거된 기술 표준, 공지 원리, 법령 및 관련 규격은 이해를 돕기 위한 예시적 서술이며 전면적·고착적 한정을 의미하지 않습니다. 작성자의 주관적 한계나 인지적 착오로 인해 특정 세부 규격, 관련 산업 표준, 후속 개정안 또는 균등 선행기술의 명시가 누락되거나 누적 생략되었을 수 있으나, 이는 의도적인 은폐나 배척이 아닙니다. 개시된 상위 기술 사상과 연결되는 모든 파생 표준, 개정 규격, 균등 기구 및 공지기술 조합은 본 방어적 공개 백서의 선행기술 포괄 범주에 포함된 것으로 간주합니다.
* **방어적 공표 및 선사용권 병행:** 본 백서는 방어적 선행기술(Prior Art) 공표를 1차 목적으로 하며, 대한민국 특허법 제103조 및 미국 특허법 35 U.S.C. §273에 따른 선사용권 확립을 위해 독자적인 설계도·시제품·개발 기록을 오프라인으로 병행 관리한다.
* **사업화 내용 분리:** 본 백서 원안에는 Pure Open Source 및 선행기술 개시 내용만을 포함하며, 독자적인 수익 모델 및 사업화 세부 실행안은 별도 기술 문서로 분리 관리한다.

---

## 8. 출처 및 기록 (Sources & Records)

* **차동 감속 및 배터리 교환 도킹 공지기술 원리 (Foundational Docking & Swap Prior Art)**
  * Public Domain Kinematics & Gear Reduction — N/(N+1) 차동 기어 감속, 지렛대 완충 및 구체/챔퍼 홈 자동 정렬 공지 원리
  * US Patent US4450400A — Battery replacement system for electric vehicles (롤러 이송 및 승강 이동에 의한 차동 배터리 교환 시스템)
  * US Patent US8164300B2 — Battery exchange station (Better Place, 하부 도킹 및 차동 승강 교환 스테이션)
  * European Patent EP3705359A1 — Battery swapping actuating mechanism (차동 도킹, 가이드 핀/소켓 및 승강 제어 메커니즘)
  * US Patent CN112721722A — Rotation type battery replacement station and battery replacement method (회전형 교환 스테이지 및 가이드 정렬 메커니즘)

* **본 실시예의 공학적 차별점 (Specific Embodiment Feature)**
  * 공지된 차동 감속 및 배터리 교환 승강 원리를 기초로 하되, N/(N+1) 차동 기어비(60T/61T -> 0.016rpm)를 통한 상대속도 저충격 접합, 회전형 교환 스테이지, 양측/단측 홈 정렬 스왑랙 및 0.1ms HW Intercept 비상 이탈을 한정한 특정 실시예 구조에 기술적 차별성이 있음

* **소마모아 생태계 저장소 및 학술 식별자 (Ecosystem Repositories & DOIs)**
  * 상위 범용 생존 아키텍처 & APU 연산 제어기 (`chiplet-apu-multi-system-survival-architecture`) — GitHub: `deundeuni / chiplet-apu-multi-system-survival-architecture` | CERN Zenodo DOI: `10.5281/zenodo.22374987` (https://doi.org/10.5281/zenodo.22374987)
  * 재난 피난 유도 & 보조 인프라 (`LAST-LIGHT`) — GitHub: `deundeuni / LAST-LIGHT` | CERN Zenodo DOI: `10.5281/zenodo.22373189` (https://doi.org/10.5281/zenodo.22373189)
  * CWP 배터리 교환 도킹 (`CWP-Battery-Swap`) — CERN Zenodo DOI: `10.5281/zenodo.22373538` (https://doi.org/10.5281/zenodo.22373538)
  * CWP 전자기 클램핑 (`CWP-Clamping-Battery-Swap-System`) — CERN Zenodo DOI: `10.5281/zenodo.22373722` (https://doi.org/10.5281/zenodo.22373722)
  * CWP 롤링 셀프얼라인 (`CWP-Rolling-Self-Align-Battery-Swap-System`) — CERN Zenodo DOI: `10.5281/zenodo.22373704` (https://doi.org/10.5281/zenodo.22373704)
  * CWP 진입 유도 정렬 (`CWP-Entry`) — GitHub: `deundeuni / CWP-Entry`
  * 최상위 거점 관문 및 메인 저장소 (`soma-moa`) — GitHub: `deundeuni / soma-moa` | 관문 도메인: `somamoa.ai.kr`

* **법적 근거 및 선사용권·방어적 공개 규정 (Legal Statutes & Precedents)**
  * 대한민국 특허법 제103조 — 선사용에 의한 통상실시권
  * 미국 특허법 35 U.S.C. §273 — Defense to Infringement Based on Prior Commercial Use
  * 방어적 개시 및 고의성 부인 규정 — 본 문서는 미국 특허법상 고의 침해(Willful Infringement / 35 U.S.C. §284 및 관련 판례 법리) 주장에 대한 사전 방어 논리를 제공하고, 공공 영역(Public Domain)에 선행기술을 명시적으로 개시하여 제3자의 독점 특허화를 방지하기 위한 방어적 공개(Defensive Publication) 목적으로 공개되었음.
