# datacenter-commissioning-templates
L4 Functional and L5 Integrated Systems Testing templates for critical data center infrastructure
# Data Center Commissioning (Cx) Document Templates 🚀

This repository hosts professional documentation templates for Level 4 (L4) Functional Performance Testing and Level 5 (L5) Integrated Systems Testing (IST). These frameworks ensure zero open defects and robust system reliability before facility handover.

---

## 📋 1. Level 4 (L4) Functional Performance Testing Script
**Equipment Tag:** CH-01 (Centrifugal Chiller Plant)  
**Prerequisites Check:** 
- [ ] L3 Factory Startup Reports Approved
- [ ] NETA Electrical Test Sheets Signed Off
- [ ] TAB (Testing, Adjusting, Balancing) Report Completed
- [ ] 0 Open Priority-1 Issues in Cx Master Log

### Test Sequence & Operational Verification

| Step | Test Procedure / Operational Command | Expected Engineering Response | Result (P/F) | Comments / Measurements |
| :--- | :--- | :--- | :---: | :--- |
| **4.1** | Verify BMS communication with chiller controller. | Real-time telemetry (temperatures, flow rates, setpoints) visible on BMS. | | |
| **4.2** | Initiate local manual start-up sequence. | Oil pump starts; purge cycle completes; compressor ramps up cleanly without surge. | | |
| **4.3** | Command Chilled Water Control Valve (CHW-V) to 50% open via BMS. | Valve actuator modulates to 50% travel; flow meter registers proportional GPM. | | Temp: ____ °F |
| **4.4** | Simulate a high condenser water temperature fault signal. | Chiller controller generates critical alarm; unit executes controlled safety shutdown. | | Alarm Code: ____ |

---

## ⚡ 2. Level 5 (L5) Integrated Systems Testing (IST) Protocol
**Objective:** Validate whole-facility failover and concurrent maintainability under maximum design thermal load utilizing temporary load banks.

### Scenario: Full Utility Blackout & Generator Synchronization

*   **Pre-Test State:** Facility running on normal Utility Power Grid A and Grid B. Chiller plants operating under active 100% load bank simulation.
*   **Execution Step:** Simulate an instantaneous, unannounced loss of all incoming utility power.

#### Sequence of Operations (SOO) Verification Checklist:
- [ ] **0 to 2 Seconds:** Uninterruptible Power Supply (UPS) systems seamlessly pick up all critical information technology and BMS control loads without dropping voltage.
- [ ] **0 to 10 Seconds:** Emergency Standby Generators receive start signals, ramp up to rated speed, and stabilize output voltage and frequency.
- [ ] **12 Seconds:** Automatic Transfer Switches (ATS) throw over; Generator Paralleling Switchgear synchronizes buses and begins stepped load blocks.
- [ ] **60 Seconds:** Mechanical re-start logic initiates; Chiller pumps restart under generator power, and control valves modulate to maintain transient thermal loops.

---

## 🛠️ Usage
These markdown formats are optimized for direct translation into digital commissioning software databases (e.g., CxAlloy Test Templates) or for conversion into localized field execution guides.
