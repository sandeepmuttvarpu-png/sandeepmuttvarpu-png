<div align="center">

# 🥪 Sandeep Muttvarpu
### Systems & High-Performance Inference Engineer | Creator of [Sandwich.cpp](https://github.com/sandeepmuttvarpu-png/Sandwich-cpp)

*"Democratizing 100B+ MoE and 128k-context local inference on budget 8GB workstations. Zero OOM. Zero compromise."*

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
