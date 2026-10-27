<div align="center">

# 🥪 Sandeep Muttvarpu
### Systems & High-Performance Inference Engineer | Creator of [Sandwich.cpp](https://github.com/sandeepmuttvarpu-png/Sandwich-cpp)

<p align="center">
  <img src="https://readme-typing-svg.demolab.com?font=Fira+Code&pause=1000&color=58A6FF&center=true&vCenter=true&width=640&lines=Optimizing+CUDA+kernels+down+to+the+warp+registers...%3BShattering+the+128k+context+barrier+on+8GB+VRAM...%3B3-Tier+MoE+streaming%3A+GDDR6+-%3E+DDR5+THP+-%3E+NVMe+io_uring...%3BExact+unit-variance+norm+conservation%3A+%7C%7Cv%7C%7C%5E2+equiv+%7C%7Cv%7C%7C%5E2..." alt="Dynamic Terminal Typing Tagline" />
</p>

<!-- Badges -->
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

### ⚡ Overview

* 🥪 **Creator of [Sandwich.cpp](https://github.com/sandeepmuttvarpu-png/Sandwich-cpp)**: Standalone C++/CUDA inference engine breaking the memory wall on budget hardware.
* ⚡ **54 Active Techniques**: Pipelined speculative decoding, AVX2-VNNI P-core vectorization, and zero-allocation CUDA kernels.
* 🧠 **TurboQuant Polar KV Cache**: Up to 8× compression (`turbo4`, `turbo3`, `turbo2`) via Walsh-Hadamard pre-rotation + Lloyd-Max codebooks.
* 📐 **Closed-Form Dual-Axis Variance Normalization**: Eliminates long-horizon reasoning drift with exact norm conservation ($\|\hat{\mathbf{v}}\|^2 \equiv \|\mathbf{v}\|^2$).
* 🚀 **Phase 12 3-Tier MoE Engine**: Dynamic storage hierarchy (GDDR6 VRAM $\to$ DDR5 2MB THP $\to$ NVMe Linux kernel `io_uring` direct DMA).
* 🎯 **Asymmetric Split-KV & 70% RAM Rule**: 100% weights in host DDR5, 100% VRAM dedicated to attention and drafters, 0 PCIe bubbles.
* 📊 **1,140 Verified Benchmark Corpus**: Evaluated across 11 heavyweight models (10B to 117B) up to 128k context on an 8GB laptop GPU.
* 📄 **Academic Systems Whitepaper (v5.0)**: Formal IMRaD systems preprint compiling comprehensive empirical evaluations.
* 🖥️ **Primary Testbed**: Arch Linux • Intel Core i7-13620H (6P+4E) • NVIDIA GeForce RTX 5050 Mobile 8GB GDDR6 (sm_120 Blackwell).
* 📫 **Connect**: Reach out at [sandeepmuttvarpu@gmail.com](mailto:sandeepmuttvarpu@gmail.com) or explore [Sandwich-cpp](https://github.com/sandeepmuttvarpu-png/Sandwich-cpp).

---

### 🐍 Contribution Activity

<div align="center">

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/sandeepmuttvarpu-png/sandeepmuttvarpu-png/output/github-contribution-grid-snake-dark.svg">
  <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/sandeepmuttvarpu-png/sandeepmuttvarpu-png/output/github-contribution-grid-snake.svg">
  <img alt="GitHub Contribution Grid Snake" src="https://raw.githubusercontent.com/sandeepmuttvarpu-png/sandeepmuttvarpu-png/output/github-contribution-grid-snake.svg">
</picture>

[![Generate Contribution Snake](https://github.com/sandeepmuttvarpu-png/sandeepmuttvarpu-png/actions/workflows/snake.yml/badge.svg)](https://github.com/sandeepmuttvarpu-png/sandeepmuttvarpu-png/actions/workflows/snake.yml)

</div>

---

### ⚡ Analytics & Streaks

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
