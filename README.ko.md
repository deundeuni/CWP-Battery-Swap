> **다국어 공개 안내:** 본 문서는 동일 내용의 한/영 이중 공개 문서입니다. v3.1 2026-08-22 (영문 버전: [README.md](README.md))

# CWP-Battery-Swap v3.1 - 핫스왑을 위한 차동 감속 도킹 메커니즘 및 회전형 교환 스테이지

* **공개 일자:** 2026-08-22 (초안 2026-08-20, v0.2.1 2026-08-22, v3.0 2026-08-22)
* **작성자:** deundeuni
* **라이선스:** CC BY 4.0 - 자유 이용, 출처 표기
* **공개 목적:** 방어적 공개 / 선행기술(Prior Art) 등록 - 독점 특허화 방지
* **검색 키워드:** EV 배터리 교환, 핫스왑, CWP, 차동 감속, 저충격 도킹, 시소 지렛대 원리, 원심력, 자전거 기어비 60T/61T 0.016rpm, 우주 도킹, ESS, 물류로봇, 드론, V홈 U홈 C홈 T홈 더브테일 핀소켓, 홈 정렬, 스왑랙, 회전형 스테이지, Groove Alignment, Swap-Rack, Rotary Battery Swapping Stage, Low-impact docking, Differential reduction

---

## 0. 설계자 노트 (Designer's Note)

전기차가 충전하는 동안 기다리는 시간이 너무 아까웠다. 배터리를 교체식으로 하면 시간을 아낄 수 있지 않을까? 그런데 무거운 배터리를 꽂는 순간 충격이 크면 차가 망가질 텐데, 시소처럼, 자전거 기어처럼 천천히 맞물리면 되지 않을까? 라는 생각에서 시작됨.

이 고민과 조합의 방향은 전적으로 설계자 본인(deundeuni)이 한 것이며, AI는 계산과 정리 과정에서 도구로 활용됨.

* **AI 활용 공개:** 초안 작성 및 정리 Meta AI, 기술 검토 및 문서 형식화 Google Gemini, 도면 작성 Claude(Rika)를 도구로 활용. 핵심 아이디어 착안, 조합 결정, 최종 판단은 모두 설계자 본인이 수행.

---

### 0.1 착안 배경 및 공공 기술 조합 (Public Domain Combination)

본 방식은 새로 만든 원천 기술이 아니며, 100년 이상 공개된 표준 기술들의 조합적 활용임.

* **시소 / 지렛대 원리** (표준 역학)
* **원심력 / 회전 안정성** (표준 물리)
* **자전거 기어비** (표준 기계요소: 60T/61T -> 0.016rpm 예시)
* **우주 도킹 시스템** (표준 도킹 메커니즘)
* **V홈/U홈 및 더브테일/핀-소켓 정렬** (표준 기계요소: 선반 센터, 금형 가이드, 서랍 레일)

---

### 0.2 조합 예시 (일례, 한정 없음)

본 조합이 어떻게 동작할 수 있는지에 대한 이해를 돕기 위한 단순한 일례이며, 순서나 수치가 바뀌어도 본 선행기술에 속함.

1. **접근:** 전기차가 교체 스테이션에 우주 도킹처럼 정렬하여 접근
2. **하중 분산:** 시소/지렛대 원리로 배터리 무게 분산 지지
3. **저속 접합:** 차동 기어비(예: 60T/61T)로 상대속도를 저속(예: 0.016rpm 수준)으로 감속시켜 무충격 도킹
4. **정렬 고정:** 홈 구조로 위치를 구속하여 도킹 정밀도 확보

---

### 0.3 홈 정렬 및 스왑랙 구조 (Groove Alignment & Swap-Rack)

* **양측면 홈 방식 (Both-side groove):** 배터리 양 측면 홈과 본체 대응 홈 결합으로 2축 동시 구속, 고정밀 정렬.
* **단측면 홈 방식 (One-side groove):** 한쪽만 구속하고 반대쪽은 유격(여유 공간)을 두어 1축 구속 및 조립 오차 흡수, 고속 교환.
* **스왑랙 분리형 메커니즘 (Swap-Rack):** 단측면 인출(One-side out) -> 이송(Transfer) -> 양측면 삽입(Both-side in) 순서로 탈착, 충전은 스테이션 내부에서 분리 수행.
* **저충격 가압 메커니즘 (공통):** 일정 오프셋 구간(예: 약 100mm 전)부터 서서히 지그시 누르는 방식으로 충격 최소화.
* **형상 및 수치 범위 비한정 선언 (핵심):** 본 문서에 기술된 모든 홈 형상(V홈, U홈, C홈, T홈, 더브테일, 핀-소켓 등 암수 결합 가이드 전반), 기어비(60T/61T 등), 속도(0.016rpm 등), 거리(100mm 등), 구동 방식(모터/공압/유압/수동/지렛대), 개수(8슬롯 등)는 이해를 돕기 위한 일례이며, 형태 변형, 수치 변경, 구동원 변경을 포함한 모든 유사 응용은 본 선행기술의 범위에 속함.

---

### 0.4 회전형 교환 스테이지 결합 예시 (Rotary Swapping Stage)

본 도킹 메커니즘은 회전형 스테이션과 결합될 수 있다. (Fig.1, Fig.2 참조)

* **구성:** 중앙 회전 허브 베어링 어셈블리, 회전 플랫폼, 양측면 레버 메커니즘(피벗/리니어 액추에이터), 양측면 도킹 홈(자동정렬 챔퍼 홈).
* **동작:** 회전(Rotation) -> 정렬(Alignment) -> 저충격 도킹(Docking) -> 잠금(Lock) 순서로 자동 교환.
* **비한정:** 슬롯 수, 플랫폼 형상, 회전 방향(CW/CCW), 레버 구조가 바뀌어도 동일 기술로 간주함.

---

## 1. 핵심 개념

배터리 교체 시 충격 최소화를 위한 차동 감속 도킹 구조 및 이를 활용한 회전형 교환 시스템.

### 1.1 방어 논리 (Defensive Logic)
본 방식은 누구나 생각할 수 있는 공공 기술의 조합임을 명시하여, 특정 기업/국가의 독점 특허화를 방지하고 자유 사용을 목적으로 함. 본 문서 자체가 선행기술임.

### 1.2 적용 범위
EV, ESS, 물류로봇, 드론, 선박, 항공우주 등 배터리 교환이 필요한 전 분야. 공개된 산업 동향을 바탕으로 설계자가 정의한 넓은 범위이며, 이에 한정되지 않음.

---

## 2. 도면 (Figures) - 무치수 광역 버전

회전형 배터리 교환 스테이지 - 기술 개략도]

![fig1](https://private-user-images.githubusercontent.com/319694809/639891656-4e1d2ffb-7aef-4e30-a1d1-65091c850691.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3ODc0MDEyMTMsIm5iZiI6MTc4NzQwMDkxMywicGF0aCI6Ii8zMTk2OTQ4MDkvNjM5ODkxNjU2LTRlMWQyZmZiLTdhZWYtNGUzMC1hMWQxLTY1MDkxYzg1MDY5MS5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjYwODIyJTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI2MDgyMlQxMjE1MTNaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT1lNDRjNGYwMzgzZmE0ZGJlZDBlZDI4ODAxYzZkZDAwNzVjMWZkMGU5ZGI3YmU0NTkyMTM1ZmNjMmY0YTdkYzFmJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCZyZXNwb25zZS1jb250ZW50LXR5cGU9aW1hZ2UlMkZwbmcifQ.biSpUMSEH0Kr6RbZR05__584EpbRhMPORUqlXqvXJWo)

* **도면 비고:** 본 도면의 모든 치수, 각도, 수량은 예시이며 범위를 한정하지 않음. 기능적 구조(회전, 홈 정렬, 레버 잠금)만이 본 공개의 핵심임.

**주의 (AI 시각화 면책 조항):** 본 도면의 메커니즘 개념은 설계자(deundeuni)가 독자적으로 고안했습니다. 첨부된 이미지는 이해를 돕기 위해 AI 도구(Meta AI)를 활용하여 생성된 개념적 시각화 예시일 뿐이며, 기존의 특정 상용 제품이나 타인의 등록 특허 도면을 복제한 것이 아닙니다.

---

## 3. 한계 및 면책

유사 아이디어가 존재할 수 있으나, 본 문서는 하나의 가능한 방식을 제시하는 것이며 특정 환경에서의 동작을 보장하지 않음. 본 문서는 방어적 공개를 위한 기술적 개념 개시이며, 제품화를 보증하지 않음.

---

## 4. 공개 증명

GitHub 커밋 이력이 최초 공개 시점(2026-08-20)을 증명함.  
본 v3.0은 Zenodo DOI 발급 예정.

---

## 5. 버전 이력

* **v0.1 (2026-08-20):** 초안
* **v0.2.1 (2026-08-22):** 차동 감속 도킹 개념 공개
* **v3.0 (2026-08-22):** 회전형 스테이지 결합, 무치수 도면 추가, 비한정 선언 강화

---

## 6. 라이선스

CC BY 4.0 - 누구나 자유롭게 이용, 변형, 상업적 이용 가능. 단 출처 표기.
