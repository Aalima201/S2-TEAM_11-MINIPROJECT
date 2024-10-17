#  FAULT TOLERANCE MECHANISMS FOR SPACECRAFTS

<!-- First Section -->
## Team Details
<details>
  <summary>Details</summary>
- **Semester**: 3rd Sem B. Tech. CSE
- **Section**: S2
- **Team ID**: 11

1. **Aalima Khan**, Roll No: 231CS201, [Email](mailto:aalimakhan.231cs217@nitk.edu.in)
2. **Basitha Sadipirala**, Roll No: 231CS251, [Email](mailto:basithasadipirala.231cs251@nitk.edu.in)
3. **Bukke Lahari**, Roll No: 231CS217, [Email](mailto:laharinaik.231cs217@nitk.edu.in)
</details>
<!-- Second Section -->

## Abstract
<details>
  <summary>Details</summary>

  ### Motivation:
  Our fascination with space exploration drives this project, aiming to ensure
  high reliability in extreme and remote environments. Developing a fault-tolerant system for
  spacecraft is critical for maintaining mission continuity despite subsystem failures, minimizing
  human intervention, and safeguarding astronaut safety. Historical mission challenges, such as
  Apollo 13 and the James Webb Space Telescope, emphasize the need for robust fault-tolerant
  systems in future missions.
### Problem Statement:
The goal of this project is to design a multi-layered digital circuit-
based fault diagnosis and recovery system. This system will employ a hierarchical approach,
where subsystems are organized into levels based on their criticality to the spacecraft’s mis-
sion. A level-by-level verification ensures that critical subsystems are diagnosed and recovered
efficiently to minimize mission disruption.
### Key components:
• Basic Logic gates 
>
• MUX(2x1)
>
• Shifters
>
• D-Flip Flops
>
• LEDs
### Features:
• A layered approach ensures that critical subsystems are prioritized in diagnosis and re-
covery, minimizing the overall recovery time.
>
• Built-in error detection mechanisms ensure system self-correction without human inter-
vention.
>
• Users can decide whether to activate non-crucial subsystems, with the ideal scenario being
that these subsystems are turned off.
>
• A predefined recovery plan ensures the mission continues only if all subsystems in every
level pass, and the mission will terminate upon any critical failure.
</details>
<!-- Third Section -->

## Block Diagram
<details>
  <summary>Details</summary>
  
  
  
  ![Functional Block Diagram](https://github.com/Lahari-Naik/S2-TEAM_11-MINIPROJECT/blob/main/Snapshots/BLOCK%20DIAGRAM.jpg) 
  

  
</details>
<!-- Fourth Section -->

## Working
<details>
  <summary>Details</summary>
  
  ### System Architecture:
 #### Level 1:Base Layer
 – Subsystems: Advanced Sensors, Data Acquisition and Analysis, Advanced Materials, Device
 Failure Physics, Thermal Regulation.
 >
 – Thesystem will first focus on diagnosing and recovering these subsystems to ensure the
 spacecraft’s baseline functionality. One subsystem in this level is crucial but uncorrectable; if this
 subsystem fails, the mission will terminate immediately. Passing Level 1 is mandatory for the
 mission to proceed to the next level.
 #### Level 2: Functional Module Implementation Layer
 – Subsystems: Power Status Monitoring, Attitude Control, Load Monitoring, Measure- ment
 Control, Communications Integrity.
 >
 – If Level 1 is passed, this layer ensures that subsystems crucial for spacecraft stability, control,
 and communication are fully operational. One subsystem in this layer is uncorrectable, and if it
 fails, the mission will terminate.
 #### Level 3: Task Goal Implementation Layer
 – Subsystems: Fault Detection, Fault Isolation, Fault Prediction, Health Assessment, Repair
 Planning.
 >
 – This final level assesses and ensures fault detection and health management systems are functioning.
 The same condition applies—one uncorrectable subsystem must pass, and failure will lead to mission
 termination.
 #### Non-Critical Subsystems:
 These subsystems, although not essential for the core space- craft operations,
 can be monitored and toggled based on the user’s discretion. In an ideal operational scenario, all
 non-crucial subsystems are turned off to conserve resources. Fail- ures in non-crucial subsystems are
 tolerated.
### Mission Termination Conditions:
 ● Ifanycrucial subsystem, particularly the uncorrectable ones in each level, fails to recover, the
 mission will terminate immediately.
 >
 ● Progression to the next level occurs only if all crucial subsystems in the current level are
 functional. Failure to pass any level results in mission termination.
 >
 ● Forthemission to succeed, all levels must be passed.
### Truth Tables:
 #### LEVEL1:
 ##### Reason for “!!”
 In level 1, since the first bit (R1) is 0, the enable signal for R2 also becomes 0, causing the multiplexer
 (MUX) for R2 not to function, and it outputs an indeterminate signal (x). This "x" signal is mixed, meaning
 it could be either 0 or 1, which leads to uncertainty and triggers an error (indicated by a red line). As a
 result, the MUX for the third bit will also fail, and the same logic applies to the fourth bit. This issue carries
 forward to subsequent levels as well.Hence, mission fails.
 >
 Since the system checks each bit individually, any failure to correct bits to match the expected values will
 prevent further checks on crucial subsystems. Therefore, the process will halt if the corrected bits do not
 meet the expected conditions.
#### LEVEL 2:
 ##### Reason for “!!”
 Unlike in Level 1, in Level 2, we give the user the option to decide whether to switch off the non-crucial
 subsystem (R4). However, this user interaction is only possible if the outputs O1, O2, and O3 match the
 expected bits. This ensures that only after verifying the crucial subsystems can the user be asked about
 the non-crucial subsystem's status.
### LEVEL 3:
#### Reason for “!!”
 In Level 3, there are two non-crucial subsystems (R3 and R4), so the user is asked whether they want to
 switch off both non-crucial subsystems. The interesting point here is that if the user denies switching off
 R3 (via switch1) but permits switching off R4 (via switch2), the output O4 still won’t change. This is
 because O4 depends on R3, and since the system checks each bit individually, the behavior of R4 alone
 won’t override the decision for R3.
#### Note:
R5 is a non-essential subsystem and operates independently of the other bits. Therefore, its status
 does not affect the outcomes or dependencies related to the other subsystems.
 MULTIPLEXER(2 X 1)
### STATE DIAGRAM:
 S:Before correction
 >
 C:After correction
### STATE EQUATIONS:– 
#### Multiplexer:
 Y =E.(S0’.I0+S0.I1)
 #### Level 1:
 Level1_passed = O1.O2.O3.O4 
 #### Level 2:
Level2_passed = O1.O2.O3
#### Level 3:
 Level3_passed = O1.O2
</details>
<!-- Fifth Section -->

## Logisim
<details>
  <summary>Logisim</summary>
  
  
  
  
  ### MAIN CIRCUIT
  ![Logisim Final Circuit Diagram](https://github.com/Lahari-Naik/S2-TEAM_11-MINIPROJECT/blob/main/Logisim/Circuit%20%20Images/S2-T11.png)
 ### LEVEL 1
 ![LEVEL 1 Circuit Diagram](https://github.com/Lahari-Naik/S2-TEAM_11-MINIPROJECT/blob/main/Logisim/Circuit%20%20Images/Level1Image.png)
### LEVEL 2
![LEVEL 2 Circuit Diagram](https://github.com/Lahari-Naik/S2-TEAM_11-MINIPROJECT/blob/main/Logisim/Circuit%20%20Images/Level2Image.png)
### LEVEL 3
![LEVEL 3 Circuit Diagram](https://github.com/Lahari-Naik/S2-TEAM_11-MINIPROJECT/blob/main/Logisim/Circuit%20%20Images/Level3.Image.png)
### LFSR 
![LFSR Circuit Diagram](https://github.com/Lahari-Naik/S2-TEAM_11-MINIPROJECT/blob/main/Logisim/Circuit%20%20Images/LFSRImage.png)
  
  - [Brief description about logisim circuit](https://github.com/Lahari-Naik/S2-TEAM_11-MINIPROJECT/blob/main/Logisim/Design-Logisim.pdf)
  - [Download LFSR Circuit](https://github.com/Lahari-Naik/S2-TEAM_11-MINIPROJECT/blob/main/Logisim/Circuit/LFSR.circ)
  - [Download Level 1 Circuit](https://github.com/Lahari-Naik/S2-TEAM_11-MINIPROJECT/blob/main/Logisim/Circuit/level1.circ)
  - [Download Level 2 Circuit](https://github.com/Lahari-Naik/S2-TEAM_11-MINIPROJECT/blob/main/Logisim/Circuit/level2.circ)
  - [Download Level3 Circuit](https://github.com/Lahari-Naik/S2-TEAM_11-MINIPROJECT/blob/main/Logisim/Circuit/level3.circ)
  - [Download Logisim Final Circuit](https://github.com/Lahari-Naik/S2-TEAM_11-MINIPROJECT/blob/main/Logisim/Circuit/S2-T11.circ)
  
</details>

<!-- Sixth Section -->

## Verilog
<details>
  <summary>Verilog</summary>
  

- [S2-T11-data.v](https://github.com/Lahari-Naik/S2-TEAM_11-MINIPROJECT/blob/main/Verilog/S2-T11-data.v)
- [S2-T11-gate.v](https://github.com/Lahari-Naik/S2-TEAM_11-MINIPROJECT/blob/main/Verilog/S2-T11-gate.v)
- [S2-T11_tb.v](https://github.com/Lahari-Naik/S2-TEAM_11-MINIPROJECT/blob/main/Verilog/S2-T11_tb.v)
  ### Output
![S2-T11(output).png](https://github.com/Lahari-Naik/S2-TEAM_11-MINIPROJECT/blob/main/Verilog/S2-T11(output).png)
### Usage
- To run the program, execute commands in the terminal:

```bash
iverilog -o dds S2-T11_tb.v S2-T11-data.v
```

```bash
vvp dds
```

</details>

<!-- Seventh Section -->

## References
 <details> <summary>References</summary>


- [Link 1](https://ntrs.nasa.gov/api/citations/20210020739/downloads/FinalCopy.pdf/)
- [Link 2](https://www.isro.gov.in/spacesciexp.html/)
- [Link 3](https://www.esa.int/Space_Safety/Hera/Fault_detection_isolation_and_recovery/)
- [Link 4](https://iopscience.iop.org/article/10.1088/1742-6596/2762/1/012064/pdf/)
- [Link 5](https://www.spacenavigators.com/post/fault-detection-and-recovery-in-satellite-aocs-ensuring-resilience-in-space/)



</details>

# S2-TEAM_11-MINIPROJECT

---



  

