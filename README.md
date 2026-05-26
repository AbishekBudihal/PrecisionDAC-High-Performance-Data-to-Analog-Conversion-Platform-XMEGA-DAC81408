## PrecisionDAC — High-Performance Data-to-Analog Conversion Platform
### *ATxmega128A1U • DAC81408EVM • Industrial RS-232 Interface • Multi-Rail Power System*

---

## Project Overview
**PrecisionDAC** is an industry-grade **Data-to-Analog Conversion (DAC) platform** built using:

- **ATxmega128A1U (100-pin)** microcontroller  
- **DAC81408EVM** (16-bit, 8-channel precision DAC)  
- **MAX3232** UART Transceiver (RS-232 ↔ TTL)  
- **DB-25 industrial connector interface**  
- **Isolated ±12V and 5V DC-DC converters**

Designed for **test equipment, control systems, industrial automation, and analog signal generation**, this project showcases embedded systems development, SPI driver design, mixed-signal understanding, and hardware–firmware integration.

---

## Key Features
- 16-bit precision Data-to-Analog conversion  
- SPI driver for DAC81408  
- UART (RS-232 <→ TTL) communication via MAX3232  
- DB-25 industrial interface mapping  
- Multi-rail power system: 24V → ±12V → 5V  
- Modular firmware structure  
- Scalable design for multi-channel instrumentation  

---

## Hardware Architecture

| Module | Part Number | Purpose |
|--------|-------------|---------|
| MCU | ATxmega128A1U | SPI control, UART communication, data processing |
| DAC Module | DAC81408EVM | 16-bit, 8-channel analog output |
| UART Transceiver | MAX3232 | RS-232 to TTL |
| Industrial Connector | DB-25 | Analog output interface |
| DC-DC Converters | ±12V & 5V modules | Power supply subsystem |

---

## Block Diagram
      +-----------------------------+
      |     ATxmega128A1U MCU       |
      |   (SPI + UART + GPIO)       |
      +---------------+-------------+
                      |
                      | SPI
                      v
            +------------------+
            |  DAC81408EVM     |
            | 16-bit, 8-ch DAC |
            +--+--+--+--+--+---+
               |  |  |  |  
               v  v  v  v  
          DB-25 Industrial Output

      UART (USART)
            |
            v
    +-------------------+
    |   MAX3232 IC      |
    | RS232 <-> TTL     |
    +---------+---------+
              |
            RS-232
              |
            PC/Host

 Power System:
 24V → ±12V → 5V → DAC + MCU


---

## Repository Structure
PrecisionDAC/  
│
├── firmware/  
│ └── main.c  
│
├── hardware/  
│ └── schematics/  
│
├── docs/  
│ ├── schematics/  
│ └── images/  
│
├── LICENSE  
└── README.md  

---

## Firmware Highlights
- SPI driver for DAC81408  
- UART handler for RS-232 communication  
- DAC channel initialization  
- Structured command interface  
- Lookup-table based waveform support  
- Watchdog and safety checks  

---

## Validation Results
| Parameter | Result |
|---|---|
| Full-Scale Error | **0.037%** |
| Validation Tools | Oscilloscope + DMM |
| Tolerance Standard | Industrial-grade |

---

## Build & Flash Instructions
### 1. Install AVR toolchain
- AVR-GCC  
- Atmel/Microchip Studio
- Docklight Scripting / Docklight Standard  

### 2. Build  
#### 2 — Open the project  
- Open Microchip Studio  
- Go to: File → Open → Project/Solution  
- Select the .atsln file inside the project folder  
#### Step 3 — Configure the device  
- Go to: Project → Properties → Device  
- Select: ATxmega128A1U  
- Make sure the toolchain is AVR/GNU C Compiler  
#### Step 4 — Set project clock (recommended)  
- Go to: Project → Properties → Toolchain → Symbols  
- Define CPU frequency: F_CPU=32000000UL  
#### Step 5 — Build the firmware  
- Go to: Build → Build Solution  
- The compiled HEX file will be located in: /Debug/YourProjectName.hex  

### 3. Flashing the Firmware (Using Atmel-ICE)  
#### Step 1 — Open Device Programming  
- Go to: Tools → Device Programming  
#### Step 2 — Select programmer & device  
- Tool: Atmel-ICE  
- Device: ATxmega128A1U  
- Interface: PDI (mandatory for XMEGA)  
#### Step 3 — Verify connection  
- Click Read (to read device signature)  
#### Step 4 — Load the HEX file  
- Open the Memories section  
- Select the .hex file generated from the build  
#### Step 5 — Flash  
- Click Program  

### 2. Docklight Configuration  
#### Step 1 — Open Docklight  
- Go to: Project → New Project  
#### Step 2 — Set Communication Settings  
- COM Port: Select the port detected in Device Manager  
- Baud Rate: 115200 (or whatever your firmware uses)  
- Data Bits: 8  
- Parity: None  
- Stop Bits: 1  
- Flow Control: None  
#### Step 3 — Connect  
- Click Project → Start Communication  
- You should now see incoming data from the ATxmega128A1U  

