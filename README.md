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

