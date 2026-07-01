# Smart-Conveyor-Sorting-System

<img width="327" height="317" alt="image" src="https://github.com/user-attachments/assets/144ed8e4-e107-4d85-b3ac-f259f68628ee" />

## 📌 Overview
This project features a laboratory-scale, automated conveyor-based material sorting system engineered to detect, classify, and divert objects into designated collection bins based on their material composition (metallic vs. non-metallic). The system utilizes a multi-sensor array and pneumatic actuation, all governed by a Siemens SIMATIC S7-1200 Programmable Logic Controller (PLC) using standard Ladder Logic.

## ✨ Key Features
* **Multi-Sensor Classification:** Utilizes a sequential interrogation process using through-beam photoelectric, inductive, and capacitive sensors to accurately distinguish between metallic and non-metallic objects.
* **Pneumatic Sorting Mechanism:** Features double-acting pneumatic cylinders controlled by 5/2 solenoid-actuated Directional Control Valves (DCVs) for precise, high-speed object ejection.
* **Fail-Safe Motor Control:** A 12V DC geared motor is controlled via a 24V electromagnetic relay interfaced with the PLC, ensuring the conveyor halts safely during inspection or power faults.
* **Industrial-Grade Logic:** Programmed in Siemens TIA Portal V17 using IEC 61131-3 compliant Ladder Diagram (LAD) language, featuring edge-triggered detection, retentive latches, and staggered timing for sequenced actuation.

## 🛠️ Hardware Specifications
* **Programmable Logic Controller (PLC):** Siemens SIMATIC S7-1200 CPU 1214C DC/DC/DC
* **Sensors:** * Omron E3JK-TP12 2M (Through-Beam Photoelectric) - Object presence
  * Omron E2B-M18KN10-WP-C1 2M (Inductive Proximity) - Metal detection
  * Pepperl+Fuchs CBB4-12GH70-E2 (Capacitive Proximity) - Non-metal detection
* **Pneumatics:** Double-Acting Cylinders, 5/2 Solenoid Spring-Return DCVs, FRL (Filter-Regulator-Lubricator) Unit, Pressure Regulator, Manifold Distributor, Meter-out Flow Control Valves
* **Motor & Drive:** 12V DC Geared Motor, 24V DC Electromagnetic Relay Module

---


### System Block Diagram & Control Flow
<img width="1024" height="1536" alt="FLow" src="https://github.com/user-attachments/assets/d27b85a5-5f8e-4c1a-ae73-0c7c7590bb51" />




### Project Demonstration


https://github.com/user-attachments/assets/26d0b03b-d8f1-410b-88b9-2181918b8c7d


---

## 🚀 How to Operate

1. **System Initialization:** Power on the PLC (RUN mode) and ensure the pneumatic compressor is supplying regulated air (3-5 bar) through the FRL unit.
2. **Detection & Halt:** Place an object on the moving conveyor. The through-beam sensor detects the object's presence, triggering a 2-second conveyor halt for inspection.
3. **Material Classification:** * If the **Inductive Sensor** triggers, the object is classified as **Metallic**.
   * If the object bypasses the inductive sensor and triggers the **Capacitive Sensor**, it is classified as **Non-Metallic**.
4. **Pneumatic Ejection:** Based on the classification, the PLC executes precise delay timers (3,700 ms for metal, 2,300 ms for non-metal) before firing the respective solenoid valve to extend the pneumatic cylinder.
5. **Auto-Reset:** After ejection, the cylinder retracts, the station clears its memory latches, and the conveyor readies for the next object.

## 🔮 Future Enhancements
* **Computer Vision Integration:** Implementing semantic classification using camera systems and AI (e.g., YOLOv8) for complex sorting beyond basic material composition.
* **SCADA Connectivity:** Utilizing the PLC's PROFINET interface for plant-level monitoring and telemetry data collection.
* **HMI Deployment:** Adding a supervisory touch panel to allow operators to adjust timer setpoints and monitor system diagnostics without reprogramming the PLC.

## 🤝 Author
@Enavamsi
