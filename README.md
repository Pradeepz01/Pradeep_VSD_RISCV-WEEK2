# Pradeep_VSD_RISCV-WEEK2
</details>

<details>
<summary>📅 Week 2 – Baby SoC Fundamentals (Research Summary)</summary>

### 🔹 Introduction

This week was focused on understanding the **Baby SoC (System-on-Chip)** — what it actually is, how it works, and what the main building blocks inside it are.  
It’s more like the *foundation week* where I got to know how everything in an SoC — CPU, memory, I/O, PLL, DAC — all work together to form a small complete computer on a chip.  

---

### 🔹 What is a System-on-Chip (SoC)?

A **System-on-Chip (SoC)** is basically a **mini computer built inside a single chip**.  
It has the **processor (CPU)**, **memory**, **peripherals (I/O)**, and **interconnects** all integrated together.  
This makes the chip powerful, compact, and energy efficient — that’s why SoCs are used in mobiles, IoT boards, and smart devices.

**Why it’s useful:**
- Saves a lot of PCB space.  
- Uses very less power.  
- Works faster due to internal connectivity.  
- Reliable and cheaper to produce.

---

### 🔹 Key Components of a SoC

| Component | Description |
|------------|--------------|
| **CPU (Processor)** | The main brain — executes instructions, manages everything. |
| **Memory** | RAM for temporary data, ROM for firmware and boot code. |
| **Peripherals / I/O** | Interfaces like UART, SPI, I2C, GPIO, ADC, DAC, etc. |
| **GPU** | Handles all display-related graphics work. |
| **DSP** | Used for signal processing like audio and video. |
| **Power Management Unit** | Distributes power efficiently inside the SoC. |
| **Other Features** | Wi-Fi, Bluetooth, and security modules (optional). |

---

### 🔹 Types of SoCs

1. **Microcontroller-based SoC** → small and low power (used in IoT, automation).  
2. **Microprocessor-based SoC** → high performance (used in mobiles, SBCs).  
3. **Application-Specific SoC (ASIC)** → made for one fixed purpose (like GPU, AI chip, etc).

---

### 🔹 SoC Design Flow

The **SoC Design Flow** starts with an idea and ends with a working chip:
> Specification → RTL Design → Verification → Synthesis → Physical Design → Tapeout
<p align="center">
<img width="960" height="720" alt="image" src="https://github.com/user-attachments/assets/e1749b03-50a8-46b1-9a6a-c99c4c338137" />

</p>

Each step ensures the chip works correctly before moving to the next stage.

---

### 🔹 VSD Baby SoC – Overview

The **VSDBabySoC** is a compact SoC built using the **RISC-V architecture**.  
It’s made for learning purposes — so we can explore how a real SoC works, test RISC-V cores, and understand both **digital and analog integration**.

#### 🧠 Main Components

1. **RVMyth SoC** –  
   A simple RISC-V processor built for quick understanding.  
   Helps visualize how CPU executes instructions, interacts with memory, and works inside an SoC.
<p align="center">
<img width="2270" height="1260" alt="vsd_babysoc" src="https://github.com/user-attachments/assets/b79352d5-5bf9-41e0-8b75-cf826a614e15" />
</p>

2. **PLL (Phase-Locked Loop)** –  
   Used to generate synchronized clock signals.  
   It ensures that all components of the chip work on stable and matching timing — preventing timing mismatches.
<p align="center">
<img width="317" height="159" alt="image" src="https://github.com/user-attachments/assets/427dc97d-a0f4-4c74-bf83-d7cfe447e933" />

</p>
3. **DAC (Digital-to-Analog Converter)** –  
   Converts digital binary signals into analog voltages.  
   Commonly used in audio output, sensors, or analog interfacing.

   Two types were discussed:
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

So this week I basically learned:
- What a SoC is and how all the blocks connect inside it.  
- Different types of SoCs and their use cases.  
- The flow of SoC design from RTL to final chip.  
- Components of **VSD Baby SoC** like RVMyth, PLL, and DAC.  

This week sets the foundation for **functional modeling and synthesis** in upcoming tasks.

---
