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

<details>
  <summary>Abstract</summary>
  
 
  ![click here](https://github.com/Lahari-Naik/S2-TEAM_11-MINIPROJECT/blob/main/Snapshots/Fault%20Tolerance%20in%20Spacecrafts(ABSTRACT).pdf) 
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
  
  ![click here](https://github.com/Lahari-Naik/S2-TEAM_11-MINIPROJECT/blob/main/Snapshots/WORKING.pdf)
  
</details>

---

<details>
  <summary>Logisim</summary>
  
  
  
  
  MAIN CIRCUIT![Logisim Final Circuit Diagram](https://github.com/Lahari-Naik/S2-TEAM_11-MINIPROJECT/blob/main/Logisim/Circuit%20%20Images/S2-T11.png)
LEVEL 1 ![LEVEL 1 Circuit Diagram](https://github.com/Lahari-Naik/S2-TEAM_11-MINIPROJECT/blob/main/Logisim/Circuit%20%20Images/Level1Image.png)
 LEVEL 2 ![LEVEL 2 Circuit Diagram](https://github.com/Lahari-Naik/S2-TEAM_11-MINIPROJECT/blob/main/Logisim/Circuit%20%20Images/Level2Image.png)
 LEVEL 3 ![LEVEL 3 Circuit Diagram](https://github.com/Lahari-Naik/S2-TEAM_11-MINIPROJECT/blob/main/Logisim/Circuit%20%20Images/Level3.Image.png)
 LFSR ![LFSR Circuit Diagram](https://github.com/Lahari-Naik/S2-TEAM_11-MINIPROJECT/blob/main/Logisim/Circuit%20%20Images/LFSRImage.png)
  
  - [Brief description about logisim circuit](https://github.com/Lahari-Naik/S2-TEAM_11-MINIPROJECT/blob/main/Logisim/Design-Logisim.pdf)
  - [Download LFSR Circuit](https://github.com/Lahari-Naik/S2-TEAM_11-MINIPROJECT/blob/main/Logisim/Circuit/LFSR.circ)
  - [Download Level 1 Circuit](https://github.com/Lahari-Naik/S2-TEAM_11-MINIPROJECT/blob/main/Logisim/Circuit/level1.circ)
  - [Download Level 2 Circuit](https://github.com/Lahari-Naik/S2-TEAM_11-MINIPROJECT/blob/main/Logisim/Circuit/level2.circ)
  - [Download Level3 Circuit](https://github.com/Lahari-Naik/S2-TEAM_11-MINIPROJECT/blob/main/Logisim/Circuit/level3.circ)
  - [Download Logisim Final Circuit](https://github.com/Lahari-Naik/S2-TEAM_11-MINIPROJECT/blob/main/Logisim/Circuit/S2-T11.circ)
  
</details>

---

<details>
  <summary>Verilog Code</summary>
  TEST BENCH
  
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
    always #5 clk = ~clk;

    // LFSR for generating pseudo-random numbers
    always @(posedge clk or posedge rst) begin
        if (rst) begin
            lfsr <= 5'b10011; // Initial seed
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
    gate_level1 level1_inst (
        .R1(R1), .R2(R2), .R3(R3), .R4(R4), .R5(R5),
        .E1(E[4]), .E2(E[3]), .E3(E[2]), .E4(E[1]), .E5(E[0]),
        .O1(O1), .O2(O2), .O3(O3), .O4(O4), .O5(O5),
        .LEVEL1_PASSED(LEVEL1_PASSED)
    );

    // Instantiate Level 2
    gate_level2 level2_inst (
        .clk(clk), .rst(rst),
        .E1L2(E[4]), .E2L2(E[3]), .E3L2(E[2]), .E4L2(E[1]), .E5L2(E[0]),
        .SWITCH1L2(SWITCH1L2),
        .O1L2(O1L2), .O2L2(O2L2), .O3L2(O3L2), .O4L2(O4L2), .O5L2(O5L2),
        .LEVEL2_PASSED(LEVEL2_PASSED)
    );

    // Instantiate Level 3
    gate_level3 level3_inst (
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
        #10;
        rst = 0;

        // Loop to generate multiple test sets
        repeat (32) begin // Adjust the number of test runs as needed
            #20; // Wait for outputs to stabilize

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
                $display("Level 2 Passed: O1L2=%b O2L2=%b O3L2=%b O4L2=%b O5L2=%b", O1L2, O2L2, O3L2, O4L2_reg, O5L2);
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

                    // $display("Level 2 Passed: O1L2=%b O2L2=%b O3L2=%b O4L2=%b O5L2=%b", O1L2, O2L2, O3L2, O4L2_reg, O5L2);
                    
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

---
 <details> <summary>References</summary>


- [Link 1](https://ntrs.nasa.gov/api/citations/20210020739/downloads/FinalCopy.pdf/)
- [Link 2](https://www.isro.gov.in/spacesciexp.html/)
- [Link 3](https://www.esa.int/Space_Safety/Hera/Fault_detection_isolation_and_recovery/)
- [Link 4](https://iopscience.iop.org/article/10.1088/1742-6596/2762/1/012064/pdf/)
- [Link 5](https://www.spacenavigators.com/post/fault-detection-and-recovery-in-satellite-aocs-ensuring-resilience-in-space/)



</details>

---



  

