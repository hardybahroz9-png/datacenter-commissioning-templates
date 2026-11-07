# Method of Procedure (MOP): Whole-Facility Blackout Simulation

**Document ID:** MOP-ENG-001  
**Target System:** Utility Power Infrastructure / Standby Generation  
**Level:** Level 5 Integrated Systems Testing (IST)  
**Author:** Hardy Maroof, Data Center Commissioning Engineer  

---

## 1. Purpose & Objective
This MOP outlines the step-by-step field execution guide to simulate a catastrophic loss of normal utility power (blackout). The test validates the automatic sequence of operations for the emergency standby generation system, primary electrical switchgear transfer, and automated mechanical cooling plant restart.

## 2. Safety, PPE, & Lockout/Tagout (LOTO)
- **Arc Flash Boundary:** All operations inside electrical rooms must strictly adhere to NFPA 70E boundaries.
- **Required PPE:** Minimum Category 2 Arc Flash suit, face shield, insulated safety gloves (Class 00/0), safety glasses, and steel-toe boots.
- **LOTO Protocol:** All circuit breakers altered during this procedure must be under active engineering monitoring, tagged out where appropriate, and operated strictly via remote pendant or BMS/EPMS command when applicable to minimize flash risk.
- **Emergency Halt:** At any point, the Commissioning Engineer, Facility Operations Lead, or safety watchers can call a **"STOP WORK"** order if telemetry values stray outside critical safety boundaries.

---

## 3. Pre-Test Conditions & Equipment Alignment
Before executing the primary power drop, confirm the following initial states:

- [ ] **Utility Feeders:** Both Source 1 (Grid A) and Source 2 (Grid B) are active and supporting the facility normally.
- [ ] **UPS Systems:** Main UPS strings are online, in normal double-conversion mode, and fully charged (100% battery capacity).
- [ ] **Standby Generators:** Jacket heaters active, fuel day tanks verified at >95% capacity, zero active engine control unit (ECU) alarms.
- [ ] **BMS / EPMS:** Telemetry logging interval set to 1-second capture frequency for transient monitoring.
- [ ] **Load Banks:** Temporary load banks deployed on the data hall floor are energized and stabilizing at 100% design thermal/electrical load.

---

## 4. Step-by-Step Step Sequence

| Step | Time | Authorized Operator | Action Items / Operational Commands | Expected Engineering Feedback | Verification Notes |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **1.1** | T-00:00 | Control Room Eng | Initiate data recording on BMS/EPMS historical trend logs. | Status registers active; baseline GPM, kW, and Hz recorded. | |
| **1.2** | T-00:05 | Field Electrician | **EXECUTE:** Open Main Utility Circuit Breakers (52-U1 and 52-U2) via remote control interface. | Catastrophic drop in voltage on the main utility busbar. | |
| **1.3** | T-00:06 | Safety Watcher | Verify critical computing loads on the floor remain energized. | UPS strings seamlessly step into battery discharge mode; 0ms phase angle shift. | DC Voltage: _____ V |
| **1.4** | T-00:12 | Gen Operator | Monitor generator engine block cranks and voltage escalation. | All generators fire; voltage and frequency stabilize at nominal ratings (e.g., 4160V / 60Hz). | Generator RPM: _____ |
| **1.5** | T-00:20 | Field Electrician | Verify Automatic Transfer Switch (ATS) and Paralleling Switchgear close into generator bus. | Generator breakers close; emergency power distribution line is re-energized. | Bus Frequency: _____ Hz |
| **1.6** | T-00:45 | Control Room Eng | Monitor BMS mechanical equipment re-start logic. | Chillers, secondary CHW pumps, and CRAH fans execute staggered sequencing to prevent current inrush spikes. | Chiller Amps: _____ A |
| **1.7** | T-01:30 | Mechanical Eng | Confirm chilled water loop temperature stabilization. | Control valves modulate cleanly; transient thermal loop stabilizes within safe operational bounds. | Loop Temp: _____ °F |

---

## 5. Restoration & Return to Normal Operations (RNO)
Following successful data capture under generator power, return the facility to stable utility configuration:

1. **Verify Utility Health:** Ensure utility grid voltage and frequency have returned to normal tolerances for at least 15 continuous minutes.
2. **Synchronize Buses:** Initiate closed-transition (make-before-break) re-transfer via EPMS to line up utility power without dropping load.
3. **Open Generator Breakers:** Once utility utility breakers are securely closed, open generator tie breakers.
4. **Engine Cooldown:** Allow generators to run un-loaded for a 5-minute cool-down cycle before reverting to automatic standby readiness state.
5. **System Sign-Off:** Review the master logs for any transient deviations, sign off the MOP sheet, and log the test inside CxAlloy.
