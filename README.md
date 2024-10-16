#  FAULT TOLERANCE MECHANISMS FOR SPACECRAFTS

---

<details>
  
  ## Team Details

- **Semester**: 3rd Sem B. Tech. CSE
- **Section**: S2
- **Team ID**: 11

### Team Members:
1. **Aalima Khan**, Roll No: 231CS201, [Email](mailto:aalimakhan.231cs217@nitk.edu.in)
2. **Basitha Sadipirala**, Roll No: 231CS251, [Email](mailto:basithasadipirala.231cs251@nitk.edu.in)
3. **Bukke Lahari**, Roll No: 231CS217, [Email](mailto:laharinaik.231cs217@nitk.edu.in)

  
  
</details>

---

<Verilog>
  <summary>Abstract</summary>
  
 
  -[click here](https://github.com/Lahari-Naik/S2-TEAM_11-MINIPROJECT/blob/main/Snapshots/Fault%20Tolerance%20in%20Spacecrafts(ABSTRACT).pdf) 
</details>

---
<details>
  <summary>Flowchart</summary>
  
  ![Flowchart referred for project](https://github.com/Lahari-Naik/S2-TEAM_11-MINIPROJECT/blob/main/Snapshots/TechnicalArchitecture.png) 
  
</details>

---
<details>
  <summary>Functional Block Diagram</summary>
  
  
  
  ![Functional Block Diagram](https://github.com/Lahari-Naik/S2-TEAM_11-MINIPROJECT/blob/main/Snapshots/BLOCK%20DIAGRAM.jpg) 
  

  
</details>

---

<details>
  <summary>Working</summary>
  
  -[click here](https://github.com/Lahari-Naik/S2-TEAM_11-MINIPROJECT/blob/main/Snapshots/WORKING.pdf)
  
</details>

---

<details>
  <summary>Logisim</summary>
  
  
  
  
  MAIN CIRCUIT![Logisim Final Circuit Diagram](https://github.com/Lahari-Naik/S2-TEAM_11-MINIPROJECT/blob/main/Logisim/Circuit%20%20Images/S2-T11.png)
  ![LEVEL 1 Circuit Diagram](https://github.com/Lahari-Naik/S2-TEAM_11-MINIPROJECT/blob/main/Logisim/Circuit%20%20Images/Level1Image.png)
  ![LEVEL 2 Circuit Diagram](https://github.com/Lahari-Naik/S2-TEAM_11-MINIPROJECT/blob/main/Logisim/Circuit%20%20Images/Level2Image.png)
  ![LEVEL 3 Circuit Diagram](https://github.com/Lahari-Naik/S2-TEAM_11-MINIPROJECT/blob/main/Logisim/Circuit%20%20Images/Level3.Image.png)
  ![LFSR Circuit Diagram](https://github.com/Lahari-Naik/S2-TEAM_11-MINIPROJECT/blob/main/Logisim/Circuit%20%20Images/LFSRImage.png)
  
  - [Brief description about logisim circuit](https://github.com/Lahari-Naik/S2-TEAM_11-MINIPROJECT/blob/main/Logisim/Design-Logisim.pdf)
  - [Download LFSR Circuit](https://github.com/Lahari-Naik/S2-TEAM_11-MINIPROJECT/blob/main/Logisim/Circuit/LFSR.circ)
  - [Download Level 1 Circuit](https://github.com/Lahari-Naik/S2-TEAM_11-MINIPROJECT/blob/main/Logisim/Circuit/level1.circ)
  - [Download Level 2 Circuit](https://github.com/Lahari-Naik/S2-TEAM_11-MINIPROJECT/blob/main/Logisim/Circuit/level2.circ)
  - [Download Level3 Circuit](https://github.com/Lahari-Naik/S2-TEAM_11-MINIPROJECT/blob/main/Logisim/Circuit/level3.circ)
  - [Download Logisim Final Circuit](https://github.com/Lahari-Naik/S2-TEAM_11-MINIPROJECT/blob/main/Logisim/Circuit/S2-T11.circ)
  
</details>

---

<details>
  
  
- [S2-T11-data.v](https://github.com/Lahari-Naik/S2-TEAM_11-MINIPROJECT/blob/main/Verilog/S2-T11-data.v)
- [S2-T11_tb.v](https://github.com/Lahari-Naik/S2-TEAM_11-MINIPROJECT/blob/main/Verilog/S2-T11_tb.v)
- Usage:
- To run the program, execute commands in the terminal:

```bash
iverilog -o dds S2-T11_tb.v S2-T11-data.v
```

```bash
vvp dds
```

### Output-1
  
```bash
Level 1 Inputs: R1L1=1 R2L1=0 R3L1=0 R4L1=0 R5L1=1 EL1=11110
Level 1 Passed: O1L1=1 O2L1=1 O3L1=1 O4L1=1 O5L1=1
Level 2 running...
Level 2 Inputs: R1L2=1 R2L2=1 R3L2=0 R4L2=0 R5L2=0 EL2=11100
User chose not to switch off the 4th bit. O4L2=0
Level 2 Passed: O1L2=1 O2L2=1 O3L2=1 O4L2=0 O5L2=0
Level 3 running...
Level 3 Inputs: R1L3=1 R2L3=1 R3L3=0 R4L3=0 R5L3=0 EL3=11000
User chose not to switch off the 3rd bit. O3L3=0
User asked to switch off 4th bit. O4L3 set to 0.
Level 3 Passed: O1L3=1 O2L3=1 O3L3=0 O4L3=0 O5L3=0
MISSION SUCCESSFUL!
  
-----------------------------
```

### Output-2
```bash
Level 1 Inputs: R1L1=0 R2L1=1 R3L1=1 R4L1=0 R5L1=0 EL1=11110
Level 1 Failed!
MISSION ABORTED!

-----------------------------
```
### Output-3
```bash
Level 1 Inputs: R1L1=1 R2L1=0 R3L1=1 R4L1=1 R5L1=0 EL1=11110
Level 1 Passed: O1L1=1 O2L1=1 O3L1=1 O4L1=1 O5L1=0
Level 2 running...
Level 2 Inputs: R1L2=1 R2L2=1 R3L2=0 R4L2=1 R5L2=1 EL2=11100
User asked to switch off 4th bit. O4L2 set to 0.
Level 2 Passed: O1L2=1 O2L2=1 O3L2=1 O4L2=0 O5L2=1
Level 3 running...
Level 3 Inputs: R1L3=1 R2L3=1 R3L3=0 R4L3=1 R5L3=1 EL3=11000
User asked to switch off 3rd bit. O3L3 set to 0.
User asked to switch off 4th bit. O4L3 set to 0.
Level 3 Passed: O1L3=1 O2L3=1 O3L3=0 O4L3=0 O5L3=1
MISSION SUCCESSFUL!

-----------------------------
```
</details>

---
 <details> <summary>References</summary>


- [Link 1](https://ntrs.nasa.gov/api/citations/20210020739/downloads/FinalCopy.pdf/)
- [Link 2](https://www.isro.gov.in/spacesciexp.html/)
- [Link 3](https://www.esa.int/Space_Safety/Hera/Fault_detection_isolation_and_recovery/)
- [Link 4](https://iopscience.iop.org/article/10.1088/1742-6596/2762/1/012064/pdf/)
- [Link 5](https://www.spacenavigators.com/post/fault-detection-and-recovery-in-satellite-aocs-ensuring-resilience-in-space/)



</details>

---



  

