> **다국어 공개 안내:** 본 문서는 동일 내용의 한/영 이중 공개 문서입니다. v2.6 2026-09-06 (영문 버전: [README.md](README.md))  
> **Original Authority Notice:** 본 기술 명세의 법적·공학적 판단 최상위 기준은 한글 원본(`README.ko.md`)에 귀속되며, 영문본은 보조 참조용으로만 기능한다. (PHILOSOPHY.ko.md is authoritative original)

# CWP-Entry - 진입 유도 및 위치 정렬 시스템 v2.6 Revised Final

* **공개 일자:** 2026-09-06 (초안 2026-08-20, v2.4 2026-08-27, v2.5 2026-09-03, v2.6 2026-09-06)
* **작성자:** deundeuni (System Architect / Natural Person Inventor)
* **라이선스:** CERN-OHL-S v2 (하드웨어/CAD/도면) | CC BY-SA 4.0 (문서/설명)
* **공개 목적:** 방어적 공개 / 선행기술(Prior Art) 등록 - 독점 특허화 방지 및 권리 침해 위험 완화
* **검색 키워드:** CWP, CWP-Entry, EV 배터리 교환, 진입 유도, 위치 정렬, 세차장 V레일, V-Rail, Line Laser, 0.1ms HW Intercept, Minimal Infra Retrofit, Quiet Assist, Fail-Safe, Selective Passage, EV Battery Swap Alignment, Guidance System, Prior Art, CWP-Rolling-Self-Align, CWP-Battery-Swap, CWP-Clamping

---

## 0. 설계자 독자 아키텍처 및 선행기술 공개 선언 (Designer's Philosophical Declaration)

1. **설계 철학 및 기술 조합의 독자성 (Architectural Conception):**  
   본 시스템은 기존 고가 전용 로봇 인프라의 경제적 한계 극복, 현장 숙련 엔지니어의 기존 기술 능력 연계 및 활용, 다양한 현장 환경(야외 노지, 정전, 승객 갇힘) 대입을 통한 저충격 도킹 및 0.1ms HW Intercept 기반 Fail-Safe 유도를 지향하는 **설계자(deundeuni)의 독자적 철학과 문제 의식**에서 출발하였다. '세차장 V레일 공용기술 + 진입 유도 정렬 시스템'의 방향성을 정립하고 최적의 파라미터 규격을 선택·조합한 아키텍처 결정권은 설계자 자연인에게 있다.

2. **소프트웨어 유틸리티 활용에 관한 명시 (Software Utility Limitation):**  
   본 문서 작성 과정에서 활용된 소프트웨어 및 AI 도구는 설계자가 이미 정의한 기술 조합, 설계 방향, 수치 파라미터를 바탕으로 단순 포맷팅, 문맥 정제, 개념 시각화 출력을 실행한 **수동적 실행 유틸리티(Passive Execution Utility)**에 국한된다. 본 인프라의 모든 설계 의도, 구조적 결합권, 선행기술 공개 권한은 전적으로 설계자에게 귀속된다.

---

## 1. 개요
CWP-Entry는 전기차 배터리 스왑 및 범용 모빌리티 정렬을 위한 진입 유도 및 위치 정렬 시스템이다.  
Guide -> Entry -> V-Home 3단계 정렬, 상부 라인 레이저 + 하부 V레일 결합을 통해 ±2mm 수준의 정밀 정렬 유도를 도모하도록 구성된다.

---

## 2. Background 및 인프라 경제학 (Background & Minimal Infra Retrofit)

* **기존 인프라 최소 개보수 연동 (Minimal Infra Retrofit):** 고가의 전용 로봇 설비를 새로 구축하거나 바닥을 완전히 철거하는 대공사 대신, 전국 주유소, 주차장, 자동 세차장에서 운용 중인 V레일 및 체인 이송 메커니즘을 원용. 5cm(SLIM) 또는 8cm(SHUTTLE) 모듈을 기존 인프라 표면에 최소 개보수 방식으로 연동하여 초기 구축 비용 경감 및 배터리 스왑 거점화를 도모함.
* **현장 엔지니어 기존 능력 연계 (High-Skill Human-Centric):** AI가 현장 엔지니어를 감시·대체하는 구조가 아닌, Quiet Assist 햅틱 신호(1x/2x)를 통해 숙련 엔지니어의 기존 정비 능력 및 현장 노하우를 직접 연계. 현장 인력의 실무 경험을 최우선 판단 요소로 결합하는 조력자 구조로 작동하도록 설계됨.
* **공용 기술 결합 (Public Domain Synergy):** 특정 기업의 독점 기술을 배제하고 표준 기계요소(시소, 차동 기어, V/U/C/T홈 등)를 조합하여 로열티 부담 완화 및 특정 기업의 특허 독점 가능성을 방어함.

---

## 3. 한계, 보증 부인 및 면책 (Limitation, Disclaimer of Warranties & Liability)

본 문서는 방어적 공개를 위한 기술적 개념 개시이며, 어떠한 보증도 없이 있는 그대로(AS-IS) 제공된다.

1. **보증 부인:** 특정 목적 적합성, 상품성, 안전성, 제품화를 보증하지 않는다.
2. **책임 제한:** 본 문서의 사용, 구현, 응용으로 인한 직접·간접 손해, 사고, 손실에 대해 작성자(deundeuni)는 어떠한 법적 책임도 지지 않는다.
3. **제3자 권리 비보증:** 본 문서가 제3자의 특허, 상표, 저작권 등 권리를 침해하지 않음을 보증하지 않으며, 권리 조사는 구현자의 책임이다.
4. **법규·안전·인증 책임:** 각 국가의 법규, 전기·소방·안전 기준, 인증 획득 및 안전 검증 책임은 전적으로 구현자에게 있다.

---

## 3.5 CWP 3대 하드웨어 연계 및 생존 아키텍처 (CWP 3-Hardware & System Integration)

본 CWP-Entry 시스템은 단독 작동에 그치지 않고 CWP 3대 핵심 하드웨어 메커니즘 및 상위 생존 아키텍처와 유기적으로 결합되어 무중단 생존 지향형 인프라를 형성할 수 있다.

* **진입 유도 및 1차 정렬 (`CWP-Entry` - 본 기술):** 세차장 V레일 인프라 원용 및 라인 레이저 가이드를 통해 차량 진입 오차를 완화하고 정비 구역으로 정밀 유도함.
* **기구적 2차 정렬 (`CWP-Rolling-Self-Align-Battery-Swap-System`):** V-홈 및 캐스터 수동/자율 정렬 메커니즘(A/B/C/S 타입)과 연동하여 진입 후 치수 오차(예: ±5mm 이상)를 물리적으로 흡수하고 정밀 도킹 구역으로 안내함.
* **차동 감속 저충격 도킹 (`CWP-Battery-Swap`):** N/(N+1) 차동 기어비(예: 60T/61T) 및 회전형 스테이지를 활용하여 도킹 상대속도를 극저속(예: 0.016rpm 수준)으로 감속시켜 완충 도킹을 지향함.
* **전자기 클램핑 및 안전 체결 (`CWP-Clamping-Battery-Swap-System`):** 범용 EPM 마그네틱 클램핑 모듈, 이중 핀 고정 및 3중 쿠션 구조와 결합하여 정밀 정렬 후 무전력 영구자석 고정 및 비상시 안전 해제를 지향함.
* **물리적 비상 차단·해제 (`0.1ms HW Intercept` / `LAST-LIGHT` 연계):** 화재, 정전 등 비상 상황 발생 시 Hardware Intercept 신호에 의해 체인, 공압, EPM 클램프가 릴리즈(Release)되어 무전력 기계식 이탈 및 탈출을 지향함.
* **연산적 제어 생존 (`chiplet-apu-multi-system-survival-architecture`):** 분산 관제(CCS) 및 다중 칩렛 제어 아키텍처와 결합하여 관제 칩렛 고장 시에도 진입 및 교환 로직이 지속 동작하도록 구성함.

---

## 4. 도면의 간단한 설명 (Brief Description of Drawings)

* **FIG. 1**: CWP-Entry 자율 유도 및 정렬 시스템의 전체 등각 투영도
  * 천장 마운트 및 라인 레이저를 통한 상부 1차 유도
  * V레일 가이드 채널 및 체인 견인 메커니즘을 통한 하부 2차 정렬
  * 배터리 스왑 플랫폼 결합 구조
* **FIG. 2**: CWP-Entry [SLIM] 타입 평면도 (5cm 매립/얹임, 단일 체인 견인 방식)
* **FIG. 3**: CWP-Entry [SHUTTLE] 타입 평면도 (8cm 팔레트, 4점 공압 에어리프트 방식)
* **FIG. 4**: CWP-Entry [FREE] 타입 평면도 (내장 팔레트, 결합 단일 모터, 2단 토크 센서, 복합 레이저 가이드 방식)

* **도면 비고:** 본 도면의 모든 치수, 각도, 수량은 범위를 한정하지 않는 예시이다. 기능적 구조(레일 가이드, 레이저 유도, 이송 연동)만이 본 공개의 핵심이다.

---

## 5. 라인업 (Lineup)

* **SLIM (Infra-Transition Type):** 5cm 매립/얹임 구조, 단일 체인 풀, 기존 인프라 호환 개보수형.
* **SHUTTLE:** 8cm 팔레트 구조, 4점 공압 리프트 결합형.
* **FREE:** 결합 단일 모터, 2단 토크 센서, 내장 팔레트, LED 가이드 및 라인 레이저 가이드 결합형.

---

## 6. 범용 확장성, 제어 모드 및 선택 통과 구조 (Universal Mobility & Protection)

### 6.1 이중 보호 및 이송 제어 모드 (Dual Protection Mode)
본 시스템은 비상 상황 시의 차단 반응속도와 정상 상태의 이송 메커니즘을 물리적으로 구분하여 운용한다.

* **Mode A - 0.1ms HW Fail-Safe (비상 차단·해제 반응속도):** 화재, 정전, 신호 이상 발생 시 Hardware Intercept(EN LOW, soma-moa E_STOP_LATCH 연동)를 통해 0.1ms 이하의 반응속도로 체인 및 공압 릴리즈 신호 구동을 차단/해제 방향으로 전환한다. 이는 이송 물리 속도가 아닌 제어 신호 차단 및 무전력 기계식 해제 반응시간을 의미한다.
* **Mode B - 정상 진입 정렬 이송 (정숙 이송 제어):** Guide -> Entry -> V-Home 구간에서는 초 단위의 완만한 정숙 이송을 수행하며, 모터 과부하 및 기계적 충격을 방지하는 부드러운 토크 스무싱 보호 로직을 적용한다.

### 6.2 범용 확장성 및 비상 탈출 (Universal Mobility & Safety Escape)
* **Form-Factor Agnostic:** 승용 EV 외 UAM/드론 landing skid, 물류 AGV/AMR, 마이크로 모빌리티, 특수 탐사 로버 및 궤도상 모듈 정렬 구조로 확장 가능함.
* **Rescue Clearance:** 측면 Door Clearance(최대 850mm) 확보 및 정전 시 상부 라인 레이저의 비상 유도등 자동 전환(30분 배터리 백업) 지원.

### 6.3 선택 통과 시스템 및 적용 범위 확장 (Selective Passage & Extended Scope)
* **선택 통과 연동:** Minimal Infra Retrofit 원칙에 따라 신규 전용 이송 로봇 추가 없이 기존 자동 세차장 레일 인프라를 원용하여 진출입 동선을 구현함.
  * **스왑 이용 차량:** 배터리 교체 완료 후 기존 세차 라인으로 자연스럽게 진입하여 후속 공정 수행 (기존 체인 메커니즘 공유).
  * **미이용 통과 차량:** 별도의 복잡한 가변 분기 기계 장치 없이 기존 세차장의 표준 분기 가이드 구조를 원용하여 단순 통과 및 출차가 가능함.
* **기존 연료 유통 및 플릿 연동:** 주유소, 충전소 등 기존 액체연료 유통 거점 및 카셰어링, 택시, 물류 플릿 정비 거점의 지면 이송 인프라에 동일하게 배치 가능함.

---

## 7. 실리보호 (Practical Protection)

* **원안 우선 원칙:** 본 명세서의 법적·기술적 해석은 한국어 원본(`README.ko.md`)을 최우선 기준으로 적용하며, 영문본 및 기타 언어 번역본은 참고용으로만 기능한다.
* **범위 포괄성:** 본 문서에 기술된 레일 규격, 센서 파라미터, 진입 오차 수치, 이송 모드, 라인업 등은 광범위한 선행기술 선점을 위한 예시로서 상위개념으로 포괄 적용된다.
* **사업화 내용 분리:** 본 백서 원안에는 Pure Open Source 및 선행기술 개시 내용만을 포함하며, 독자적인 수익 모델 및 사업화 세부 실행안은 별도 기술 문서로 분리 관리한다.

---

## 8. 출처 (Sources)

* **공식 저장소:** GitHub Repository (`deundeuni/CWP-Entry`)
* **연계 CWP 저장소 1:** GitHub Repository (`deundeuni/CWP-Rolling-Self-Align-Battery-Swap-System`)
* **연계 CWP 저장소 2:** GitHub Repository (`deundeuni/CWP-Battery-Swap`)
* **연계 CWP 저장소 3:** GitHub Repository (`deundeuni/CWP-Clamping-Battery-Swap-System`)
* **연계 아키텍처 저장소:** GitHub Repository (`deundeuni/chiplet-apu-multi-system-survival-architecture`)
* **최상위 관문:** `somamoa.ai.kr` (Canonical Gateway)

---

## Appendix A. 기여 및 역할 (Inventorship & Attribution)

* **deundeuni (System Architect & Sole Inventor):** 본 명세서에 기술된 CWP-Entry 시스템 아키텍처, V레일 정렬 파라미터, 현장 엔지니어 기존 능력 연계 기반 진입 유도 메커니즘, 0.1ms HW Intercept 및 Minimal Retrofit 구조의 총괄 기획자이자 원천 발명자 (Natural Person Conception).
* **Software Tooling Notice:** 소프트웨어 유틸리티 도구는 설계자의 직접 지시 및 조건 대입에 따라 문서 정제 및 단순 시각 보조 도구로 제한적으로 활용되었으며, 본 시스템의 독자적 설계 노하우, 핵심 로직 및 발명자성에는 영향을 미치지 않음.

---

## Appendix B. 참조 규격 및 적용 표준 (Standards & References)

* **[Standard-EV]** IEC 62840-1:2016 (EV Battery Swap Infrastructure Safety)
* **[Standard-EV]** GB/T 40032-2021 (Electric Vehicle Battery Swap Safety Requirement)
* **[Standard-Comm]** ISO 15118 (Road vehicles — Vehicle to grid communication interface)
* **[Standard-Safety]** ISO 13849-1:2023 (Safety of machinery — Safety-related parts of control systems / Cat 4, PL e)
* **[Standard-Safety]** IEC 61508:2010 (Functional Safety of E/E/PE Safety-related Systems / SIL3)
* **[Standard-Design]** ISO 128 / USPTO MPEP 608.02 (Technical Drawings & Patent Drawing Standards)
* **[Standard-Label]** KS M ISO 17398 (Safety colours and safety signs)
* **[Legal-AI]** USPTO AI Inventorship Guidance 2024 (Principle 3: Refinement & Error Correction)
* **[Prior Art]** 세차장 이송 레일 업계 관행 (V레일 + 체인 견인 메커니즘, 20년 이상 Public Domain)
