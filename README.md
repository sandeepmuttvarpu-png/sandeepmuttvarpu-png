<div align="center">

# 🥪 Sandeep Muttvarpu
### Systems & High-Performance Inference Engineer | Creator of [Sandwich.cpp](https://github.com/sandeepmuttvarpu-png/Sandwich-cpp)

*"Democratizing 100B+ MoE and 128k-context local inference on budget 8GB workstations. Zero OOM. Zero compromise."*

<p align="center">
  <img src="https://readme-typing-svg.demolab.com?font=Fira+Code&pause=1000&color=58A6FF&center=true&vCenter=true&width=640&lines=Optimizing+CUDA+kernels+down+to+the+warp+registers...%3BShattering+the+128k+context+barrier+on+8GB+VRAM...%3B3-Tier+MoE+streaming%3A+GDDR6+-%3E+DDR5+THP+-%3E+NVMe+io_uring...%3BExact+unit-variance+norm+conservation%3A+%7C%7Cv%7C%7C%5E2+equiv+%7C%7Cv%7C%7C%5E2..." alt="Dynamic Terminal Typing Tagline" />
</p>

---

<!-- Sandwich.cpp Core Badges -->
[![Sandwich.cpp Core](https://img.shields.io/badge/Project-Sandwich.cpp-brightgreen?style=for-the-badge&logo=c%2B%2B)](https://github.com/sandeepmuttvarpu-png/Sandwich-cpp)
[![54 Active Techniques](https://img.shields.io/badge/Techniques-54%20Active%20%E2%9A%A1-orange?style=for-the-badge)](https://github.com/sandeepmuttvarpu-png/Sandwich-cpp)
[![CUDA 13.4 | sm_120](https://img.shields.io/badge/CUDA-13.4%20%7C%20sm__120%20Blackwell-green?style=for-the-badge&logo=nvidia)](https://developer.nvidia.com/cuda-toolkit)
[![Context: 128k Verified](https://img.shields.io/badge/Context-128k%20Verified%20%F0%9F%A7%A0-blueviolet?style=for-the-badge)](https://github.com/sandeepmuttvarpu-png/Sandwich-cpp)
[![VRAM: 8GB Friendly](https://img.shields.io/badge/VRAM-8GB%20Friendly%20%F0%9F%92%AA-76B900?style=for-the-badge&logo=nvidia)](https://github.com/sandeepmuttvarpu-png/Sandwich-cpp)
[![KV Quant: TurboQuant](https://img.shields.io/badge/KV%20Cache-TurboQuant%204b%2F3b%2F2b-blue?style=for-the-badge)](https://github.com/sandeepmuttvarpu-png/Sandwich-cpp)
[![Norm Conservation](https://img.shields.io/badge/Scale%20Invariance---turboquant--varn-cyan?style=for-the-badge)](https://github.com/sandeepmuttvarpu-png/Sandwich-cpp)
[![MoE Engine](https://img.shields.io/badge/MoE-Phase%2012%203--Tier%20Hierarchy-red?style=for-the-badge)](https://github.com/sandeepmuttvarpu-png/Sandwich-cpp)
[![Throughput: 35+ tok/s](https://img.shields.io/badge/Throughput-35%2B%20tok%2Fs%20MoE-critical?style=for-the-badge)](https://github.com/sandeepmuttvarpu-png/Sandwich-cpp)
[![Whitepaper: v5.0](https://img.shields.io/badge/Whitepaper-v5.0%20Systems%20Edition-success?style=for-the-badge)](https://github.com/sandeepmuttvarpu-png/Sandwich-cpp)

</div>

---

## 🥪 Flagship Research & Development: [Sandwich.cpp](https://github.com/sandeepmuttvarpu-png/Sandwich-cpp)

**Sandwich.cpp** is a standalone, hardware-aware C++/CUDA inference engine designed to shatter the memory wall on budget laptops and consumer workstations, enabling multi-billion parameter models and massive 128k context windows on an **8GB laptop GPU**.

### ⚡ Architectural Breakthroughs
* **Asymmetric Split-KV & The 70% RAM Rule**: Eliminates PCIe roundtrip latency serialization on dense models. Pushes 100% of weights to host DDR5 (AVX2-VNNI P-cores) and reserves 100% of GPU VRAM strictly for FlashAttention, speculative drafters, and the KV cache.
* **Phase 12 3-Tier Hierarchical MoE Engine**: Dynamic three-tier storage orchestrator: **Tier 1 HOT VRAM** (GDDR6 @ 288 GB/s) $\to$ **Tier 2 WARM DDR5** (2MB Transparent HugePages @ 50 GB/s) $\to$ **Tier 3 COLD NVMe** (Linux kernel `io_uring` direct asynchronous DMA @ 7,000 MB/s). Powers **GPT-OSS-120B** on an 8GB mobile GPU.
* **TurboQuant Polar Lloyd-Max KV Cache**: Compresses KV states up to $8\times$ (`turbo4`, `turbo3`, `turbo2`) utilizing orthonormal Walsh-Hadamard pre-rotation to eliminate outlier channel distortion.
* **Closed-Form Dual-Axis Variance Normalization (`--turboquant-varn`)**: Solves long-horizon reasoning drift across 10k–32k token CoT chains by enforcing exact unit-variance norm conservation ($\|\hat{\mathbf{v}}\|^2 \equiv \|\mathbf{v}\|^2$) on-the-fly via 4-warp butterfly shuffle reduction.
* **1,140 Verified Benchmark Corpus**: Formally compiled and peer-reviewed in the [v5.0 Academic Systems Whitepaper](https://github.com/sandeepmuttvarpu-png/Sandwich-cpp).

### 🔬 System Architecture Blueprint (Phase 12 3-Tier Hierarchy & Split-KV)

```text
  ┌────────────────────────────────────────────────────────────────────────┐
  │ TIER 1: HOT VRAM (8GB GDDR6 @ 288 GB/s — sm_120 Blackwell)             │
  │  • Pinned Router Gates (W_gate) & Shared Experts across ALL Layers     │
  │  • TurboQuant KV Cache (turbo4/turbo2) + Native FlashMLA Attention     │
  │  • Resident 2Q Active Expert Slab (Am Frequent | A1in Probation)       │
  └───────────────────────────────────┬────────────────────────────────────┘
                                      ▲ PCIe 4.0 DMA Ring (28 GB/s)
  ┌───────────────────────────────────┴────────────────────────────────────┐
  │ TIER 2: WARM DDR5 (24GB @ 50 GB/s — 2MB Transparent HugePages)         │
  │  • 10–12 GB Buffer Pool & Fast O(1) Slab Manager (A1out Ghost Table)   │
  │  • 100% Dense Model Weights under Asymmetric Split-KV (AVX2-VNNI)      │
  └───────────────────────────────────┬────────────────────────────────────┘
                                      ▲ Linux Kernel io_uring (7,000 MB/s)
  ┌───────────────────────────────────┴────────────────────────────────────┐
  │ TIER 3: COLD NVMe (PCIe 4.0 x4 SSD — Zero-Copy Direct Kernel DMA)      │
  │  • Immutable GGUF Shards; asynchronous page eviction without stalls    │
  └────────────────────────────────────────────────────────────────────────┘
```

---

## 📄 Academic Research & Systems Whitepaper (v5.0)

> **"Project Sandwich: An Asymmetric Memory Hierarchy and Polar-Quantized Engine for Ultra-Long Context (128K) LLM Inference on Budget Workstations"**  
> *Sandeep Muttvarpu & The Project Sandwich Research Team (October 2026)*

* **The 1,140 Data Point Corpus**: Evaluated across 11 heavyweight architectures (Qwen3.6-35B, DeepSeek-Coder-V2-Lite, Command R 35B, Gemma-4-31B, GPT-OSS-120B) across 6 context tiers up to 128,000 tokens with zero OOM faults.
* **Exact Norm Conservation**: Eliminates spurious attention sinks in deep reasoning chains via Closed-Form Dual-Axis Variance Normalization ($\|\hat{\mathbf{v}}\|^2 \equiv \|\mathbf{v}\|^2$).
* **Available Formats**: [Full Markdown Systems Paper](https://github.com/sandeepmuttvarpu-png/Sandwich-cpp/blob/main/docs/whitepaper.md) • Synchronized Word (DOCX) & PDF Corpus.

<details>
<summary>📑 <b>Cite this Research (BibTeX)</b></summary>

```bibtex
@article{muttvarpu2026sandwich,
  title={Project Sandwich: An Asymmetric Memory Hierarchy and Polar-Quantized Engine for Ultra-Long Context (128K) LLM Inference on Budget Workstations},
  author={Muttvarpu, Sandeep and Research Team, Project Sandwich},
  journal={Systems Research Preprint},
  volume={5.0},
  year={2026},
  url={https://github.com/sandeepmuttvarpu-png/Sandwich-cpp}
}
```
</details>

---

## 🖥️ Workstation Rig & Benchmark Testbed

```text
  sandeep@victus
  --------------
  OS:       Arch Linux x86_64 (Linux Kernel 6.12, Hyprland Wayland)
  CPU:      13th Gen Intel Core i7-13620H (16 vCPUs, 6P + 4E cores @ up to 4.9 GHz)
  GPU:      NVIDIA GeForce RTX 5050 Mobile (8,151 MiB GDDR6, CC 12.0 Blackwell, CUDA 13.4)
  Memory:   24GB DDR5-5600 MT/s (2MB Transparent HugePages, ~50 GB/s bandwidth)
  Storage:  1TB PCIe 4.0 x4 NVMe SSD (io_uring Direct Kernel DMA @ 7,000 MB/s)
  Topology: Strict 900MB Runtime VRAM Headroom Guard, Worker P-Core Hardware Pinning
```

---

## 🔭 Current Focus & In-Flight Research

* 🔨 **Building**: Blackwell-native NVFP4 / MXFP4 Tensor Core MMA inner loops for sub-2-bit MoE routing.
* 🔬 **Researching**: Zero-latency speculative tree verification with Bayesian multi-drafter arbitration (`--spec-select`).
* ⚡ **Core Philosophy**: Zero-allocation hot paths, hardware-aware cache eviction, and complete local compute sovereignty.
* 💬 **Ask Me About**: CUDA PTX, MoE caching topologies, Walsh-Hadamard polar quantization, FlashMLA, and `io_uring` kernel pipelines.

---

## 🐍 Contribution Activity

<div align="center">

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/sandeepmuttvarpu-png/sandeepmuttvarpu-png/output/github-contribution-grid-snake-dark.svg">
  <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/sandeepmuttvarpu-png/sandeepmuttvarpu-png/output/github-contribution-grid-snake.svg">
  <img alt="GitHub Contribution Grid Snake" src="https://raw.githubusercontent.com/sandeepmuttvarpu-png/sandeepmuttvarpu-png/output/github-contribution-grid-snake.svg">
</picture>

[![Generate Contribution Snake](https://github.com/sandeepmuttvarpu-png/sandeepmuttvarpu-png/actions/workflows/snake.yml/badge.svg)](https://github.com/sandeepmuttvarpu-png/sandeepmuttvarpu-png/actions/workflows/snake.yml)

</div>

---

## ⚡ GitHub Analytics & Streaks

<div align="center">

<!-- GitHub Readme Streak Stats -->
<a href="https://github.com/sandeepmuttvarpu-png">
  <img src="https://streak-stats.demolab.com/?user=sandeepmuttvarpu-png&theme=tokyonight&hide_border=true&background=0D1117" alt="GitHub Streak Stats" />
</a>

<br><br>

<!-- GitHub Stats & Top Languages Cards -->
<a href="https://github.com/sandeepmuttvarpu-png">
  <img src="https://github-readme-stats.vercel.app/api?username=sandeepmuttvarpu-png&show_icons=true&theme=tokyonight&hide_border=true&bg_color=0D1117&title_color=58A6FF&icon_color=79C0FF&text_color=C9D1D9" alt="GitHub Profile Stats" height="175" />
</a>
<a href="https://github.com/sandeepmuttvarpu-png">
  <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=sandeepmuttvarpu-png&layout=compact&theme=tokyonight&hide_border=true&bg_color=0D1117&title_color=58A6FF&text_color=C9D1D9" alt="Top Languages" height="175" />
</a>

</div>

---

## 🛠️ Technical Arsenal

| Domain | Technologies & Systems |
| :--- | :--- |
| **Low-Level & HPC** | `C++20` • `CUDA (sm_120 Blackwell)` • `Inline PTX` • `AVX2-VNNI` • `Rust` • `Linux io_uring` • `THP (Transparent HugePages)` |
| **Inference & Acceleration** | `ggml/llama.cpp` • `TurboQuant` • `FlashAttention-2 / FlashMLA` • `Speculative Tree Decoding (EAGLE3 / DFlash2)` • `Lloyd-Max Quantization` |
| **Platforms & Tooling** | `Arch Linux` • `CMake` • `NVIDIA Nsight Systems` • `Valgrind` • `GDB` • `Git` • `GitHub Actions` |
| **Hardware Focus** | Edge GPUs (`NVIDIA GeForce RTX 5050 Mobile 8GB GDDR6`), Hybrid Intel CPU topologies (P-core pinning), Pinned Zero-Copy DMA (`cudaHostRegister`) |

---

## 📫 Connect & Collaborate

* **GitHub**: [@sandeepmuttvarpu-png](https://github.com/sandeepmuttvarpu-png)
* **Flagship Project**: [Sandwich-cpp](https://github.com/sandeepmuttvarpu-png/Sandwich-cpp)
* **Email**: [sandeepmuttvarpu@gmail.com](mailto:sandeepmuttvarpu@gmail.com)

<div align="center">
  <sub>Built with relentless focus on systems optimization, zero-allocation kernels, and local compute sovereignty. 🥪🚀</sub>
</div>
