🚀 P_DINESH_WEEK_1_RISC_V_SoC_Tapeout_Program_VSD

This repository documents my Week 1 progress in the RISC-V SoC Tapeout Program organized by VLSI System Design (VSD).
The main goal of this week was to set up a complete digital design flow using open-source tools and gain hands-on experience in RTL design, simulation, verification, and synthesis.

🌟 Week 1 Highlights

✅ 1. **RTL Design**  
   - Implemented basic digital modules to understand hardware description at the **register-transfer level (RTL)**.  
   - Created **testbenches** to verify functionality by applying input vectors and monitoring outputs.

✅ 2. **Simulation with Icarus Verilog**  
   - Compiled Verilog design and testbench into a **simulation executable**.  
   - Verified design behavior under different test conditions.
✅ 3.  **Waveform Analysis with GTKWave**  
   - Visualized **signal transitions, timing diagrams, and logic behavior**.  
   - Debugged and confirmed correctness of the designorrectness.
✅ 4. **Logic Synthesis with Yosys**  
   - Transformed **Verilog RTL** into a **gate-level netlist** mapped to a standard cell library.  
   - Optimized design using `synth` and `abc` commands.  
   - Prepared synthesized netlist for further verification or tapeout.


1️⃣ Icarus Verilog (iverilog) – Compile  Simulate Verilog

Purpose: Compile Verilog code and testbenches to produce a simulation executable.

Steps:

Open a terminal in the folder containing your Verilog files.

```
bash

iverilog  FILE_NAME.v FILE_NAME_TB.v

./a.out

```

2️⃣ GTKWAVE - Simulate Verilog
Purpose of GTKWave :Waveform Visualization

Steps:

Compile the design with the testbench:
```
bash

gtkwave filename.vcd

```

3️⃣Yosys – Logic Synthesis

### Purpose of Yosys

1. **RTL to Gate-Level Synthesis**  
   - Converts your **Verilog RTL code** into a **gate-level netlist**.  
   - Maps the design to standard cells from a library like SkyWater 130nm.

2. **Design Optimization and Verification**  
   - Uses commands like `synth` and `abc` to optimize logic.  
   - Produces synthesized Verilog and netlists for further flow steps.

3. **Integration with Open-Source EDA Flow**  
   - Works with **Icarus Verilog**, **GTKWave**, and other open-source tools.  
   - Essential for preparing designs for tapeout or FPGA implementation.

---

### Step-by-Step Commands

**Set Environment Variable for PDK Library**

```bash
# Set the path to your standard cell library
export SKY130_LIB=/path/to/skywater-pdk/libs/sky130_fd_sc_hd/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
# 1️⃣ Open Yosys shell
yosys

# 2️⃣ Read your Verilog design
read_verilog FILE_NAME.v

# 3️⃣ Read standard cell library using environment variable
read_liberty -lib $SKY130_LIB

# 4️⃣ Synthesize top module
synth -top FILE_NAME

# 5️⃣ Write synthesized Verilog netlist
write_verilog synthesized.v

# 6️⃣ Optimize logic using ABC with the same library
abc -liberty $SKY130_LIB

# 7️⃣ Exit Yosys
exit
