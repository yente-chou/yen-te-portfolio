# Isaac Sim Deployment Issue – Driver Compatibility Case Study

## Overview
This case study documents a real-world issue encountered when deploying NVIDIA Isaac Sim on a laptop environment.

The focus is on identifying and resolving system-level instability caused by GPU driver incompatibility.

---

## Problem
Isaac Sim repeatedly crashed across multiple versions during initialization.

---

## Environment
- Laptop: GIGABYTE A7 K1
- GPU: NVIDIA RTX 3060 Laptop GPU
- iGPU: AMD Radeon Graphics
- OS: Windows 11

---

## Issue
- Application crashed after reaching "app ready"
- Occurred across versions: 5.1.0 / 5.0.0 / 4.5.0 / 4.2.0

---

## Investigation
- Compared multiple Isaac Sim versions
- Analyzed logs and GPU initialization behavior
- Evaluated GPU selection (iGPU vs dGPU)
- Tested different NVIDIA driver versions

---

## Root Cause
NVIDIA driver incompatibility

- 511.81 → initial  
- 595.xx → unstable  
- 537.58 → stable  

---

## Solution
- Downgraded NVIDIA driver to 537.58
- Forced Windows to use RTX 3060 (dGPU)
- Verified GPU-related logs

---

## Hardware Constraint Note
This setup was tested on an RTX 3060 laptop GPU.

Although official recommendations often suggest higher-end GPUs (e.g., RTX 40-series), this experiment was conducted to evaluate practical limits on mid-range hardware.

The system was able to run with some limitations, providing useful insight into performance constraints in simulation environments.

---

## Key Observations
- "app ready" does not guarantee runtime stability
- iGPU interference can impact GPU workloads
- Driver version plays a critical role in simulation stability

---

## Key Learnings
System-level debugging is critical in AI simulation environments.

Issues often originate from interactions between:
- GPU drivers  
- OS configuration  
- Hardware behavior  

This becomes especially important when working toward real-world robotics systems, where stability and reliability are essential.
