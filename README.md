# Pradeep_VSD_RISCV-WEEK2

<details>
<summary>Part-1 Baby SoC Fundamentals (Research Summary)</summary>

### 🔹 Introduction
This week focused on understanding the **Baby SoC (System-on-Chip)** — its architecture, components, and working principles.  
It served as a *foundation week*, exploring how a small CPU, memory, PLL, DAC, and I/O work together on a single chip.

---

### 🔹 What is a System-on-Chip (SoC)?
A **System-on-Chip (SoC)** is a **miniature computer on a single chip**.  
It integrates **CPU**, **memory**, **peripherals (I/O)**, and **interconnects**, enabling compact, low-power, and efficient operation.  

**Benefits:**
- Saves PCB space.  
- Reduces power consumption.  
- Improves speed due to internal connectivity.  
- Cost-effective and reliable.

---

### 🔹 Key Components of a SoC

| Component | Description |
|------------|--------------|
| **CPU (Processor)** | Executes instructions and coordinates all operations. |
| **Memory** | RAM for temporary storage, ROM for firmware/boot code. |
| **Peripherals / I/O** | UART, SPI, I2C, GPIO, ADC, DAC, etc. |
| **GPU** | Handles graphics/display tasks. |
| **DSP** | For signal processing like audio/video. |
| **Power Management Unit** | Efficiently distributes power. |
| **Other Features** | Optional modules like Wi-Fi, Bluetooth, security, etc. |

---

### 🔹 Types of SoCs
1. **Microcontroller-based SoC** – Low power, small, used in IoT/automation.  
2. **Microprocessor-based SoC** – High performance, used in mobiles, SBCs.  
3. **Application-Specific SoC (ASIC)** – Dedicated purpose, e.g., GPU, AI chip.

---

### 🔹 SoC Design Flow
**Flow:** Specification → RTL Design → Verification → Synthesis → Physical Design → Tapeout

<p align="center">
<img width="960" height="720" alt="image" src="https://github.com/user-attachments/assets/e1749b03-50a8-46b1-9a6a-c99c4c338137" />
</p>

---

### 🔹 VSD Baby SoC – Overview
The **VSDBabySoC** is a small SoC using the **RISC-V architecture**, designed for learning purposes.  
It demonstrates integration of digital and analog components.

#### 🧠 Main Components
1. **RVMyth CPU** – RISC-V processor that updates registers and prepares values for DAC.  
<p align="center">
<img width="2270" height="1260" alt="vsd_babysoc" src="https://github.com/user-attachments/assets/b79352d5-5bf9-41e0-8b75-cf826a614e15" />
</p>

2. **PLL (Phase-Locked Loop)** – Generates synchronized clocks for stable operation.  
<p align="center">
<img width="317" height="159" alt="image" src="https://github.com/user-attachments/assets/427dc97d-a0f4-4c74-bf83-d7cfe447e933" />
</p>

3. **DAC (Digital-to-Analog Converter)** – Converts digital values to analog voltages.  
   - **Weighted Resistor DAC**  
<p align="center">
<img width="601" height="301" alt="image" src="https://github.com/user-attachments/assets/67f1c018-8607-4546-a55a-15c063d18a08" />
</p>
   - **R-2R Ladder DAC**  
<p align="center">
<img width="800" height="390" alt="image" src="https://github.com/user-attachments/assets/6d424b72-8ed2-47d3-88f8-bab1937c4fd6" />
</p>

---

### 🔹 Summary
This week I learned:
- SoC fundamentals and internal block interactions.  
- Types of SoCs and applications.  
- Complete SoC design flow from RTL to chip.  
- Components of VSDBabySoC: RVMyth, PLL, DAC.  

This forms the foundation for **functional modeling and synthesis** tasks.

</details>

<details>
<summary>Part 2 – Labs (Hands-on Functional Modeling of VSDBabySoC)</summary>

### 🔹 Working Principle

1. **Clock Generation** – PLL multiplies reference clock to generate stable, higher-frequency clock for CPU and DAC.  
2. **CPU Operation** – RVMYTH continuously updates register `r17` with computed values for DAC conversion.  
3. **Analog Output** – DAC converts 10-bit digital `D` to voltage:

\[
OUT = VREFL + \frac{D}{1023} \times (VREFH - VREFL)
\]

---

### 🔹 Visualizing Signals with GTKWAVE
Using GTKWave, observe:
- Clock (`CLK`) stability from PLL  
- Register `r17` updates from CPU  
- Digital-to-analog conversion at DAC output  

This validates **design correctness pre- and post-synthesis**.

---

### 🔹 Simulation Process

#### Install dependencies
```bash
sudo apt install make python3 python3-pip git iverilog gtkwave docker.io
sudo chmod 666 /var/run/docker.sock
pip3 install pyyaml click sandpiper-saas
```
Clone repository
```bash
git clone https://github.com/manili/VSDBabySoC.git
cd VSDBabySoC
```
Run simulations
```bash
make pre_synth_sim
make post_synth_sim
```
View waveforms
```bash
gtkwave output/pre_synth_sim/pre_synth_sim.vcd
gtkwave output/post_synth_sim/post_synth_sim.vcd
```
🔹 Observations
Signal	Source	Behavior
CLK	PLL	Stable and synchronous
reset	External	Initializes registers properly
RV_TO_DAC[9:0]	RVMYTH	Sequential updates as CPU executes
DAC.OUT	DAC	Smooth analog transitions
VSDBabySoC.OUT	SoC output	Digital representation of analog signal
🔹 Post-Synthesis Analysis
<img width="1315" height="481" alt="image" src="https://github.com/user-attachments/assets/9ad03bd4-56dc-4e1e-9ae2-37d9d6bac7ef" />
🔹 Pre-Synthesis Analysis
<img width="1310" height="448" alt="image" src="https://github.com/user-attachments/assets/58919561-554d-41f2-9824-8154a1bc6f03" />

Post-synthesis results match pre-synthesis behavior.

VSDBabySoC.OUT shows digital levels (1 and 0).

DAC.OUT shows smooth analog waveform formed by fine digital steps — visually continuous.
