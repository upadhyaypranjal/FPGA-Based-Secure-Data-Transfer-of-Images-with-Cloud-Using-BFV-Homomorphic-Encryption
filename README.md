<div align="center">

<img src="https://img.shields.io/badge/IIITDM-Kurnool-blue?style=for-the-badge" />
<img src="https://img.shields.io/badge/Subject-ID--351-orange?style=for-the-badge" />
<img src="https://img.shields.io/badge/Status-Complete-brightgreen?style=for-the-badge" />
<img src="https://img.shields.io/badge/License-MIT-purple?style=for-the-badge" />

<br/><br/>

```
██████╗ ███████╗██╗   ██╗    ██╗  ██╗ ██████╗ ███╗   ███╗ ██████╗ ███╗   ███╗ ██████╗ ██████╗ ██████╗ ██╗  ██╗██╗ ██████╗
██╔══██╗██╔════╝██║   ██║    ██║  ██║██╔═══██╗████╗ ████║██╔═══██╗████╗ ████║██╔═══██╗██╔══██╗██╔══██╗██║  ██║██║██╔════╝
██████╔╝█████╗  ██║   ██║    ███████║██║   ██║██╔████╔██║██║   ██║██╔████╔██║██║   ██║██████╔╝██████╔╝███████║██║██║
██╔══██╗██╔══╝  ╚██╗ ██╔╝    ██╔══██║██║   ██║██║╚██╔╝██║██║   ██║██║╚██╔╝██║██║   ██║██╔══██╗██╔═══╝ ██╔══██║██║██║
██████╔╝██║      ╚████╔╝     ██║  ██║╚██████╔╝██║ ╚═╝ ██║╚██████╔╝██║ ╚═╝ ██║╚██████╔╝██║  ██║██║     ██║  ██║██║╚██████╗
╚═════╝ ╚═╝       ╚═══╝      ╚═╝  ╚═╝ ╚═════╝ ╚═╝     ╚═╝ ╚═════╝ ╚═╝     ╚═╝ ╚═════╝ ╚═╝  ╚═╝╚═╝     ╚═╝  ╚═╝╚═╝ ╚═════╝
```

# 🔐 FPGA-Based Secure Transfer of Images to Cloud Using BFV Homomorphic Encryption

### *Hardware-Accelerated Privacy-Preserving Image Transfer · FPGA → Cloud → ASIC SoC*

<br/>

[![Live Demo](https://img.shields.io/badge/🌐_Live_Portal-BFV_Encryption_Gateway-00C7B7?style=for-the-badge&logo=netlify)](https://bfv-encryption-gateway.netlify.app/)
[![SoC Repo](https://img.shields.io/badge/GitHub-SoC_Design_Repo-181717?style=for-the-badge&logo=github)](https://github.com/sohan2311/SoC-BFV-Homomorphic-Encryption-Genus-Innovus-180-90-nm)
[![Web Repo](https://img.shields.io/badge/GitHub-Web_Interface_Repo-181717?style=for-the-badge&logo=github)](https://github.com/sohan2311/BFV-Homomorphic-Encryption-of-Image-using-Cloud)

</div>

---

## 📌 Table of Contents

- [Project Overview](#-project-overview)
- [Team Members](#-team-members)
- [Repository Structure](#-repository-structure)
- [Background & Motivation](#-background--motivation)
- [BFV Cryptographic Theory](#-bfv-cryptographic-theory)
- [System Architecture](#-system-architecture)
- [Phase 1: FPGA Implementation](#-phase-1-fpga-implementation)
  - [Hardware Architecture & RTL Design](#hardware-architecture--rtl-design)
  - [Image Preprocessing Pipeline](#image-preprocessing-pipeline)
  - [FSM Implementation](#fsm-implementation)
  - [Modular Arithmetic Units](#modular-arithmetic-units)
  - [Vivado Block Design & AXI Integration](#vivado-block-design--axi-integration)
  - [Behavioral Simulation & Verification](#behavioral-simulation--verification)
  - [FPGA Implementation Results](#fpga-implementation-results)
  - [Vitis Bare-Metal Application](#vitis-bare-metal-application)
  - [Cloud Transfer Pipeline](#cloud-transfer-pipeline)
  - [Decryption Core](#decryption-core)
- [Phase 2: ASIC SoC Design (RTL → GDSII)](#-phase-2-asic-soc-design-rtl--gdsii)
  - [Design Flow Overview](#design-flow-overview)
  - [Pipelined FSM for ASIC](#pipelined-fsm-for-asic)
  - [180nm Synthesis Results](#180nm-synthesis-results-cadence-genus)
  - [90nm Synthesis Results](#90nm-synthesis-results-cadence-genus)
  - [Technology Node Comparison](#technology-node-comparison)
  - [Physical Design (Cadence Innovus 180nm)](#physical-design--cadence-innovus-180nm)
  - [Signoff Verification](#signoff-verification)
- [BFV Encryption Gateway – Web Application](#-bfv-encryption-gateway--web-application)
- [Consolidated Results](#-consolidated-results)
- [Applications](#-applications)
- [Conclusion & Future Work](#-conclusion--future-work)
- [RTL Source Code](#-rtl-source-code)
- [Software Scripts](#-software-scripts)
- [ASIC Scripts](#-asic-scripts)
- [Setup & Usage Guide](#-setup--usage-guide)
- [References](#-references)

---

## 🚀 Project Overview

> **"The cloud should compute on what it cannot see."**

Modern cloud computing exposes a critical **Trust Barrier**: conventional encryption schemes (AES, RSA) require data to be **decrypted** before cloud CPUs/GPUs can operate on it — creating a vulnerability window where raw pixel data is exposed in memory.

This project eliminates that vulnerability entirely through **Brakerski/Fan-Vercauteren (BFV) Fully Homomorphic Encryption (FHE)**, hardware-accelerated on a **Xilinx Zynq-7000 FPGA SoC**, and further validated through a complete **ASIC RTL-to-GDSII flow** on **180nm and 90nm** technology nodes.

### 🎯 Key Achievements

| Achievement | Detail |
|---|---|
| **Zero-Trust Encryption** | 64×64 grayscale image (4096 pixels) encrypted with BFV, never exposing raw pixels |
| **FPGA Acceleration** | Custom AXI4-Lite IP core encrypts 4096 pixels in **~164µs** at 100 MHz |
| **100% Pixel Recovery** | Perfect pixel-perfect decryption with **zero data loss** |
| **ASIC Silicon-Readiness** | Full RTL→GDSII at **180nm** (43,582 µm², 7.42 mW) and **90nm** (12,789 µm², 1.45 mW) |
| **Cloud Integration** | Encrypted ciphertexts securely hosted on GitHub Gists via HTTPS API |
| **Web Application** | Full-stack BFV Encryption Gateway (Next.js + Supabase) with RBAC |
| **All Signoff Clean** | DRC, Connectivity, Antenna checks all **PASS** |

---

## 👥 Team Members

| Name | Roll Number | Institution |
|---|---|---|
| **Divyansh Tiwari** | 123EC0039 | IIITDM Kurnool |
| **Vikramaditya Singh** | 123EC0042 | IIITDM Kurnool |
| **Sohan Maity** | 523EC0001 | IIITDM Kurnool |
| **Pranjal Upadhyay** | 523EC0012 | IIITDM Kurnool |

**Project Supervisor:** Dr. Mohamed Asan Basiri M (Asst. Prof Grade 1, Dept. of ECE)  
**Course Instructor:** Dr. Elangovan K · Dr. Vinay Kumar Tiwari  
**Department:** Electronics and Communications Engineering  
**Subject:** Product Design Practise (ID-351) · Submission: March 30, 2026

---

## 📁 Repository Structure

```
bfv-fpga-secure-cloud/
│
├── README.md                          ← You are here
│
├── rtl/
│   ├── encryption/
│   │   ├── bfv_mod_adder.v            ← Modular adder (single-cycle)
│   │   ├── bfv_mod_mult.v             ← Modular multiplier (Barrett, DSP48)
│   │   ├── bfv_keygen.v               ← Public key generation core
│   │   ├── bfv_encrypt_core.v         ← BFV encryption: computes C1, C2
│   │   └── bfv_top.v                  ← Top-level FSM controller (FPGA)
│   │
│   ├── decryption/
│   │   └── bfv_decrypt_core.v         ← BFV decryption core
│   │
│   └── asic/
│       └── bfv_top_pipelined.v        ← 11-state pipelined FSM for ASIC
│
├── software/
│   ├── preprocessing/
│   │   ├── image_converter.py         ← Image → .mem file (PIL/Numpy)
│   │   └── convert_image.py           ← .mem → C header for Vitis
│   │
│   ├── cloud/
│   │   ├── capture_uart.py            ← UART serial capture daemon
│   │   ├── push_to_gist.py            ← Encrypted upload to GitHub Gist
│   │   └── decrypt_verify.py          ← Python decryption & verification
│   │
│   └── vitis/
│       └── bfv_encrypt_app.c          ← Bare-metal C app for ARM Cortex-A9
│
├── asic/
│   ├── synthesis/
│   │   ├── run_genus_pipelined_180.tcl ← Cadence Genus 180nm script
│   │   ├── run_genus_pipelined_90.tcl  ← Cadence Genus 90nm script
│   │   └── bfv_pipelined_180nm.sdc    ← SDC timing constraints
│   │
│   ├── simulation/
│   │   └── tb_bfv_top.v               ← Testbench for ASIC simulation
│   │
│   └── physical_design/
│       └── innovus_flow.tcl           ← Cadence Innovus P&R script
│
├── constraints/
│   └── bfv_fpga.xdc                   ← Vivado XDC timing constraints
│
├── docs/
│   ├── PROJECT_REPORT.pdf             ← Full project report (colour)
│   ├── BFV_THEORY.md                  ← Detailed cryptographic theory
│   ├── FPGA_SETUP.md                  ← FPGA setup and programming guide
│   ├── ASIC_FLOW.md                   ← ASIC flow step-by-step guide
│   └── WEB_APP.md                     ← Web application documentation
│
└── results/
    ├── fpga/
    │   ├── timing_summary_encrypt.txt ← Vivado timing report (encrypt)
    │   ├── timing_summary_decrypt.txt ← Vivado timing report (decrypt)
    │   └── utilization_report.txt     ← Resource utilization report
    │
    └── asic/
        ├── timing_180nm.rpt           ← Genus timing report 180nm
        ├── power_180nm.rpt            ← Genus power report 180nm
        ├── timing_90nm.rpt            ← Genus timing report 90nm
        └── power_90nm.rpt             ← Genus power report 90nm
```

---

## 🔍 Background & Motivation

### The Trust Barrier in Cloud Computing

Sensitive visual data — medical imaging, satellite reconnaissance, industrial inspection — is routinely offloaded to cloud environments. However, **conventional cryptographic protocols have a fundamental flaw**:

```
┌──────────────────────────────────────────────────────────────────┐
│                      CONVENTIONAL APPROACH                       │
│                                                                  │
│  Client            Cloud Memory              Cloud CPU/GPU       │
│                                                                  │
│  ┌─────┐          ┌──────────────┐          ┌─────────────┐      │
│  │ Raw │ ──AES──► │  DECRYPTED!  │ ───────► │  Operates   │      │
│  │ IMG │  Encrypt │  ⚠️ EXPOSED  │          │  on Plain   │      │
│  └─────┘          │    PIXELS    │          │    Text     │      │
│                   └──────────────┘          └─────────────┘      │
│                          ↑                                       │
│          VULNERABILITY WINDOW — raw pixels accessible            │
│             to cloud admins and potential attackers              │
└──────────────────────────────────────────────────────────────────┘
```

```
┌──────────────────────────────────────────────────────────────────┐
│                 BFV FHE APPROACH (THIS PROJECT)                  │
│                                                                  │
│  FPGA Edge         Cloud Memory              Cloud CPU/GPU       │
│                                                                  │
│  ┌─────┐          ┌──────────────┐          ┌─────────────┐      │
│  │ Raw │ ──BFV──► │  CIPHERTEXT  │ ───────► │ Homomorphic │      │
│  │ IMG │  Encrypt │ ✅ ENCRYPTED │          │ Evaluation  │      │
│  └─────┘          │    ALWAYS    │          │  ON CIPHER  │      │
│                   └──────────────┘          └─────────────┘      │
│                                                                  │
│          ZERO TRUST BARRIER — cloud never sees pixels            │
│             Computation happens ON the ciphertext                │
└──────────────────────────────────────────────────────────────────┘
```

### Why BFV Over Other Schemes?

| Property | RSA | Paillier | CKKS | **BFV (Chosen)** |
|---|---|---|---|---|
| Addition on Ciphertext | ❌ | ✅ | ✅ | ✅ |
| Multiplication on Ciphertext | ✅ | ❌ | ✅ | ✅ |
| Exact Integer Arithmetic | ✅ | ✅ | ❌ (approx.) | ✅ |
| 8-bit Pixel Perfect Recovery | ✅ | ✅ | ❌ | ✅ |
| Hardware Friendly (Ring-LWE) | ❌ | ❌ | Partial | ✅ |
| Post-Quantum Security | ❌ | ❌ | ✅ | ✅ |

**BFV is the only scheme that simultaneously supports both homomorphic addition AND multiplication, guarantees exact integer arithmetic (critical for 0-255 pixel recovery), and is directly grounded in Ring-LWE — making it naturally suited to FPGA polynomial arithmetic acceleration.**

---

## 🔐 BFV Cryptographic Theory

### Mathematical Foundations

The BFV scheme operates over the polynomial ring **Rq = Zq[x]/(xⁿ + 1)**. The system parameters chosen for this implementation balance security, noise budget, and FPGA resource utilization:

| Parameter | Symbol | Value | Rationale |
|---|---|---|---|
| Ciphertext Modulus | Q | **12289** | 14-bit NTT-friendly prime |
| Plaintext Modulus | T | **256** | Encapsulates 8-bit grayscale range (0–255) |
| Polynomial Degree | N | **4096** | Matches 64×64 image dimensions |
| Scaling Factor | Δ | **⌊Q/T⌋ = 48** | ⌊12289/256⌋ = 48 |
| Secret Key | SK | Ternary ∈ {0,+1,−1} | Mapped to {0, 1, Q−1} in Zq |

### Key Generation

The BFV public key pair **(PK₁, PK₂)** is derived from:

```
PK₁ = [−(a · SK + e)] mod Q
PK₂ = a
```

Where:
- `a` — uniformly random polynomial coefficient in Zq
- `e` — small error polynomial sampled from chi distribution (noise budget bounded)
- `SK` — secret key (ternary polynomial)

### Encryption Algorithm

For each plaintext pixel **m** ∈ {0, ..., 255}, the hardware computes ciphertext pair **(C₁, C₂)**:

```
C₁ = [PK₁ · u + e₁ + Δ · m] mod Q
C₂ = [PK₂ · u + e₂]         mod Q
```

Where `u`, `e₁`, `e₂` are fresh ephemeral noise terms generated per pixel by the LFSR.

### Decryption Algorithm

```
inner = (C₁ + C₂ · SK) mod Q
m     = ⌊(inner · T + ⌊Q/2⌋) / Q⌋  mod T
```

### Noise Budget Analysis

The critical constraint ensuring correct decryption is:

```
‖v‖ = e_key + e₁ + e₂ ≤ 3 + 10 + 10 = 23  <  Q/(2T) = 12289/512 ≈ 24
```

This tight bound is enforced by clipping LFSR-generated noise terms to max 10.

### LFSR Noise Generation

A 16-bit maximal-length LFSR implements the pseudo-random noise generator using polynomial **P(x) = x¹⁶ + x¹⁴ + x¹³ + x¹¹ + 1**:

```
Seed:     0xACE1
Feedback: lfsr[15] ⊕ lfsr[13] ⊕ lfsr[12] ⊕ lfsr[10]
```

Ephemeral key extraction:
- `u`:  bits [1:0] → ternary {0, 1, Q−1}
- `e₁`: bits [4:0] → clipped to max 10
- `e₂`: bits [9:5] → clipped to max 10

---

## 🏗️ System Architecture

The complete system implements a **Hardware/Software co-design** across three distinct layers:

```
╔════════════════════════════════════════════════════════════════════════════════╗
║                    END-TO-END BFV SECURE PIPELINE                              ║
╠════════════════════════════════════════════════════════════════════════════════╣
║                                                                                ║
║  ┌──────────────┐    ┌─────────────────────────────────┐    ┌────────────────┐ ║
║  │  HOST PC     │    │     FPGA SENDER BOARD           │    │  CLOUD         │ ║
║  │              │    │  ┌──────────┐  ┌──────────────┐ │    │  (GitHub Gist) │ ║
║  │ image.png    │    │  │ ARM PS   │  │ BFV Encrypt  │ │    │                │ ║
║  │     │        │    │  │ Cortex-A9│  │ AXI IP       │ │    │  Ciphertext    │ ║
║  │ Python       │ ──►│  │          │◄►│ (PL)         │ │    │  .mem file     │ ║
║  │ image_       │    │  │ AXI-Lite │  │              │ │    │  (encrypted)   │ ║
║  │ converter.py │    │  │ Control  │  │ DSP48 slices │ │    │                │ ║
║  │              │    │  └──────────┘  └──────────────┘ │    └───────┬────────┘ ║
║  │              │    │        │ UART 115200 baud       │            │          ║
║  └──────────────┘    └────────┼────────────────────────┘            │          ║
║                               │                                     │          ║
║  ┌──────────────┐    ┌────────▼──────────┐              ┌───────────▼───────┐  ║
║  │  RECEIVER PC │    │  capture_uart.py  │              │  push_to_gist.py  │  ║
║  │              │    │  output_combined  │◄─────────────│  HTTPS POST API   │  ║
║  │ decrypt.py   │◄───│  .mem             │              └───────────────────┘  ║
║  │ 100% match   │    └───────────────────┘                                     ║
║  └──────────────┘                                                              ║
║                                                                                ║
╚════════════════════════════════════════════════════════════════════════════════╝
```

---

## ⚡ Phase 1: FPGA Implementation

### Hardware Architecture & RTL Design

**Target Platform:** Xilinx Zynq-7000 SoC (xc7z020clg484-1)

The Zynq-7000 leverages a **Hardware/Software co-design** split:

| Component | Role |
|---|---|
| ARM Cortex-A9 PS | Control flow, UART orchestration, image data management |
| FPGA Programmable Logic (PL) | BFV arithmetic acceleration via custom `bfv_axi_encrypt` IP |
| AXI4-Lite Bus | Memory-mapped register interface between PS and PL |
| DSP48E Slices | Hardware-accelerated modular multiplication |
| Block RAM (BRAM) | Image pixel storage and ciphertext buffering |

### RTL Module Hierarchy

```
bfv_top.v  (Top-Level FSM Controller)
├── bfv_keygen.v           Public key generation: PK₁ = −(a·SK+e) mod q
│   ├── bfv_mod_mult.v     Modular multiplier with Barrett reduction (mod 12289)
│   └── bfv_mod_adder.v    Modular adder with conditional subtraction
│
└── bfv_encrypt_core.v     BFV encryption: C₁, C₂ from plaintext + public key
    ├── bfv_mod_mult.v     (x3 instances: PK₁·u, PK₂·u, Δ·m)
    └── bfv_mod_adder.v    (x3 instances: adder chain for C₁, C₂)
```

| Module | File | Description |
|---|---|---|
| `bfv_top` | `bfv_top.v` | Top-level FSM with pixel BRAM and ciphertext storage |
| `bfv_keygen` | `bfv_keygen.v` | Public key generation |
| `bfv_encrypt_core` | `bfv_encrypt_core.v` | Core encryption arithmetic |
| `bfv_mod_mult` | `bfv_mod_mult.v` | Modular multiplier → DSP48 mapping |
| `bfv_mod_adder` | `bfv_mod_adder.v` | Modular adder (single-cycle) |

---

### Image Preprocessing Pipeline

Raw images are converted to FPGA-compatible `.mem` files using Python:

```python
# Image → 64×64 grayscale → flattened hex → .mem
from PIL import Image
import numpy as np

img = Image.open("image.png").convert('L').resize((64, 64))
pixels = np.array(img).flatten()
# Export as hex for Vivado's $readmemh directive
with open("image_pixels.mem", 'w') as f:
    for pixel in pixels:
        f.write(f"{pixel:02x}\n")
```

**Pipeline stages:**
1. Load image in any format
2. Convert to `'L'` mode (8-bit grayscale, range 0–255)
3. Resize to 64×64 (N = 4096 coefficients, matching polynomial degree)
4. Flatten to 1D array
5. Export as hex `.mem` file for `$readmemh` in Vivado

---

### FSM Implementation

The encryption FSM is a **7-state Moore machine** that drives a single shared combinatorial BFV core through all 4096 pixels sequentially, achieving an optimal area-time tradeoff:

```
S_IDLE ──start──► S_KEYGEN ──► S_LOAD_PIX ──► S_COMPUTE
                                    ▲                │
                              pix_cnt++              ▼
                              S_NEXT_PIX ◄── S_STORE_CT
                                  │
                            pix_cnt==4095
                                  │
                                  ▼
                               S_DONE
```

| State | Action |
|---|---|
| `S_IDLE` | Wait for `start` signal |
| `S_KEYGEN` | Register PK₁, PK₂; reset pixel counter |
| `S_LOAD_PIX` | Latch current pixel from BRAM |
| `S_COMPUTE` | Wait 1 cycle for combinatorial logic to settle |
| `S_STORE_CT` | Write {C₁, C₂} as 28-bit packed word to BRAM |
| `S_NEXT_PIX` | Increment counter or transition to DONE |
| `S_DONE` | Assert `done = 1` |

**Performance:** 16,386 total clock cycles → **≈164µs at 100 MHz**

---

### Modular Arithmetic Units

#### Modular Adder (`bfv_mod_adder.v`)
Single-cycle conditional subtraction:
```
result = (a + b >= Q) ? (a + b - Q) : (a + b)
```
- Zero pipeline latency (combinatorial)
- 15-bit sum computed, Q subtracted conditionally

#### Modular Multiplier (`bfv_mod_mult.v`)
14-bit × 14-bit → 28-bit product with modulo Q reduction:
```
product = a * b          // 28-bit
result  = product % Q    // Vivado maps to DSP48E slices
```
- Vivado automatically infers **DSP48E** blocks from the `*` operator
- Uses Barrett reduction variant

---

### Vivado Block Design & AXI Integration

The ZYNQ7 Processing System communicates with the custom `bfv_axi_encrypt` IP via a **32-bit AXI4-Lite bus**, providing memory-mapped access to:

| Register | Address Offset | Function |
|---|---|---|
| CTRL | 0x00 | Start encryption (`bit[0] = 1`) |
| STATUS | 0x04 | Done flag (`bit[0]` when complete) |
| SK | 0x08 | Secret key value |
| A_KEY | 0x0C | Random polynomial `a` for keygen |
| E_KEY | 0x10 | Error polynomial `e` for keygen |
| CT_DATA | 0x14+ | Read ciphertext output registers |

The AXI wrapper isolates pure mathematical FSM logic from bus protocol handling — the BFV arithmetic core is **completely agnostic** of AXI.

---

### Behavioral Simulation & Verification

RTL simulation was performed in **Vivado Simulator** before physical implementation:

```tcl
# Testbench setup
$readmemh("image_pixels.mem", dut.pixel_mem);
rst_n = 0; start = 0;
sk = 14'd1; a_key = 14'd9847; e_key = 14'd3;
```

Verification checks:
- ✅ FSM state transitions correct
- ✅ LFSR generates non-repeating ternary ephemeral keys
- ✅ Ciphertext pairs (C₁, C₂) within valid Zq range
- ✅ Noise constraint `‖v‖ < Q/2T = 24` maintained

---

### FPGA Implementation Results

#### Performance Summary

| Metric | Encryption Core | Decryption Core |
|---|---|---|
| **Target Device** | xc7z020clg484-1 (Zynq-7000) | Same |
| **Clock Frequency** | 33.333 MHz (30.0 ns period) | Same |
| **LUTs** | 1,249 | 571 |
| **Flip-Flops (FFs)** | 688 | 676 |
| **DSP Slices (DSP48E)** | **3** | **1** |
| **Block RAM** | 0.0 | 0.0 |
| **Total On-Chip Power** | 1.678 W | 1.701 W |
| **WNS** | 1.627 ns ✅ MET | 17.370 ns ✅ MET |
| **WHS** | 0.061 ns ✅ MET | 0.067 ns ✅ MET |
| **Critical Path Delay** | 28.373 ns | 12.630 ns |
| **Actual Max Frequency** | **35.24 MHz** | **79.18 MHz** |
| **Timing Margin** | 5.4% | 57.9% |
| **Encryption Latency** | ≈164µs (16,386 clocks) | — |
| **Pixel Recovery** | **4096/4096 (100%)** | — |

#### Critical Path Analysis

- **Encryption (tight, 5.4% margin):** Critical path traverses two sequential modular multiplications (`a·SK` and `Δ·m`) mapped to 3 DSP48 slices — dense logic chain limits maximum frequency to 35.24 MHz.
- **Decryption (comfortable, 57.9% margin):** 3-stage pipeline breaks `(C₁ + C₂·SK)` into sequential steps aligned with a single DSP48 slice — maximum frequency 79.18 MHz.

---

### Vitis Bare-Metal Application

The ARM Cortex-A9 bare-metal C application (Vitis IDE) orchestrates:

1. Load image data from embedded C header (`image_data.h`)
2. Write pixel data to BFV encryption IP registers via AXI-Lite
3. Assert `start` signal
4. Poll `done` interrupt flag
5. Read ciphertext registers sequentially
6. Transmit 28-bit hex ciphertext over **UART @ 115200 baud**

```c
// UART transmission format
printf("%%BFV_START%%\n");
for (int i = 0; i < N_PIXELS; i++) {
    uint32_t combined = read_cipher(i);   // 28-bit {C1[13:0], C2[13:0]}
    printf("%07x\n", combined);
}
printf("%%BFV_END%%\n");
```

---

### Cloud Transfer Pipeline

Three sequential stages bridge the FPGA to the cloud:

```
Stage 1: UART Capture          Stage 2: Cloud Upload         Stage 3: Recipient Download
┌──────────────────────┐       ┌─────────────────────┐      ┌──────────────────────────┐
│ capture_uart.py      │       │ push_to_gist.py     │      │ decrypt_verify.py        │
│                      │       │                     │      │                          │
│ • Listen on serial   │──────►│ • HTTPS POST to     │────► │ • Download from Gist URL │
│ • Detect %BFV_START% │       │   GitHub Gist API   │      │ • Run BFV decryption     │
│ • Capture 4096 lines │       │ • TLS-encrypted     │      │ • Verify 100% match      │
│ • Save .mem file     │       │ • Data stays        │      │ • Reconstruct image      │
│ • Inline verify      │       │   encrypted         │      │                          │
└──────────────────────┘       └─────────────────────┘      └──────────────────────────┘
```

**Security guarantee:** The cloud provider (GitHub) **cannot** intercept, interpret, or reverse-engineer the underlying pixel data — the FPGA encrypts locally before any network transmission.

---

### Decryption Core

The decryption core operates on the receiver's FPGA board:

```
C₁, C₂ → inner product → scale & round → recovered pixel m
```

```
inner = (C₁ + C₂ · SK) mod Q
m     = ⌊(inner · T + ⌊Q/2⌋) / Q⌋  mod T
```

**Difference from encryption:** No noise generation (e₁, e₂ terms absent) — the design is **significantly less area-intensive**, using only 1 DSP48 slice vs. 3 for encryption.

#### Security Verification (Wrong Key Test)

When an incorrect secret key is used (SK_incorrect ≠ SK_correct), accumulated computational noise overflows the plaintext space — the output degrades into **uniform mathematical randomness** (0–255), completely destroying any geometric pattern. This empirically validates **semantic security**.

---

## 🏭 Phase 2: ASIC SoC Design (RTL → GDSII)

### Design Flow Overview

The FPGA-validated RTL was migrated to a full **silicon-ready ASIC design** using the Cadence Digital Design Bundle from the **C2S program via ChipIN @ C-DAC**:

```
BFV RTL Verilog
      │
      ▼
┌─────────────────────────────────────────────────────────┐
│  1. Cadence NCLaunch    Pre-synthesis RTL simulation    │
│  2. Cadence Genus 20.11 Logic synthesis → Gate netlist  │
│  3. Cadence Innovus 20.14 P&R → GDSII export            │
└─────────────────────────────────────────────────────────┘
      │              │               │
      ▼              ▼               ▼
  GPDK180         GPDK090      Physical Design
  (180nm)         (90nm)       Floorplan → Power
  GSC Lib         GSC Lib      CTS → Route → GDSII
```

### Pipelined FSM for ASIC

The FPGA 7-state FSM was expanded to **11 states** by introducing pipeline wait states to allow modular multiplier settling time at 100 MHz on slower standard-cell libraries:

```
IDLE → KEYGEN_W1 → KEYGEN_W2 → KEYGEN → LOAD_PIX
                                              │
                                        COMPUTE_1
                                              │
                                        COMPUTE_2
                                              │
                                        COMPUTE_3
                                              │
                                        STORE_CT → NEXT_PIX → DONE
```

### SoC Design Parameters

| Parameter | Symbol | Value |
|---|---|---|
| Coefficient Word Width | W | 14 bits |
| Ciphertext Modulus | Q | 12289 |
| Plaintext Width | MSG_W | 8 bits |
| Plaintext Modulus | T | 256 |
| Number of Pixels | N_PIX | 4096 |
| Address Width | ADDR_W | 12 bits |
| Target Clock Period | — | 10 ns (100 MHz) |

### SDC Timing Constraints

```tcl
create_clock -name clk -period 10.0 [get_ports clk]
set_clock_uncertainty -setup 0.2 [get_clocks clk]
set_clock_uncertainty -hold  0.1 [get_clocks clk]
set_clock_transition       0.2 [get_clocks clk]
set_input_delay  0.5 -max -clock clk [all_inputs_except_clk]
set_input_delay  0.1 -min -clock clk [all_inputs_except_clk]
set_output_delay 0.5 -max -clock clk [all_outputs]
set_output_delay 0.1 -min -clock clk [all_outputs]
set_load 2.0 [all_outputs]
```

---

### 180nm Synthesis Results (Cadence Genus)

**Library:** GSC Lib (Cadence Generic Standard Cell) · **GPDK180** · Slow corner · Balanced tree optimization

| Metric | Value |
|---|---|
| Cell Count | **2,592** |
| Total Cell Area | **43,582.49 µm²** |
| Sequential Cells | 103 (15.9% area) |
| Logic Cells | 1,950 (73.6% area) |
| Inverters | 493 (8.1% area) |
| Buffers | 46 (2.4% area) |
| **Total Power** | **7.42 mW** |
| Leakage Power | 1.23 µW (0.02%) |
| Internal Power | 2.89 mW (39.0%) |
| Switching Power | 4.53 mW (61.0%) |
| WNS | **0.000 ns ✅ MET** |
| Critical Path Delay | 9.544 ns |
| **Actual Clock Frequency** | **104.78 MHz** |

---

### 90nm Synthesis Results (Cadence Genus)

**Library:** GSC Lib (Cadence Generic Standard Cell) · **GPDK090** · Slow corner

| Metric | Value | vs 180nm |
|---|---|---|
| Cell Count | **2,153** | 16.9% fewer ⬇️ |
| Total Cell Area | **12,789.34 µm²** | **70.6% reduction** ⬇️ |
| **Total Power** | **1.45 mW** | **80.5% reduction** ⬇️ |
| Leakage Power | 53.05 µW (3.66%) | Higher (expected) |
| Internal Power | 0.70 mW (48.2%) | — |
| Switching Power | 0.70 mW (48.1%) | — |
| WNS | **0.000 ns ✅ MET** | — |
| Critical Path Delay | 9.741 ns | Slightly relaxed |
| **Actual Clock Frequency** | **102.66 MHz** | — |

---

### Technology Node Comparison

| Metric | FPGA Enc | FPGA Dec | ASIC 180nm | ASIC 90nm |
|---|---|---|---|---|
| Theoretical Clock | 33.33 MHz | 33.33 MHz | 100 MHz | 100 MHz |
| Cell Count | 1,249 LUTs | 571 LUTs | 2,592 | 2,153 |
| Seq. Elements | 688 FFs | 676 FFs | 103 | — |
| DSP/Multipliers | 3 DSP48 | 1 DSP48 | N/A | N/A |
| **Total Power** | **1.678 W** | **1.701 W** | **7.42 mW** | **1.45 mW** |
| WNS | 1.627 ns | 17.370 ns | 0.000 ns | 0.000 ns |
| Critical Path | 28.373 ns | 12.630 ns | 9.544 ns | 9.741 ns |
| **Max Frequency** | **35.24 MHz** | **79.18 MHz** | **104.78 MHz** | **102.66 MHz** |
| Timing Margin | 5.4% | 57.9% | 0.0% | 0.0% |

> **Note:** FPGA power (1.6W+) includes entire Zynq-7000 SoC static power. ASIC power (mW range) reflects only the BFV IP core at the target process node — a ~230× improvement in core power efficiency.

---

### Physical Design – Cadence Innovus (180nm)

Full P&R using **Cadence Innovus 20.14** with GPDK180 GSC Lib:

| Parameter | Value |
|---|---|
| Core Utilization | ≈ 70% |
| Aspect Ratio | 1.0 (square die) |
| Power Structure | VDD/VSS ring + stripes |
| Clock Tree | Balanced CTS (100 MHz) |
| Routing | NanoRoute (multi-layer) |

**P&R Flow:**
```
1. Floorplan      → Define core area, aspect ratio 1.0, ~70% utilization
2. Power Network  → VDD/VSS ring around core + horizontal/vertical stripes
3. Placement      → Standard cell placement with timing-driven optimization
4. CTS            → Clock tree synthesis, balanced distribution at 100 MHz
5. Special Route  → Power network routing (sroute)
6. NanoRoute      → Detailed multi-layer signal routing
7. GDSII Export   → bfv_top_180_gds.gds (2.3 MB)
```

---

### Signoff Verification

All physical design signoff checks **passed cleanly**:

| Check | Result | Details |
|---|---|---|
| **Design Rule Check (DRC)** | ✅ **PASS** | No DRC violations found |
| **Connectivity Verification** | ✅ **PASS** | No problems or warnings |
| **Antenna Check** | ✅ **PASS** | No violations found |

Final GDSII: `bfv_top_180_gds.gds` — **2.3 MB, tape-out ready**

---

## 🌐 BFV Encryption Gateway – Web Application

A dedicated full-stack web portal provides a modern client-side interface for the encrypted image transfer workflow.

> ⚠️ **Note:** The web app interfaces **only** with the cloud storage layer (Supabase/GitHub). All BFV encryption and decryption is performed exclusively on FPGA/ASIC hardware.

### Technology Stack

| Component | Technology |
|---|---|
| Frontend Framework | Next.js 14 (React 18) |
| Styling | Tailwind CSS 3 |
| Backend API | Next.js API Routes |
| Database ORM | Prisma (PostgreSQL) |
| Cloud Storage | Supabase Storage (TLS-encrypted) |
| Authentication | Custom JWT with role management |
| Deployment | Netlify (Serverless) |
| Language | TypeScript |

### Architecture

```
┌──────────────────────────────────────────────────────────────────┐
│                    BFV ENCRYPTION GATEWAY                        │
├──────────────────────────────────────────────────────────────────┤
│                                                                  │
│  USER PORTAL            ADMIN GATEWAY          RECEIVER ACCESS   │
│  ┌──────────────┐       ┌─────────────┐        ┌──────────────┐  │
│  │ • Authenticate│      │ • Pipeline  │        │ • Download   │  │
│  │ • Submit img  │      │   health    │        │   .mem files │  │
│  │ • Track tasks │      │ • Fulfill   │        │ • Get cipher │  │
│  │   Pending→    │      │   payloads  │        │   keys       │  │
│  │   Processed→  │      │ • Upload    │        │ • No raw img │  │
│  │   Downloaded  │      │   .mem files│        │   access     │  │
│  └───────────────┘      └─────────────┘        └──────────────┘  │
│                                                                  │
│  TASK LIFECYCLE:  Pending → Processing → Processed → Downloaded  │
└──────────────────────────────────────────────────────────────────┘
```

### Security Features

| Feature | Implementation |
|---|---|
| **Homomorphic Encryption** | Data remains ciphertext during all cloud operations |
| **Strict Tenant Isolation** | Senders cannot access processed files; receivers cannot see raw inputs |
| **Secure Transport** | All transitions TLS-wrapped; Supabase row-level security |
| **RBAC** | Asymmetric access enforced: User / Admin / Receiver roles |
| **Identity Verification** | Recipient must be verified via directory search before transfer authorized |

### Live Resources

| Resource | Link |
|---|---|
| 🌐 Live Portal | [bfv-encryption-gateway.netlify.app](https://bfv-encryption-gateway.netlify.app/) |
| 💻 Web Interface Repo | [github.com/sohan2311/BFV-Homomorphic-Encryption-of-Image-using-Cloud](https://github.com/sohan2311/BFV-Homomorphic-Encryption-of-Image-using-Cloud) |

---

## 📊 Consolidated Results

### FPGA Implementation Summary

| Metric | Encryption Core | Decryption Core |
|---|---|---|
| IP Core | `bfv_axi_encrypt` | `bfv_axi_decrypt` |
| LUTs | 1,249 | 571 |
| Flip-Flops | 688 | 676 |
| DSP48E Slices | **3** | **1** |
| On-Chip Power | 1.678 W | 1.701 W |
| WNS | 1.627 ns ✅ | 17.370 ns ✅ |
| Critical Path | 28.373 ns | 12.630 ns |
| Max Frequency | **35.24 MHz** | **79.18 MHz** |
| Timing Margin | 5.4% | 57.9% |
| Processing Time | ≈164 µs | — |
| Pixel Recovery | **4096/4096 (100%)** | — |
| Ciphertext Format | 28-bit packed {C₁[13:0], C₂[13:0]} | — |
| UART Baud Rate | 115200 bps | — |

### ASIC Synthesis Comparison

| Metric | ASIC 180nm | ASIC 90nm | Improvement |
|---|---|---|---|
| Cell Count | 2,592 | 2,153 | 16.9% fewer |
| Total Area | 43,582 µm² | 12,789 µm² | **70.6% reduction** |
| Total Power | 7.42 mW | 1.45 mW | **80.5% reduction** |
| Max Frequency | 104.78 MHz | 102.66 MHz | Both >100 MHz |
| WNS | 0.000 ns ✅ | 0.000 ns ✅ | Both clean |

---

## 🌍 Applications

| Domain | Application |
|---|---|
| 🏥 **Medical Imaging** | Hospitals transmit X-ray/MRI/CT to cloud AI diagnostics without exposing patient data (HIPAA compliant) |
| 🛰️ **Satellite/Defence** | Classified reconnaissance images processed on untrusted infrastructure for object detection |
| 👤 **Facial Recognition** | Biometric data processed for authentication without exposing actual face images (GDPR compliant) |
| 🏭 **Secure IoT** | Industrial visual inspection sensors encrypt at edge before cloud analytics offload |
| 🏦 **Financial Documents** | Cheque/signature images encrypted before cloud OCR and fraud detection |
| 🚗 **Autonomous Vehicles** | Real-time camera feeds encrypted before cloud perception model training |
| 🤖 **MLaaS** | Cloud ML inference on encrypted data — clients use powerful models without revealing datasets |
| 🚁 **Drone Surveillance** | Encrypted aerial imagery transmitted to command centres without interception risk |

---

## 🔮 Conclusion & Future Work

### Conclusion

This project successfully bridged **theoretical cryptography, VLSI design, and modern cloud architecture** through a comprehensive two-phase approach:

**Phase 1 (FPGA):** Fully functional BFV homomorphic encryption system on Xilinx Zynq-7000. Custom AXI4-Lite IP core encrypts 4096 pixels in ~164µs, transmits 28-bit ciphertexts over UART, uploads to GitHub Gists via HTTPS. Decryption pipeline achieved **100% pixel-perfect recovery with zero data loss.**

**Phase 2 (ASIC):** FPGA-validated RTL migrated to full ASIC flow using Cadence Genus + Innovus. Successful synthesis on both GPDK180 (43,582 µm², 7.42 mW, 104.78 MHz) and GPDK090 (12,789 µm², 1.45 mW, 102.66 MHz) at 100 MHz target with **zero WNS**. All DRC, Connectivity, and Antenna checks passed cleanly.

### Future Work

1. **ASIC Tape-Out** — Submit GDSII for fabrication as standalone edge-device SoC chip
2. **Higher Resolution** — Scale polynomial degree N for 128×128 (16K pixels) and 256×256 (65K pixels) with external DRAM
3. **Color Image Support** — RGB support via 3× parallel BFV cores (3 channels × 8 bits)
4. **NTT-Based Polynomial Multiplication** — Replace coefficient-level with NTT for batched homomorphic operations
5. **Ethernet TCP/IP** — Add Ethernet MAC IP for direct network transmission, eliminating UART/host PC bridge
6. **Actual Homomorphic Cloud Computation** — Implement HE addition/multiplication on cloud side for encrypted image filtering
7. **5nm/7nm Migration** — FinFET nodes for >1 GHz operation and sub-milliwatt power
8. **TRNG Integration** — Replace LFSR with True Random Number Generator for production-grade security
9. **Real-Time Video** — Frame-level pipelining with double-buffered pixel memories for video encryption

---

## 💻 RTL Source Code

All RTL source code is in the [`rtl/`](./rtl/) directory. See individual files for complete Verilog implementations. Key files:

- [`rtl/encryption/bfv_mod_adder.v`](./rtl/encryption/bfv_mod_adder.v) — Modular adder
- [`rtl/encryption/bfv_mod_mult.v`](./rtl/encryption/bfv_mod_mult.v) — Modular multiplier (DSP48)
- [`rtl/encryption/bfv_keygen.v`](./rtl/encryption/bfv_keygen.v) — Key generation
- [`rtl/encryption/bfv_encrypt_core.v`](./rtl/encryption/bfv_encrypt_core.v) — Encryption core
- [`rtl/encryption/bfv_top.v`](./rtl/encryption/bfv_top.v) — Top-level FSM

---

## 🐍 Software Scripts

- [`software/preprocessing/image_converter.py`](./software/preprocessing/image_converter.py) — Image → `.mem`
- [`software/preprocessing/convert_image.py`](./software/preprocessing/convert_image.py) — `.mem` → C header
- [`software/cloud/capture_uart.py`](./software/cloud/capture_uart.py) — UART capture daemon
- [`software/cloud/push_to_gist.py`](./software/cloud/push_to_gist.py) — GitHub Gist upload
- [`software/cloud/decrypt_verify.py`](./software/cloud/decrypt_verify.py) — BFV decryption and verification

---

## ⚙️ ASIC Scripts

- [`asic/synthesis/run_genus_pipelined_180.tcl`](./asic/synthesis/run_genus_pipelined_180.tcl) — 180nm synthesis
- [`asic/synthesis/run_genus_pipelined_90.tcl`](./asic/synthesis/run_genus_pipelined_90.tcl) — 90nm synthesis
- [`asic/synthesis/bfv_pipelined_180nm.sdc`](./asic/synthesis/bfv_pipelined_180nm.sdc) — Timing constraints
- [`asic/simulation/tb_bfv_top.v`](./asic/simulation/tb_bfv_top.v) — ASIC testbench

---

## 🛠️ Setup & Usage Guide

### Prerequisites

| Tool | Version | Purpose |
|---|---|---|
| Xilinx Vivado | 2020.2+ | FPGA synthesis, implementation, simulation |
| Xilinx Vitis | 2020.2+ | Bare-metal ARM application development |
| Python | 3.8+ | Image preprocessing and cloud scripts |
| Cadence Genus | 20.11 | ASIC logic synthesis |
| Cadence Innovus | 20.14 | ASIC physical design |
| Cadence NCLaunch | — | Pre-synthesis RTL simulation |

### Python Dependencies

```bash
pip install numpy pillow pyserial requests
```

### Step-by-Step FPGA Flow

```bash
# Step 1: Preprocess image
python software/preprocessing/image_converter.py input.png image_pixels.mem

# Step 2: Convert to Vitis C header
python software/preprocessing/convert_image.py
# Generates: image_data.h

# Step 3: Open Vivado, create project
#   - Add all RTL files from rtl/encryption/
#   - Add image_pixels.mem as simulation source
#   - Package bfv_top.v as AXI4-Lite IP
#   - Create block design: ZYNQ PS + AXI Interconnect + BFV IP
#   - Add constraints from constraints/bfv_fpga.xdc

# Step 4: Run synthesis, implementation, generate bitstream
# Step 5: Export hardware (.xsa) for Vitis

# Step 6: In Vitis, create bare-metal application
#   - Copy image_data.h to project
#   - Build bfv_encrypt_app.c

# Step 7: Program FPGA and run application
# Step 8: On PC, capture UART output
python software/cloud/capture_uart.py
# Generates: received/output_combined.mem

# Step 9: Upload to cloud
python software/cloud/push_to_gist.py
# Outputs GitHub Gist URL

# Step 10: Verify decryption
python software/cloud/decrypt_verify.py received/output_combined.mem image_pixels.mem
# Expected: RESULT: 4096/4096 pixels correct — PERFECT MATCH!
```

### Step-by-Step ASIC Flow (180nm)

```bash
# Prerequisites: Cadence tools + GPDK180 library installed
# C2S program via ChipIN @ C-DAC access required

# Step 1: Pre-synthesis simulation
# Launch NCLaunch, add all RTL files + testbench, simulate

# Step 2: Logic synthesis
cd asic/synthesis
genus -f run_genus_pipelined_180.tcl
# Outputs: bfv_180nm_pipelined_netlist.v, timing/power/area reports

# Step 3: Physical design
# Launch Innovus, source innovus_flow.tcl
# Stages: floorplan → power → placement → CTS → route → signoff → GDSII
```

---

## 📚 References

1. Inferati Inc. *"Introduction to the BFV FHE Scheme."* Washington, USA.
2. Mareta, R., Satriawan, A., Lee, H. (2025). *"High Throughput Arithmetic Computing Unit for BFV Homomorphic Encryption."* IEEE OJCAS. DOI: 10.1109/OJCAS.2025.3581188
3. Amdouni, R., et al. (2024). *"FPGA Implementation of Robust and Secure Transmission Cryptosystem for Satellite Images."* IEEE Access. DOI: 10.1109/ACCESS.2024.3444732
4. Brakerski, Z. (2012). *"Fully Homomorphic Encryption without Bootstrapping."* ECCC.
5. Fan, J., Vercauteren, F. (2012). *"Somewhat Homomorphic Encryption over Zq."* Cryptology ePrint Archive.
6. Gentry, C. (2009). *"Fully Homomorphic Encryption Using Ideal Lattices."* ACM STOC.
7. Microsoft SEAL (v4.1). *"Simple Encrypted Arithmetic Library."* [github.com/microsoft/SEAL](https://github.com/microsoft/SEAL)
8. Roy, S.S., Vercauteren, F. (2020). *"NTRU and BFV on the Zynq-7000 SoC."* J. Cryptographic Engineering.
9. Xilinx Inc. (2021). *"Zynq-7000 SoC Data Sheet: Overview."* DS190.
10. Cadence Design Systems. (2020). *"Genus Synthesis Solution User Guide."*
11. Cadence Design Systems. (2020). *"Innovus Implementation System User Guide."*
12. Cousins, D.B., Rohloff, K. (2017). *"A Scalable Architecture for Homomorphic Encryption."* IEEE HPEC.
13. Mert, A.C., et al. (2020). *"Highly Parallel NTT-based Accelerator for BFV."* IEEE ISCAS.
14. Öztürk, E., et al. (2015). *"A Retargetable Accelerator for Homomorphic Encryption."* IEEE TVLSI.
15. Cadence Design Systems. *"GPDK090 and GPDK180 Standard Cell Libraries — C2S Program via ChipIN @ C-DAC."*

---

<div align="center">

**Made with ❤️ at Indian Institute of Information Technology Design and Manufacturing, Kurnool · Electronics & Communications Engineering**

*Product Design Practise (ID-351) · March 2026*

---

*"Compute on what you cannot see — BFV makes the invisible computable."*

</div>
