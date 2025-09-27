P_DINESH_WEEK_1_RISC_V_SoC_Tapeout_Program_VSD

This repository documents my Week 1 progress in the RISC-V SoC Tapeout Program organized by VLSI System Design (VSD). The primary focus of this week is to set up a complete digital design flow using open-source tools and gain hands-on experience in RTL design, simulation, verification, and synthesis.

The work begins with Verilog RTL design, where I implemented basic digital modules to understand hardware description at the register-transfer level. Along with the designs, I created testbenches to verify functionality by applying input vectors and monitoring outputs. Writing testbenches helped in learning structured verification methods, ensuring that the design behaves as expected.

For simulation, I used Icarus Verilog (iverilog), an efficient open-source compiler and simulator for Verilog. It allowed me to compile both the design and its corresponding testbench, producing simulation executables that validate correctness. To analyze the results, I used GTKWave, a powerful waveform viewer that enabled visualization of signal transitions, timing diagrams, and logic behavior. This step provided deeper insight into how the design responds under different test conditions.

The highlight of this week’s exercise is logic synthesis using Yosys. Yosys is a widely used open-source synthesis tool that transforms Verilog RTL code into a gate-level netlist mapped to a target technology library. Running synthesis offered exposure to how high-level hardware descriptions are broken down into logic gates and how synthesis reports can be interpreted for design quality, optimization, and correctness.

By completing these tasks, I successfully carried out the entire flow:
RTL Coding → Testbench Development → Simulation with Icarus Verilog → Waveform Analysis with GTKWave → Logic Synthesis with Yosys.

This week’s work laid the foundation for upcoming challenges in the RISC-V SoC Tapeout journey. It provided valuable hands-on practice with industry-relevant open-source EDA tools and gave me a strong understanding of the essential digital design cycle. The experience gained here will be critical in the following weeks, as the complexity of tasks increases toward the final tapeout.


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
