
<h1>EXP-4: 4Bit-Up-Down-Asynchronous-Reset-Counter-Synthesis</h1>

## Aim:

Synthesize 4Bit-Up-Down-Asynchronous-Reset-Counter design using Constraints and analyse reports, Timing, area and Power.

## Tool Required:

Functional Simulation: Incisive Simulator (ncvlog, ncelab, ncsim)

Synthesis: Genus

### Step 1: Getting Started

Synthesis requires three files as follows,

◦ Liberty Files (.lib)

◦ Verilog/VHDL Files (.v or .vhdl or .vhd)

◦ SDC (Synopsis Design Constraint) File (.sdc)

 ### Step 2 : Creating an SDC File

•	In your terminal type “gedit input_constraints.sdc” to create an SDC File if you do not have one.

•	The SDC File must contain the following commands;

create_clock -name clk -period 2 -waveform {0 1} [get_ports "clk"]

set_clock_transition -rise 0.1 [get_clocks "clk"]

set_clock_transition -fall 0.1 [get_clocks "clk"]

set_clock_uncertainty 0.01 [get_ports "clk"]

set_input_delay -max 0.8 [get_ports "rst"] -clock [get_clocks "clk"]

set_output_delay -max 0.8 [get_ports "count"] -clock [get_clocks "clk"]

i→ Creates a Clock named “clk” with Time Period 2ns and On Time from t=0 to t=1.

ii, iii → Sets Clock Rise and Fall time to 100ps.

iv → Sets Clock Uncertainty to 10ps.

v, vi → Sets the maximum limit for I/O port delay to 1ps.

### Step 3 : Performing Synthesis

The Liberty files are present in the library path,

• The Available technology nodes are 180nm ,90nm and 45nm.

• In the terminal, initialise the tools with the following commands if a new terminal is being
used.

◦ csh

◦ source /cadence/install/cshrc

• The tool used for Synthesis is “Genus”. Hence, type “genus -gui” to open the tool.

• Genus Script file with .tcl file Extension commands are executed one by one to synthesize the netlist.

#### Synthesis RTL Schematic :

![Screenshot 2024-11-11 110955](https://github.com/user-attachments/assets/56683497-ee91-42a5-b744-708869e9d355)

#### Area report:

![Screenshot 2024-11-16 153738](https://github.com/user-attachments/assets/cd7f6c58-c204-4fe9-8dbb-f5ac66c32411)

#### Power Report:

![Screenshot 2024-11-16 153756](https://github.com/user-attachments/assets/a132e1f1-bad2-4c2d-96c0-4ce3f843581e)

#### Timing Report: 

![Screenshot 2024-11-16 153811](https://github.com/user-attachments/assets/827dc3ca-04d4-488e-8192-31228c8256e2)

#### Result: 

The generic netlist has been created, and area, power, and timing reports have been tabulated and generated using Genus.





