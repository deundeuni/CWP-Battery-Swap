# CWP-Entry - 진입 유도 및 위치 정렬 시스템 v2.5 Revised Final

> **Domain:** somamoa.ai.kr | **Origin:** deundeuni (System Architect)  
> **Licenses:** CERN-OHL-S v2 (Hardware/CAD/Schematics) | CC BY-SA 4.0 (Documentation/Diagrams)  
> **Public Domain & Prior Art Declaration:** 2026-08-20 (Initial) / 2026-08-27 (v2.4) / 2026-09-03 (v2.5 Revised Final)

---

## 0. 설계자 독자 아키텍처 및 선행기술 공개 선언 (Designer's Philosophical Declaration)

1. **설계 철학 및 기술 조합의 독자성 (Architectural Conception):**  
   본 시스템은 기존 고가 전용 로봇 인프라의 경제적 한계 극복, 현장 숙련 엔지니어의 기존 기술 능력 연계 및 활용, 다양한 현장 환경(야외 노지, 정전, 승객 갇힘) 대입을 통한 저충격 도킹 및 0.1ms HW Intercept 기반 Fail-Safe 달성이라는 **설계자(deundeuni)의 독자적 철학과 문제 의식**에서 출발하였다. '세차장 V레일 공용기술 + 진입 유도 정렬 시스템'의 방향성을 정립하고 최적의 파라미터 규격을 선택·조합한 아키텍처 결정권은 설계자 자연인에게 있다.

2. **소프트웨어 유틸리티 활용에 관한 명시 (Software Utility Limitation):**  
   본 문서 작성 과정에서 활용된 소프트웨어 및 AI 도구는 설계자가 이미 정의한 기술 조합, 설계 방향, 수치 파라미터를 바탕으로 단순 포맷팅, 문맥 정제, 개념 시각화 출력을 실행한 **수동적 실행 유틸리티(Passive Execution Utility)**에 국한된다. 본 인프라의 모든 설계 의도, 구조적 결합권, 선행기술 공개 권한은 전적으로 설계자에게 귀속된다.

---

## 1. 개요
CWP-Entry는 전기차 배터리 스왑 및 범용 모빌리티 정렬을 위한 진입 유도 및 위치 정렬 시스템이다.  
Guide -> Entry -> V-Home 3단계 정렬, 상부 라인 레이저 + 하부 V레일 결합을 통해 ±2mm 수준의 정밀 정렬을 달성하도록 구성된다.

---

## 2. Background 및 인프라 경제학 (Background & Minimal Infra Retrofit)

* **기존 인프라 최소 개보수 연동 (Minimal Infra Retrofit):** 고가의 전용 로봇 설비를 새로 구축하거나 바닥을 완전히 철거하는 대공사 대신, 전국 주유소, 주차장, 자동 세차장에서 운용 중인 V레일 및 체인 이송 메커니즘을 원용. 5cm(SLIM) 또는 8cm(SHUTTLE) 모듈을 기존 인프라 표면에 최소 개보수 방식으로 연동하여 초기 구축 비용을 경감하고 배터리 스왑 거점화를 달성함.
* **현장 엔지니어 기존 능력 연계 (High-Skill Human-Centric):** AI가 현장 엔지니어를 감시·대체하는 구조가 아닌, Quiet Assist 햅틱 신호(1x/2x)를 통해 숙련 엔지니어의 기존 정비 능력 및 현장 노하우를 직접 연계. 현장 인력의 실무 경험을 최우선 판단 요소로 결합하는 조력자 구조로 작동.
* **공용 기술 결합 (Public Domain Synergy):** 특정 기업의 독점 기술을 배제하고 표준 기계요소(시소, 차동 기어, V/U/C/T홈 등)를 조합하여 로열티 부담 완화 및 특정 기업의 특허 독점 가능성을 차단.

---

## 3. 도면의 간단한 설명 (Brief Description of Drawings)

* **FIG. 1**: CWP-Entry 자율 유도 및 정렬 시스템의 전체 등각 투영도
  * 천장 마운트 및 라인 레이저를 통한 상부 1차 유도
  * V레일 가이드 채널 및 체인 견인 메커니즘을 통한 하부 2차 정렬
  * 배터리 스왑 플랫폼 결합 구조
* **FIG. 2**: CWP-Entry [SLIM] 타입 평면도 (5cm 매립/얹임, 단일 체인 견인 방식)
* **FIG. 3**: CWP-Entry [SHUTTLE] 타입 평면도 (8cm 팔레트, 4점 공압 에어리프트 방식)
* **FIG. 4**: CWP-Entry [FREE] 타입 평면도 (내장 팔레트, 결합 단일 모터, 2단 토크 센서, 복합 레이저 가이드 방식)

---

## 4. 라인업 (Lineup)

* **SLIM (Infra-Transition Type):** 5cm 매립/얹임 구조, 단일 체인 풀, 기존 인프라 호환 개보수형.
* **SHUTTLE:** 8cm 팔레트 구조, 4점 공압 리프트 결합형.
* **FREE:** 결합 단일 모터, 2단 토크 센서, 내장 팔레트, LED 가이드 및 라인 레이저 가이드 결합형.

---

## 5. 범용 확장성, 안정성 및 제어 모드 (Universal Mobility & Dual Protection Mode)

### 5.1 이중 보호 및 이송 제어 모드 (Dual Protection Mode)
본 시스템은 비상 상황 시의 차단 반응속도와 정상 상태의 이송 메커니즘을 물리적으로 구분하여 운용한다.

* **Mode A - 0.1ms HW Fail-Safe (비상 차단·해제 반응속도):** 화재, 정전, 신호 이상 발생 시 Hardware Intercept(EN LOW, soma-moa E_STOP_LATCH 연동)를 통해 0.1ms 이하의 반응속도로 체인 및 공압 릴리즈 신호를 차단한다. 이는 이송 물리 속도가 아닌 제어 신호 차단 및 무전력 기계식 해제 반응시간을 의미한다.
* **Mode B - 정상 진입 정렬 이송 (정숙 이송 제어):** Guide -> Entry -> V-Home 구간에서는 초 단위의 완만한 정숙 이송을 수행하며, 모터 과부하 및 기계적 충격을 방지하는 부드러운 토크 스무싱 보호 로직을 적용한다.

### 5.2 범용 확장성 및 비상 탈출 (Universal Mobility & Safety Escape)
* **Form-Factor Agnostic:** 승용 EV 외 UAM/드론 landing skid, 물류 AGV/AMR, 마이크로 모빌리티, 특수 탐사 로버 및 궤도상 모듈 정렬 구조로 확장 가능.
* **Rescue Clearance:** 측면 Door Clearance(최대 850mm) 확보 및 정전 시 상부 라인 레이저의 비상 유도등 자동 전환(30분 배터리 백업) 지원.

---

## 6. 라이선스 및 상업적 이용 안내 (Licensing)

* **Hardware / CAD / Schematics:** CERN-OHL-S v2 (Strongly Reciprocal)
* **Documentation / Spec:** CC BY-SA 4.0
* **Copyright (c) 2026 deundeuni / somamoa.ai.kr**
* **상업적 이용 안내:** 누구나 상업적 제조 및 판매가 가능함. CWP 개작/개선 도면만 동일 라이선스로 공개해야 하며, 결합되는 타사의 독립적 비공개 비밀 설계(Trade Secret)까지 소급 공개할 필요는 없음.

---

## 7. 참조 규격 및 적용 표준 (Standards & References)

* **[Standard-EV]** IEC 62840-1:2016 (EV Battery Swap Infrastructure Safety)
* **[Standard-EV]** GB/T 40032-2021 (Electric Vehicle Battery Swap Safety Requirement)
* **[Standard-Comm]** ISO 15118 (Road vehicles — Vehicle to grid communication interface)
* **[Standard-Safety]** ISO 13849-1:2023 (Safety of machinery — Safety-related parts of control systems / Cat 4, PL e)
* **[Standard-Safety]** IEC 61508:2010 (Functional Safety of E/E/PE Safety-related Systems / SIL3)
* **[Standard-Design]** ISO 128 / USPTO MPEP 608.02 (Technical Drawings & Patent Drawing Standards)
* **[Standard-Label]** KS M ISO 17398 (Safety colours and safety signs)
* **[Legal-AI]** USPTO AI Inventorship Guidance 2024 (Principle 3: Refinement & Error Correction)
* **[Prior Art]** 세차장 이송 레일 업계 관행 (V레일 + 체인 견인 메커니즘, 20년 이상 Public Domain)

---

## 8. 선택 통과 시스템 (Selective Passage System)

Minimal Infra Retrofit 원칙에 따라 신규 전용 이송 로봇 추가 없이 기존 자동 세차장 레일 인프라를 원용하여 진출입 동선을 구현한다.

* **연동 구조:** 배터리 교체용 CWP-Entry 라인을 기존 세차장 체인 레일 및 동선과 직접 연동한다.
* **스왑 이용 차량:** 배터리 교체 완료 후 기존 세차 라인으로 자연스럽게 진입하여 후속 공정을 수행(기존 체인 메커니즘 공유).
* **미이용 통과 차량:** 별도의 복잡한 가변 분기 기계 장치 없이 기존 세차장의 표준 분기 가이드 구조를 원용하여 단순 통과 및 출차가 가능함.
* **운용 유연성:** 서비스 선택권을 보장하며, 특정 차량에 대한 강제 진입 구조를 배제함.

---

## 9. 적용 범위 확장 (Extended Application Scope)

본 시스템의 최소 개보수 연동 사상은 세차장 레일 구조에 한정되지 않으며, 다음과 같은 유사 인프라 영역으로 확장 적용될 수 있다.

* **기존 연료 유통 인프라 연동:** 주유소, 충전소 등 기존 액체연료 유통 거점의 지면 이송 및 차량 정렬 인프라에 동일한 V레일/체인 이송 메커니즘으로 적용 가능.
* **플릿 및 공유 모빌리티 거점:** 카셰어링, 택시, 물류 플릿 등 집중형 운영 거점의 정비/스왑 라인에 동일한 방식으로 최소 개보수 배치 가능.

---

## Appendix A. 기여 및 역할 (Inventorship & Attribution)

* **deundeuni (System Architect & Sole Inventor):** 본 명세서에 기술된 CWP-Entry 시스템 아키텍처, V레일 정렬 파라미터, 현장 엔지니어 기존 능력 연계 기반 진입 유도 메커니즘, 0.1ms HW Intercept 및 Minimal Retrofit 구조의 총괄 기획자이자 원천 발명자 (Natural Person Conception).
* **Software Tooling Notice:** 소프트웨어 유틸리티 도구는 설계자의 직접 지시 및 조건 대입에 따라 문서 정제 및 단순 시각 보조 도구로 제한적으로 활용되었으며, 본 시스템의 독자적 설계 노하우, 핵심 로직 및 발명자성에는 영향을 미치지 않음.
