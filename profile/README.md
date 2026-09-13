# Zircon on Mobile Devices (ZOMD)

> Rethinking mobile computing with a modern, capability-based microkernel under the Zircon On Mobile Devices Initiative.

Welcome to **ZOMD**—an open-source project dedicated to porting Google’s **Zircon microkernel** to ARM64 and next-generation mobile silicon. By decoupling drivers from the kernel and leveraging modern capability-based security, ZOMD delivers a lightweight, secure, and crash-resilient alternative to monolithic mobile platforms.

---

## Project Tiers

### ZOMD (Standard Edition)
Designed for modern smartphones and high-performance mobile computing.
* **Target Hardware:** 4GB+ RAM, ARMv8.2-A+ architecture.
* **Storage Requirement:** **UFS 2.1 Minimum** (UFS 3.1+ Recommended) for full-duplex asynchronous I/O.
* **Graphics & Runtime:** Powered by Fuchsia's **Scenic** Vulkan compositor and native Flutter framework, with optional Linux/Android binary support via the **Starnix** runtime layer.

### ZOMDG (Go Edition)
An ultra-stripped microkernel stack for resource-constrained hardware and minimalist devices.
* **Target Hardware:** 256MB – 512MB RAM target profile.
* **Storage Support:** **eMMC 5.1 supported** alongside SD/UFS.
* **Architecture:** Bypasses heavy abstraction layers in favor of direct 2D framebuffer rendering and native compiled execution. Ideal for feature phones and IoT targets.

---

## Architecture Blueprint
+-------------------------------------------------------------+
|        User Space Apps (Flutter / Native C++ / Rust)       |
+-------------------------------------------------------------+
|        Graphical Pipeline (Scenic Vulkan / 2D Engine)       |
+-------------------------------------------------------------+
|  User-Space Drivers (DFv2 Framework: GPU, Touch, Storage)  |
+-------------------------------------------------------------+
|=================== Zircon Microkernel ======================|
|    Isolated Handles | Threading | Virtual Memory | IPC      |
+-------------------------------------------------------------+
|                  ARM64 / RISC-V Hardware Target             |---

## Technical Roadmap

- [ ] **Phase 1: Bootstrapping & Early Console**
  - Custom PSCI secondary core bring-up.
  - Early UART debug logging (`kernel.serial`).
  - U-Boot / UEFI loader integration for `.zbi` payloads.
- [ ] **Phase 2: Board Support Packages (BSPs)**
  - ARM GICv3 interrupt controller and generic timer setup.
  - SMMUv3 IOMMU domain isolation for peripheral security.
- [ ] **Phase 3: User-Space Drivers (DFv2)**
  - UFS host controller & asynchronous block storage drivers.
  - MIPI-DSI display engine & touch digitizer bindings.
- [ ] **Phase 4: ZOMDG Runtime & Starnix**
  - Ultra-lightweight 2D rendering pipeline for Go targets.
  - Translation layer testing for user-space app execution.

---

## Getting Involved

We are actively seeking hardware hackers, kernel developers, and systems engineers interested in microkernel architectures.

* **GitHub Organization:** [github.com/Zircon-On-Mobile-Devices](https://github.com/Zircon-On-Mobile-Devices)
* **Contributions:** Code, hardware board bring-up reports, and driver pull requests are welcome. Check individual project repositories for contribution guides.

---

*ZOMD is an independent open-source initiative under the Zircon On Mobile Devices Initiative and is not officially affiliated with or endorsed by Google LLC.*
+-------------------------------------------------------------+
