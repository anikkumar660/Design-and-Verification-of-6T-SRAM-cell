# SRAM
Design of a 6T full CMOS SRAM  using Cadence Virtuoso.
# What is SRAM?
Static Random-Access Memory (SRAM) is a type of volatile memory that stores each bit using latching circuitry. Unlike Dynamic Random-Access Memory (DRAM), which requires periodic refreshing, SRAM retains its data as long as power is supplied, hence the term "static." However, once power is removed, the data is lost.

The fundamental storage unit in SRAM, known as the 1-bit memory cell, is built around a simple latch circuit with two stable states. Depending on the state of this latch, the stored data is interpreted as either a logic "0" or "1." To access or modify the data in the memory cell via the bit line, at least one switch is required, which is controlled by the word line or row address selection signal. Typically, two complementary nMOS pass transistors are used as access switches, connecting the 1-bit SRAM cell to the complementary bitlines (columns). This configuration can be compared to steering a car using both hands in opposite directions for balanced control.

# Table Of Contents
- [Overview](#Overview)
    - [Project Details](#Project-Details)
    - [Basics of Working Principle of a SRAM](#Basic-Working-of-SRAM) 
- [Schematic Design and Simulation](#Schematic-design-&-Simulation)
     - [Trasnsistor sizing](#Transistor-Sizing)
     - [6T cell](#6T-cell)
     - [Pre charge Clock](#Pre-charge-clock)
     - [Sense amplifier](#Sense-amplifier)
     - [Write driver](#Write-driver)
     - [Timing Diagram For Read and Write](#Timing-diagram)
# Project Details
 - Organisation :Used the tools from the SSCD Lab. [Indian  Institute Of Technology Kanpur]
 - About        :In this project, I designed a novel six-transistor (6T) static random access memory (6T-SRAM) cell for standard applications.
 - Tools used : Cadence Virtuoso
 - Technology used:  gpdk 180

# Basic Working of SRAM
- **Basic block diagram for a SRAM IP**
    - The basic SRAM IP constitute of a 6T cell array, Sense amplifier array, Write Driver array, Precharge array, Address decoder and a wordline driver
    - ![alt text](https://user-images.githubusercontent.com/49194847/100307628-56bd1c00-2fcc-11eb-99dc-e23c7501f2f5.png)
- **6T cell** 
     - A low-power SRAM cell may be designed simply by using cross-coupled CMOS inverters. Here M1-M5 and M2-M6 are two cross Coupled inverters.M3 and M4 are access transistors.Here the data will be stored in 1 and 2 that are basically parasitic capacitors.
     - ![alt text](https://user-images.githubusercontent.com/49194847/100307234-54a68d80-2fcb-11eb-9a73-0753d59bd340.png)
- **Read Operation**
    - Let's assume the 6T cell initially holds a value of 0. The effective circuit topology will look like the image shown below (assuming the bit lines are precharged to \(V_{dd}\)). When \(M_3\) and \(M_4\) are turned on, \(V_c\) will discharge, causing a change in \(V_1\). This voltage change on the bit line will then be detected by the sense amplifier and interpreted as 0.
     - ![alt text](https://user-images.githubusercontent.com/49194847/100306663-e57c6980-2fc9-11eb-8096-2ed351e49d88.png)
- **Write Operation**
   - Let's consider that the circuit initially contained a value of 1, and we want to change this to 0. For a cell holding a 1, the effective circuit would appear as follows: To write a 0, we set the bit line to 0 using the write circuitry. However, to modify the content, \(V_1\) must be equal to 0. Since the circuit is designed so that \(V_2\) cannot exceed \(V_{tn}\), we need to ensure that \(V_1\) is greater than \(V_{tn}\) to turn off \(M_2\).
    - ![alt text](https://user-images.githubusercontent.com/49194847/100307328-8fa8c100-2fcb-11eb-9d64-b9a1cc66b057.png)

    ## Output
    Please find the simulated output in the `.\SRAM_Anik.pdf` file.

