#  FAULT TOLERANCE MECHANISMS FOR SPACECRAFTS

<!-- First Section -->
## Team Details
<details>
  <summary>Details</summary>
  
 > Semester: 3rd Sem B. Tech. CSE
> 
 > Section: S2
> 
 > Team ID: 11

> **Aalima Khan**, Roll No: 231CS201, [Email](mailto:aalimakhan.231cs217@nitk.edu.in)
  >
>  **Basitha Sadipirala**, Roll No: 231CS251, [Email](mailto:basithasadipirala.231cs251@nitk.edu.in)
  >
> **Bukke Lahari**, Roll No: 231CS217, [Email](mailto:laharinaik.231cs217@nitk.edu.in)
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
 ![LEVEL 1 Truth Table](https://github.com/Lahari-Naik/S2-TEAM_11-MINIPROJECT/blob/5038f85f8502d3ce026e76fb4331a6c2a4f57278/Snapshots/LEVEL%201%20truth%20table.png)
>
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
  ![LEVEL 2 Truth Table](https://github.com/Lahari-Naik/S2-TEAM_11-MINIPROJECT/blob/d5dbd00d0816aa6d73802d84444027deada1ee63/Snapshots/LEVEL%202%20truth%20table.png)
  >
 Unlike in Level 1, in Level 2, we give the user the option to decide whether to switch off the non-crucial
 subsystem (R4). However, this user interaction is only possible if the outputs O1, O2, and O3 match the
 expected bits. This ensures that only after verifying the crucial subsystems can the user be asked about
 the non-crucial subsystem's status.
### LEVEL 3:
#### Reason for “!!”
 ![LEVEL 3 Truth Table](https://github.com/Lahari-Naik/S2-TEAM_11-MINIPROJECT/blob/d5dbd00d0816aa6d73802d84444027deada1ee63/Snapshots/LEVEL%203%20truth%20table.png)
 >
 In Level 3, there are two non-crucial subsystems (R3 and R4), so the user is asked whether they want to
 switch off both non-crucial subsystems. The interesting point here is that if the user denies switching off
 R3 (via switch1) but permits switching off R4 (via switch2), the output O4 still won’t change. This is
 because O4 depends on R3, and since the system checks each bit individually, the behavior of R4 alone
 won’t override the decision for R3.
#### Note:
R5 is a non-essential subsystem and operates independently of the other bits. Therefore, its status
 does not affect the outcomes or dependencies related to the other subsystems.
 MULTIPLEXER(2 X 1)
 ![MUX Truth Table](https://github.com/Lahari-Naik/S2-TEAM_11-MINIPROJECT/blob/d5dbd00d0816aa6d73802d84444027deada1ee63/Snapshots/MUX%20truth%20table.png)
 >
 E: Enable
>
S0: Select line
>
I0 : Input 0
>
I1 : Input 1
>
Y : Output
 ### STATE DIAGRAM:
  ![State Diagram](https://github.com/Lahari-Naik/S2-TEAM_11-MINIPROJECT/blob/d5dbd00d0816aa6d73802d84444027deada1ee63/Snapshots/State%20Diagram.png)
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
  <summary>Details</summary>
  
  ### MAIN CIRCUIT
  ![Logisim Final Circuit Diagram](https://github.com/Lahari-Naik/S2-TEAM_11-MINIPROJECT/blob/8e1ba9abdda0ab817e440630d3c362b70373aa4b/Logisim/Circuit%20%20Images/S2_T11.png)
 ### LEVEL 1
 ![LEVEL 1 Circuit Diagram](https://github.com/Lahari-Naik/S2-TEAM_11-MINIPROJECT/blob/93e3db98ab9dd1d500044b6fea50d4d26e5bf897/Logisim/Circuit%20%20Images/Level_1.png)
### LEVEL 2
![LEVEL 2 Circuit Diagram](https://github.com/Lahari-Naik/S2-TEAM_11-MINIPROJECT/blob/93e3db98ab9dd1d500044b6fea50d4d26e5bf897/Logisim/Circuit%20%20Images/Level_2.png)
### LEVEL 3
![LEVEL 3 Circuit Diagram](https://github.com/Lahari-Naik/S2-TEAM_11-MINIPROJECT/blob/93e3db98ab9dd1d500044b6fea50d4d26e5bf897/Logisim/Circuit%20%20Images/Level_3.png)
### LFSR 
![LFSR Circuit Diagram](https://github.com/Lahari-Naik/S2-TEAM_11-MINIPROJECT/blob/ae2bf319d1035249d6a33df3a0c4ef46da57df98/Logisim/Circuit%20%20Images/LFSR.png)
  
</details>

<!-- Sixth Section -->

## Verilog
<details>
  <summary>Details</summary>
  
  ### Gate Flow
    module lfsr_5bit (
    input clk,    // Clock input
    input rst,    // Reset input
    output reg [4:0] lfsr_out  // 5-bit output
    );

    wire feedback;

    // Feedback is taken from bits 5 and 3 (tap positions 4 and 2 in Verilog, 0-indexed)
    assign feedback = ~(lfsr_out[4] ^ lfsr_out[2]); 

    always @(posedge clk or posedge rst) begin
        if (rst) begin
            // On reset, set LFSR to a non-zero seed value
            lfsr_out <= 5'b00001;
        end else begin
            // Shift the LFSR and insert the feedback bit at position 4
            lfsr_out <= {lfsr_out[3:0], feedback};
        end
    end

    endmodule
    module level1(
    input wire R1, R2, R3, R4, R5,       // R : Random Input bits
    input wire E1, E2, E3, E4, E5,       // E : Expected Output bits
    output wire O1, O2, O3, O4, O5,      // O : Actual Output bits
    output wire LEVEL1_PASSED            // Equals to one if Level 1 is passed
    );
    wire notE5, x2, R2S0, R2E, MUXR2,notR2_eq_E1;
    wire x3, R3S0, R3E, MUXR3;
    wire x4, R4S0, R4E, MUXR4;

    // Not gate for E5
    not(notE5, E5);

    // Assign expected outputs
    assign E1 = 1;
    assign E2 = 1;
    assign E3 = 1;
    assign E4 = 1;
    assign E5 = 0;

    // Output O1 is directly R1
    assign O1 = R1;

    // Logic for R2
    wire R2_eq_E1; // R2 should match E1
    xor(R2_eq_E1, R1, E1);
    not(notR2_eq_E1,R2_eq_E1);
    and(x2, R2, notR2_eq_E1); // x2 = R2 & ~ (R1 ^ E1)
    xor(R2S0, x2, E2);
    and(R2E, notR2_eq_E1, 1'b1); // R2E = ~(R1 ^ E1)
    assign MUXR2 = (R2E) ? (R2S0 ? E2 : x2) : 1'b0; // MUX for R2 correction
    assign O2 = MUXR2;

    // Logic for R3
    wire R3_and_MUXR2;
    and(R3_and_MUXR2, R3, MUXR2);
    xor(R3S0, R3_and_MUXR2, E3);
    and(R3E, MUXR2, 1'b1); // R3E = MUXR2
    assign MUXR3 = (R3E) ? (R3S0 ? E3 : R3_and_MUXR2) : 1'b0; // MUX for R3 correction
    assign O3 = MUXR3;

    // Logic for R4
    wire R4_and_MUXR3;
    and(R4_and_MUXR3, R4, MUXR3);
    xor(R4S0, R4_and_MUXR3, E4);
    and(R4E, MUXR3, 1'b1); // R4E = MUXR3
    assign MUXR4 = (R4E) ? (R4S0 ? E4 : R4_and_MUXR3) : 1'b0; // MUX for R4 correction
    assign O4 = MUXR4;

    // Output O5 is directly R5 (non-essential subsystem)
    assign O5 = R5;

    // Passing condition for Level 1
    assign LEVEL1_PASSED = O1 & O2 & O3 & O4; 

    endmodule
    module level2(
    input wire clk,          // Clock input
    input wire rst,          // Reset input
    input wire E1L2, E2L2, E3L2, E4L2, E5L2, // E: Expected Output bits
    input wire SWITCH1L2,    // Switch input for controlling R4L2
    output wire O1L2, O2L2, O3L2, O4L2, O5L2, // O: Actual Output bits
    output wire LEVEL2_PASSED, // Equals 1 if Level 2 is passed
    output wire userR4L2     // Output for turning on/off subsystem R4
    );

    wire [4:0] lfsr_out;    // Output from the LFSR
    wire R1L2, R2L2, R3L2, R4L2, R5L2; // Random input bits taken from LFSR output

    // Instantiate the LFSR module (assumed)
    lfsr_5bit lfsr_inst (
        .clk(clk),
        .rst(rst),
        .lfsr_out(lfsr_out)
    );

    // Assign LFSR outputs to the random input bits
    assign R1L2 = lfsr_out[0];
    assign R2L2 = lfsr_out[1];
    assign R3L2 = lfsr_out[2];
    assign R4L2 = lfsr_out[3];
    assign R5L2 = lfsr_out[4];

    wire notE5, x2, R2S0, R2E, MUXR2,notR2_eq_E1L2;
    wire x3, R3S0, R3E, MUXR3;
    wire x4, R4S0, R4E, MUXR4;

    // Not gate for E5L2
    not(notE5, E5L2);

    // Assign expected outputs
    assign E1L2 = 1;
    assign E2L2 = 1;
    assign E3L2 = 1;
    assign E4L2 = 0;
    assign E5L2 = 0;

    // Output O1L2 is directly R1L2
    assign O1L2 = R1L2;

    // Logic for R2L2
    wire R2_eq_E1L2;
    xor(R2_eq_E1L2, R1L2, E1L2);
    not(notR2_eq_E1L2,R2_eq_E1L2);
    and(x2, R2L2,notR2_eq_E1L2); // x2 = R2L2 & ~ (R1L2 ^ E1L2)
    xor(R2S0, x2, E2L2);
    and(R2E,notR2_eq_E1L2, 1'b1); // R2E = ~(R1L2 ^ E1L2)
    assign MUXR2 = (R2E) ? (R2S0 ? E2L2 : x2) : 1'b0; // MUX for R2 correction
    assign O2L2 = MUXR2;

    // Logic for R3L2
    wire R3_and_MUXR2;
    and(R3_and_MUXR2, R3L2, MUXR2);
    xor(R3S0, R3_and_MUXR2, E3L2);
    and(R3E, MUXR2, 1'b1); // R3E = MUXR2
    assign MUXR3 = (R3E) ? (R3S0 ? E3L2 : R3_and_MUXR2) : 1'b0; // MUX for R3 correction
    assign O3L2 = MUXR3;

    // Logic for R4L2
    wire R4_and_MUXR3;
    and(R4_and_MUXR3, R4L2, MUXR3);
    xor(R4S0, R4_and_MUXR3, E4L2);
    and(R4E, SWITCH1L2, 1'b1); // R4E = SWITCH1L2
    assign MUXR4 = (R4E) ? (R4S0 ? E4L2 : R4_and_MUXR3) : 1'b0; // MUX for R4 correction
    assign O4L2 = MUXR4;

    // Output O5L2 is directly R5L2
    assign O5L2 = R5L2;

    // Condition for R4L2 if the user wants to switch the subsystem off
    assign userR4L2 = SWITCH1L2 ? 1 : 0;
    assign O4L2 = userR4L2 ? 0 : R4L2;

    // Passing condition for Level 2
    assign LEVEL2_PASSED = O1L2 & O2L2 & O3L2;

    endmodule
    module level3(
    input wire clk,          // Clock input
    input wire rst,          // Reset input
    input wire E1L3, E2L3, E3L3, E4L3, E5L3,  // E: Expected Output bits
    input wire SWITCH1L3,    // Switch input for controlling R4L3
    input wire SWITCH2L3,    // Switch input for controlling R3L3
    output wire O1L3, O2L3, O3L3, O4L3, O5L3, // O: Actual Output bits
    output wire LEVEL3_PASSED, // Equals 1 if Level 3 is passed
    output wire userR4L3,     // Output for turning on/off subsystem R4
    output wire userR3L3      // Output for turning on/off subsystem R3
    );

    wire [4:0] lfsr_out;    // Output from the LFSR
    wire R1L3, R2L3, R3L3, R4L3, R5L3; // Random input bits taken from LFSR output

    // Instantiate the LFSR module (assumed)
    lfsr_5bit lfsr_inst (
        .clk(clk),
        .rst(rst),
        .lfsr_out(lfsr_out)
    );

    // Assign LFSR outputs to the random input bits
    assign R1L3 = lfsr_out[0];
    assign R2L3 = lfsr_out[1];
    assign R3L3 = lfsr_out[2];
    assign R4L3 = lfsr_out[3];
    assign R5L3 = lfsr_out[4];

    wire notE5, x2, R2S0, R2E, MUXR2,notR2_eq_E1L3;
    wire x3, R3S0, R3E, MUXR3;
    wire x4, R4S0, R4E, MUXR4;

    // Not gate for E5L3
    not(notE5, E5L3);

    // Assign expected outputs
    assign E1L3 = 1;
    assign E2L3 = 1;
    assign E3L3 = 1;
    assign E4L3 = 0;
    assign E5L3 = 0;

    // Output O1L3 is directly R1L3
    assign O1L3 = R1L3;

    // Logic for R2L3
    wire R2_eq_E1L3;
    xor(R2_eq_E1L3, R1L3, E1L3);
    not(notR2_eq_E1L3,R2_eq_E1L3);
    and(x2, R2L3,notR2_eq_E1L3); // x2 = R2L3 & ~ (R1L3 ^ E1L3)
    xor(R2S0, x2, E2L3);
    and(R2E, notR2_eq_E1L3, 1'b1); // R2E = ~(R1L3 ^ E1L3)
    assign MUXR2 = (R2E) ? (R2S0 ? E2L3 : x2) : 1'b0; // MUX for R2 correction
    assign O2L3 = MUXR2;

    // Logic for R3L3
    wire R3_and_MUXR2;
    and(R3_and_MUXR2, R3L3, MUXR2);
    xor(R3S0, R3_and_MUXR2, E3L3);
    and(R3E, MUXR2, 1'b1); // R3E = MUXR2
    assign userR3L3 = SWITCH2L3 ? 1 : 0;
    assign O3L3 = userR3L3 ? 0 : R3L3; // User control switch for R3L3
    assign MUXR3 = (R3E) ? (R3S0 ? E3L3 : R3_and_MUXR2) : 1'b0; // MUX for R3 correction
    assign O3L3 = MUXR3;

    // Logic for R4L3
    wire R4_and_MUXR3;
    and(R4_and_MUXR3, R4L3, MUXR3);
    xor(R4S0, R4_and_MUXR3, E4L3);
    and(R4E, SWITCH1L3, 1'b1); // R4E = SWITCH1L3
    assign userR4L3 = SWITCH1L3 ? 1 : 0;
    assign O4L3 = userR4L3 ? 0 : R4L3; // User control switch for R4L3
    assign MUXR4 = (R4E) ? (R4S0 ? E4L3 : R4_and_MUXR3) : 1'b0; // MUX for R4 correction
    assign O4L3 = MUXR4;

    // Output O5L3 is directly R5L3
    assign O5L3 = R5L3;

    // Passing condition for Level 3
    assign LEVEL3_PASSED = O1L3 & O2L3; 

    endmodule

  ### Data Flow
    module lfsr_5bit (
    input clk,    // Clock input
    input rst,    // Reset input
    output reg [4:0] lfsr_out  // 5-bit output
    );

    wire feedback;

    // Feedback is taken from bits 5 and 3 (tap positions 4 and 2 in Verilog, 0-indexed)
    assign feedback = ~(lfsr_out[4] ^ lfsr_out[2]); 

    always @(posedge clk or posedge rst) begin
        if (rst) begin
            // On reset, set LFSR to a non-zero seed value
            lfsr_out <= 5'b00001;
        end else begin
            // Shift the LFSR and insert the feedback bit at position 4
            lfsr_out <= {lfsr_out[3:0], feedback};
        end
    end

    endmodule

    module level1(
    input wire R1, R2, R3, R4, R5,       //R : Random Input bits
    input wire E1, E2, E3, E4, E5,       //E : Expected Output bits
    output wire O1, O2, O3, O4, O5,      //O : Actual Output bits
    output wire LEVEL1_PASSED            //Equals to one if Level 1 is passed
    );

    wire notE5, x2, R2S0, R2I0, R2I1, R2E, MUXR2, x3, R3S0, R3I0, R3I1, R3E, MUXR3, x4, R4S0, R4I0, R4I1, R4E, MUXR4;

    // Not gate for E5
    assign notE5 = ~E5;

    assign E1=1;
    assign E2=1;
    assign E3=1;
    assign E4=1;
    assign E5=0;

    // Output O1 is directly R1
    assign O1 = R1;

    // Logic for R2
    assign x2 = R2 & (~(R1 ^ E1));
    assign R2S0 = x2 ^ E2;
    assign R2I0 = x2; 
    assign R2I1 = E2;
    assign R2E = ~(R1 ^ E1);
    assign MUXR2 = R2E ? (R2S0 ? R2I1 : R2I0) : 1'b0; //Checking the R2 and  correcting it, if it's wrong
    assign O2 = MUXR2; //R2 after correction

    // Logic for R3
    assign x3 = R3 & MUXR2;
    assign R3S0 = x3 ^ E3;
    assign R3I0 = x3;
    assign R3I1 = E3;
    assign R3E = MUXR2;
    assign MUXR3 = R3E ? (R3S0 ? R3I1 : R3I0) : 1'b0; //Checking the R3 and  correcting it, if it's wrong
    assign O3 = MUXR3; //R3 after correction

    // Logic for R4
    assign x4 = R4 & MUXR3;
    assign R4S0 = x4 ^ E4;
    assign R4I0 = x4;
    assign R4I1 = E4;
    assign R4E = MUXR3;
    assign MUXR4 = R4E ? (R4S0 ? R4I1 : R4I0) : 1'b0; //Checking the R4 and  correcting it, if it's wrong
    assign O4 = MUXR4; //R4 after correction

    // Output O5 is directly R5
    //Since R5 is non-essential subsystem
    assign O5 = R5;

    // Passing condition for Level 1 :
    //All crucial subsystems(O1,O2,O3,O4) should be working
    assign LEVEL1_PASSED = O1 & O2 & O3 & O4; 

    endmodule
    module level2(
    input wire clk,          // Clock input
    input wire rst,          // Reset input
    input wire E1L2, E2L2, E3L2, E4L2, E5L2, // E: Expected Output bits
    input wire SWITCH1L2,    // Switch input for controlling R4L2
    output wire O1L2, O2L2, O3L2, O4L2, O5L2, // O: Actual Output bits
    output wire LEVEL2_PASSED, // Equals 1 if Level 2 is passed
    output wire userR4L2     // Output for turning on/off subsystem R4
    );

    wire [4:0] lfsr_out;    // Output from the LFSR
    wire R1L2, R2L2, R3L2, R4L2, R5L2; // Random input bits taken from LFSR output

    // Instantiate the LFSR module
    lfsr_5bit lfsr_inst (
        .clk(clk),
        .rst(rst),
        .lfsr_out(lfsr_out)
    );

    // Assign LFSR outputs to the random input bits R1L2 to R5L2
    assign R1L2 = lfsr_out[0];
    assign R2L2 = lfsr_out[1];
    assign R3L2 = lfsr_out[2];
    assign R4L2 = lfsr_out[3];
    assign R5L2 = lfsr_out[4];

    wire notE5, x2, R2S0, R2I0, R2I1, R2E, MUXR2, x3, R3S0, R3I0, R3I1, R3E, MUXR3, x4, R4S0, R4I0, R4I1, R4E, MUXR4;

    // Not gate for E5L2
    assign notE5 = ~E5L2;

    assign E2L2=1;
    assign E1L2=1;
    assign E3L2=1;
    assign E4L2=0;
    assign E5L2=0;

    // Output O1L2 is directly R1L2
    assign O1L2 = R1L2;

    // Logic for R2L2
    assign x2 = R2L2 & (~(R1L2 ^ E1L2));
    assign R2S0 = x2 ^ E2L2;
    assign R2I0 = x2; // Correcting the undefined x1
    assign R2I1 = E2L2;
    assign R2E = ~(R1L2 ^ E1L2);
    assign MUXR2 = R2E ? (R2S0 ? R2I1 : R2I0) : 1'b0;   //Checking the R2L2 and  correcting it, if it's wrong
    assign O2L2 = MUXR2;  //R2L2 after correction


    // Logic for R3L2
    assign x3 = R3L2 & MUXR2;
    assign R3S0 = x3 ^ E3L2;
    assign R3I0 = x3;
    assign R3I1 = E3L2;
    assign R3E = MUXR2;
    assign MUXR3 = R3E ? (R3S0 ? R3I1 : R3I0) : 1'b0;  //Checking the R3 and  correcting it, if it's wrong
    assign O3L2 = MUXR3;  //R3L2 after correction

    // Logic for R4L2
    assign x4 = R4L2 & MUXR3;
    assign R4S0 = x4 ^ E4L2;
    assign R4I0 = x4;
    assign R4I1 = E4L2;
    assign R4E = SWITCH1L2;
    assign MUXR4 = R4E ? (R4S0 ? R4I1 : R4I0) : 1'b0;  //Checking the R4 and correcting it, if it's wrong
    assign O4L2 = MUXR4;  //R4L2 after correction

    // Output O5L2 is directly R5L2
    assign O5L2 = R5L2;

    // Condition for R4L2 if the user wants to switch the subsystem off
    assign userR4L2 = (SWITCH1L2) ? 1 : 0;
    assign O4L2 = (userR4L2) ? 0 : R4L2;
    // Passing condition for Level 2:
    // All crucial subsystems (O1L2, O2L2, O3L2) should be working
    assign LEVEL2_PASSED = O1L2 & O2L2 & O3L2;
    

    endmodule
    // Level 3 Module that uses LFSR outputs as input
     module level3(
    input wire clk,          // Clock input
    input wire rst,          // Reset input
    input wire E1L3, E2L3, E3L3, E4L3, E5L3,  // E: Expected Output bits
    input wire SWITCH1L3,    // Switch input for controlling R4L3
    input wire SWITCH2L3,    // Switch input for controlling R3L3
    output wire O1L3, O2L3, O3L3, O4L3, O5L3, // O: Actual Output bits
    output wire LEVEL3_PASSED, // Equals 1 if Level 3 is passed
    output wire userR4L3,    // Output for turning on/off subsystem R4L3
    output wire userR3L3     // Output for turning on/off subsystem R3L3
    );

    wire [4:0] lfsr_out;    // Output from the LFSR
    wire R1L3, R2L3, R3L3, R4L3, R5L3; // Random input bits taken from LFSR output

    // Instantiate the LFSR module
    lfsr_5bit lfsr_inst (
        .clk(clk),
        .rst(rst),
        .lfsr_out(lfsr_out)
    );

    // Assign LFSR outputs to the random input bits R1L3 to R5L3
    assign R1L3 = lfsr_out[0];
    assign R2L3 = lfsr_out[1];
    assign R3L3 = lfsr_out[2];
    assign R4L3 = lfsr_out[3];
    assign R5L3 = lfsr_out[4];

    wire notE5, x2, R2S0, R2I0, R2I1, R2E, MUXR2, x3, R3S0, R3I0, R3I1, R3E, MUXR3, x4, R4S0, R4I0, R4I1, R4E, MUXR4;

    // Not gate for E5L3
    assign notE5 = ~E5L3;

    assign E1L3=1;
    assign E2L3=1;
    assign E3L3=0;
    assign E4L3=0;
    assign E5L3=0;



    // Output O1L3 is directly R1L3
    assign O1L3 = R1L3;

    // Logic for R2L3
    assign x2 = R2L3 & (~(R1L3 ^ E1L3));
    assign R2S0 = x2 ^ E2L3;
    assign R2I0 = x2; // Correcting the undefined x1
    assign R2I1 = E2L3;
    assign R2E = ~(R1L3 ^ E1L3);
    assign MUXR2 = R2E ? (R2S0 ? R2I1 : R2I0) : 1'b0;   //Checking the R2L3 and correcting it if it's wrong
    assign O2L3 = MUXR2;     //R2L3 after correction
    // Logic for R3L3
    assign x3 = R3L3 & MUXR2;
    assign R3S0 = x3 ^ E3L3;
    assign R3I0 = x3;
    assign R3I1 = E3L3;
    assign R3E = SWITCH2L3;
    assign MUXR3 = R3E ? (R3S0 ? R3I1 : R3I0) : 1'b0;   //Checking the R3L3 and correcting it if it's wrong  
    assign O3L3 = MUXR3;    //R3L3 after correction

    // Logic for R4L3
    assign x4 = R4L3 & MUXR3;
    assign R4S0 = x4 ^ E4L3;
    assign R4I0 = x4;
    assign R4I1 = E4L3;
    assign R4E = SWITCH1L3;
    assign MUXR4 = R4E ? (R4S0 ? R4I1 : R4I0) : 1'b0;   //Checking the R4L3 and correcting it if it's wrong
    assign O4L3 = MUXR4;  //R4L3 after correction

    // Output O5L3 is directly R5L3
    assign O5L3 = R5L3;

    // Conditions for switching subsystems R3L3 and R4L3 off
    assign userR3L3 = (SWITCH1L3) ? 1 : 0;
    assign userR4L3 = (SWITCH2L3) ? 1 : 0;
    assign O3L3 = (userR3L3) ? 0 : R3L3;
    assign O4L3 = (userR4L3) ? 0 : R4L3;

    // Passing condition for Level 3:
    // All crucial subsystems (O1L3, O2L3) should be working
     assign LEVEL3_PASSED = O1L3 & O2L3;
    endmodule


  ### Test Bench
    module spacecraft_fault_tolerance_tb;
    reg clk;
    reg rst;

    // Inputs for Level 1
    reg R1, R2, R3, R4, R5;
    reg [4:0] E; // Register for E
    wire O1, O2, O3, O4, O5;
    wire LEVEL1_PASSED;

    // Inputs for Level 2
    reg SWITCH1L2;
    reg userR4L2;
    wire O1L2, O2L2, O3L2, O4L2, O5L2;
    wire LEVEL2_PASSED;

    // Inputs for Level 3
    reg SWITCH1L3, SWITCH2L3;
    reg userR3L3, userR4L3;
    wire O1L3, O2L3, O3L3, O4L3, O5L3;
    wire LEVEL3_PASSED;

    // Declare temporary registers for Level 2 and Level 3 outputs
    reg O4L2_reg; // Temporary register for Level 2 O4
    reg O3L3_reg; // Temporary register for Level 3 O3
    reg O4L3_reg; // Temporary register for Level 3 O4

    // Instantiate LFSR for random number generation
    reg [4:0] lfsr;

    // Clock generation
    always #20 clk = ~clk;

    // LFSR for generating pseudo-random numbers
    always @(posedge clk or posedge rst) begin
        if (rst) begin
            lfsr <= 5'b10001; // Initial seed
        end else begin
            lfsr <= {lfsr[3:0], lfsr[4] ^ lfsr[2]}; // LFSR feedback taps
        end
    end

    // Assign initial value for E (for Level 1)
    initial begin
        E = 5'b11110; // Set a constant value for E for Level 1
    end

    // Assign random inputs based on LFSR output
    always @(posedge clk) begin
        if (!rst) begin
            // Generate random inputs for Level 1
            R1 <= lfsr[0]; // Random bit (0 or 1)
            R2 <= lfsr[1];
            R3 <= lfsr[2];
            R4 <= lfsr[3];
            R5 <= lfsr[4];
        end
    end

    // Instantiate Level 1
    level1 level1_inst (
        .R1(R1), .R2(R2), .R3(R3), .R4(R4), .R5(R5),
        .E1(E[4]), .E2(E[3]), .E3(E[2]), .E4(E[1]), .E5(E[0]),
        .O1(O1), .O2(O2), .O3(O3), .O4(O4), .O5(O5),
        .LEVEL1_PASSED(LEVEL1_PASSED)
    );

    // Instantiate Level 2
    level2 level2_inst (
        .clk(clk), .rst(rst),
        .E1L2(E[4]), .E2L2(E[3]), .E3L2(E[2]), .E4L2(E[1]), .E5L2(E[0]),
        .SWITCH1L2(SWITCH1L2),
        .O1L2(O1L2), .O2L2(O2L2), .O3L2(O3L2), .O4L2(O4L2), .O5L2(O5L2),
        .LEVEL2_PASSED(LEVEL2_PASSED)
    );

    // Instantiate Level 3
    level3 level3_inst (
        .clk(clk), .rst(rst),
        .E1L3(E[4]), .E2L3(E[3]), .E3L3(E[2]), .E4L3(E[1]), .E5L3(E[0]),
        .SWITCH1L3(SWITCH1L3), .SWITCH2L3(SWITCH2L3),
        .O1L3(O1L3), .O2L3(O2L3), .O3L3(O3L3), .O4L3(O4L3), .O5L3(O5L3),
        .LEVEL3_PASSED(LEVEL3_PASSED)
    );

    initial begin
        // Initialize the clock and reset
        clk = 0;
        rst = 1;
        SWITCH1L2 = 0;
        SWITCH1L3 = 0;
        SWITCH2L3 = 0;

        // Wait for some time and then release reset
        #20;
        rst = 0;

        // Loop to generate multiple test sets
        repeat (3) begin // Adjust the number of test runs as needed
            #40; // Wait for outputs to stabilize

            // Set E for Level 1
            E = 5'b11110; 
            $display("Level 1 Inputs: R1L1=%b R2L1=%b R3L1=%b R4L1=%b R5L1=%b EL1=%b", R1, R2, R3, R4, R5, E);
            
            if (LEVEL1_PASSED) begin
                $display("Level 1 Passed: O1L1=%b O2L1=%b O3L1=%b O4L1=%b O5L1=%b", O1, O2, O3, O4, O5);

                // Generate random inputs for Level 2
                SWITCH1L2 = 1;
                #20; // Wait for Level 2 outputs
                // Set E for Level 2
                E = 5'b11100; 
                $display("Level 2 running...");
                $display("Level 2 Inputs: R1L2=%b R2L2=%b R3L2=%b R4L2=%b R5L2=%b EL2=%b", R1, R2, R3, R4, R5, E);
                
                if (LEVEL2_PASSED) begin
                    // User Prompt for Level 2: 4th Bit
                    userR4L2 = lfsr[0]; // Randomize user input (0 or 1)

                    if (userR4L2) begin
                        O4L2_reg = 0; // Switch off the 4th bit
                        $display("User asked to switch off 4th bit. O4L2 set to 0.");
                    end 
                    else begin
                        O4L2_reg = R4; // Keep the original 4th bit state
                        $display("User chose not to switch off the 4th bit. O4L2=%b", R4);
                    end

                    $display("Level 2 Passed: O1L2=%b O2L2=%b O3L2=%b O4L2=%b O5L2=%b", O1L2, O2L2, O3L2, O4L2_reg, O5L2);
                    
                    // Set E for Level 3
                    E = 5'b11000; 
                    SWITCH1L3 = 1;

                    // Generate random inputs for Level 3
                    #20; // Wait for Level 3 outputs
                    $display("Level 3 running...");
                    $display("Level 3 Inputs: R1L3=%b R2L3=%b R3L3=%b R4L3=%b R5L3=%b EL3=%b", R1, R2, R3, R4, R5, E);
                    if (LEVEL3_PASSED) begin
                        userR3L3 = lfsr[0]; // Randomize user input (0 or 1)
                        userR4L3 = lfsr[1];

                        if (userR3L3) begin
                            O3L3_reg = 0; // Switch off the 3rd bit
                            $display("User asked to switch off 3rd bit. O3L3 set to 0.");
                        end 
                        else begin
                            O3L3_reg = R3; // Keep the original 3rd bit state
                            $display("User chose not to switch off the 3rd bit. O3L3=%b", R3);
                        end

                        if (userR4L3) begin
                            O4L3_reg = 0; // Switch off the 4th bit
                            $display("User asked to switch off 4th bit. O4L3 set to 0.");
                        end 
                        else begin
                            O4L3_reg = R4; // Keep the original 4th bit state
                            $display("User chose not to switch off the 4th bit. O4L3=%b", R4);
                        end

                        $display("Level 3 Passed: O1L3=%b O2L3=%b O3L3=%b O4L3=%b O5L3=%b", O1L3, O2L3, O3L3_reg, O4L3_reg, O5L3);
                        $display("MISSION SUCCESSFUL!");
                    end else begin
                        $display("Level 3 Failed!");
                        $display("MISSION FAILED!");
                    end
                end else begin
                    $display("Level 2 Failed!");
                    $display("MISSION ABORTED!");
                    
                end
            end else begin
                $display("Level 1 Failed!");
                $display("MISSION ABORTED!");
            end
            // Add a blank line after each test iteration
            $display("\n-----------------------------\n");
        end
        $finish;
    end
    endmodule
</details>

<!-- Seventh Section -->

## References
 <details> <summary>Details</summary>


- [Link 1](https://ntrs.nasa.gov/api/citations/20210020739/downloads/FinalCopy.pdf/)
- [Link 2](https://www.isro.gov.in/spacesciexp.html/)
- [Link 3](https://www.esa.int/Space_Safety/Hera/Fault_detection_isolation_and_recovery/)
- [Link 4](https://iopscience.iop.org/article/10.1088/1742-6596/2762/1/012064/pdf/)
- [Link 5](https://www.spacenavigators.com/post/fault-detection-and-recovery-in-satellite-aocs-ensuring-resilience-in-space/)



</details>


---



  

