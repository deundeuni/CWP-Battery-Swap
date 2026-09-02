# CWP-Entry - Entry Guidance and Positional Alignment System v2.5 Revised Final

> **Domain:** somamoa.ai.kr | **Origin:** deundeuni (System Architect)  
> **Licenses:** CERN-OHL-S v2 (Hardware/CAD/Schematics) | CC BY-SA 4.0 (Documentation/Diagrams)  
> **Public Domain & Prior Art Declaration:** 2026-08-20 (Initial) / 2026-08-27 (v2.4) / 2026-09-03 (v2.5 Revised Final)

---

## 0. Designer's Philosophical Declaration (Designer's Independent Conception & Prior Art Disclosure)

1. **Architectural Conception and Originality of Technology Combination:**  
   This system originated from the **designer's (deundeuni) independent philosophy and problem-solving framework**: overcoming the economic limitations of conventional high-cost dedicated robotic infrastructure, integrating and utilizing the existing technical capabilities of skilled field engineers, and achieving low-impact docking alongside 0.1ms HW Intercept Fail-Safe across various field conditions (outdoor unpaved terrain, power outages, and trapped passengers). The architectural decision-making authority—establishing the direction of 'Car Wash V-Rail Public Domain Synergy + Entry Guidance Alignment System' and selecting/combining optimal parametric specifications—belongs solely to the natural person designer.

2. **Limitation on Software Utility Usage:**  
   Software and AI tools utilized in drafting this document are limited strictly to **Passive Execution Utilities** that executed simple formatting, contextual refinement, and conceptual visualization outputs based on the technology combinations, design directions, and numerical parameters already defined by the designer. All design intent, structural combination rights, and prior art disclosure authority for this infrastructure belong entirely to the designer.

---

## 1. Overview
CWP-Entry is an entry guidance and positional alignment system designed for electric vehicle battery swapping and universal mobility alignment.  
It utilizes a 3-stage alignment process (Guide -> Entry -> V-Home), combining an overhead line laser with a sub-surface V-rail to achieve high-precision alignment within ±2mm.

---

## 2. Background & Minimal Infra Retrofit Economics

* **Minimal Infra Retrofit:** Instead of constructing expensive new dedicated robotic facilities or completely demolishing existing ground surfaces, the system reuses field-proven V-rail and chain transport mechanisms deployed across gas stations, parking lots, and automatic car washes for over 20 years. By overlaying or embedding 5cm (SLIM) or 8cm (SHUTTLE) modules with minimal modification onto existing infrastructure surfaces, battery swap hubs are established at minimal CAPEX.
* **High-Skill Human-Centric Integration:** Rather than replacing or monitoring field engineers with AI, the system directly bridges the existing maintenance skills and field know-how of experienced technicians via Quiet Assist haptic signals (1x/2x). It operates as an assistant framework that prioritizes human practical expertise as the primary decision-making element.
* **Public Domain Synergy:** By excluding proprietary monopoly technologies and combining standard mechanical elements verified for over a century (seesaws, differential gears, V/U/C/T grooves), the system eliminates royalty burdens and prevents single-entity patent monopolies.

---

## 3. Brief Description of Drawings

* **FIG. 1**: Isometric overall view of the CWP-Entry autonomous guidance and positional alignment system
  * Overhead primary guidance via ceiling mount and line laser
  * Sub-surface secondary alignment via V-rail guide channel and chain traction mechanism
  * Battery swap platform interface structure
* **FIG. 2**: Top plan view of CWP-Entry [SLIM] type (5cm embedded/overlay, single chain traction method)
* **FIG. 3**: Top plan view of CWP-Entry [SHUTTLE] type (8cm pallet, 4-point pneumatic air-lift method)
* **FIG. 4**: Top plan view of CWP-Entry [FREE] type (integrated pallet, single coupling motor, 2-stage torque sensor, dual laser guide method)

---

## 4. Product Lineup

* **SLIM (Infra-Transition Type):** 5cm embedded/overlay structure, single chain pull, compatible retrofit type for existing infrastructure.
* **SHUTTLE:** 8cm pallet structure, integrated with 4-point pneumatic air-lift.
* **FREE:** Integrated single motor, 2-stage torque sensor, internal pallet, combined LED guide and line laser guidance.

---

## 5. Universal Mobility, Safety & Dual Protection Mode

### 5.1 Dual Protection Mode
This system physically decouples the emergency shutoff response speed from the normal operational transport mechanism.

* **Mode A - 0.1ms HW Fail-Safe (Emergency Shutoff/Release Response):** Upon detection of fire, power loss, or signal anomalies, Hardware Intercept (EN LOW, linked with soma-moa E_STOP_LATCH) cuts off chain drive and pneumatic release signals within 0.1ms. This parameter refers strictly to control signal cutoff and unpowered mechanical disengagement response time, not physical transport movement.
* **Mode B - Normal Entry Alignment Transport (Smooth Transport Control):** During the Guide -> Entry -> V-Home stages, the system performs smooth, low-speed transport over seconds, applying smooth torque protection logic to prevent motor overload and mechanical impact.

### 5.2 Universal Mobility & Safety Escape
* **Form-Factor Agnostic:** Expandable beyond passenger EVs to UAM/drone landing skids, logistics AGVs/AMRs, micro-mobility, specialized exploration rovers, and orbital module alignment structures.
* **Rescue Clearance:** Guarantees lateral Door Clearance (up to 850mm) and automatically switches the overhead line laser to emergency lighting mode during power outages (supported by 30-minute backup battery).

---

## 6. Licensing & Commercial Usage Guidelines

* **Hardware / CAD / Schematics:** CERN-OHL-S v2 (Strongly Reciprocal)
* **Documentation / Spec:** CC BY-SA 4.0
* **Copyright (c) 2026 deundeuni / somamoa.ai.kr**
* **Commercial Use Notice:** Commercial manufacturing and sales are permitted for anyone. Only modifications/improvements to CWP drawings must be disclosed under the same license; external proprietary trade secrets combined with this system do not require retroactive public disclosure.

---

## 7. Standards & References

* **[Standard-EV]** IEC 62840-1:2016 (EV Battery Swap Infrastructure Safety)
* **[Standard-EV]** GB/T 40032-2021 (Electric Vehicle Battery Swap Safety Requirement)
* **[Standard-Comm]** ISO 15118 (Road vehicles — Vehicle to grid communication interface)
* **[Standard-Safety]** ISO 13849-1:2023 (Safety of machinery — Safety-related parts of control systems / Cat 4, PL e)
* **[Standard-Safety]** IEC 61508:2010 (Functional Safety of E/E/PE Safety-related Systems / SIL3)
* **[Standard-Design]** ISO 128 / USPTO MPEP 608.02 (Technical Drawings & Patent Drawing Standards)
* **[Standard-Label]** KS M ISO 17398 (Safety colours and safety signs)
* **[Legal-AI]** USPTO AI Inventorship Guidance 2024 (Principle 3: Refinement & Error Correction)
* **[Prior Art]** Car wash conveyor rail industry practice (V-rail + chain traction mechanism, Public Domain for >20 years)

---

## 8. Selective Passage System

Adhering to the Minimal Infra Retrofit principle, entry and exit traffic flows are implemented by leveraging existing automatic car wash rail infrastructure without adding complex dedicated transport robots.

* **Interlocking Structure:** The battery swapping CWP-Entry line interfaces directly with existing car wash chain rails and movement corridors.
* **Swap-Utilizing Vehicles:** After completing the battery swap, vehicles naturally transition into the existing car wash line to proceed with follow-up processes (sharing the existing chain mechanism).
* **Bypass Vehicles:** Non-swapping vehicles bypass and exit straight through by utilizing standard car wash divergence guide structures without requiring complex variable mechanical switches.
* **Operational Flexibility:** Guarantees service choice for users while excluding forced entry constraints on any vehicle type.

---

## 9. Extended Application Scope

The Minimal Infra Retrofit concept of this system is not restricted to car wash rail structures and extends to similar infrastructure domains:

* **Existing Fuel Distribution Infrastructure:** Applicable to ground transport and vehicle alignment infrastructure at gas stations and charging hubs using identical V-rail/chain mechanisms.
* **Fleet & Shared Mobility Hubs:** Deployable with minimal retrofitting across maintenance and swap lines in concentrated fleet operation bases including car-sharing, taxi, and logistics fleets.

---

## Appendix A. Inventorship & Attribution

* **deundeuni (System Architect & Sole Inventor):** Overall architect and sole natural person inventor of the CWP-Entry system architecture, V-rail alignment parameters, human-centric guidance mechanisms, 0.1ms HW Intercept, and Minimal Retrofit structure (Natural Person Conception).
* **Software Tooling Notice:** Software utility tools were used strictly as passive aids for formatting, text refinement, and visual support under direct instruction and parameter input by the designer, and did not impact the independent design know-how, core logic, or inventorship of this system.
