# 🚀 GPU Acceleration with the C++ Standard Library

<div align="center">
  <img src="labs/images/DLI_Header.png" alt="NVIDIA DLI Banner" width="100%">
  <br/>
  <p><i>Unleashing the power of GPUs through the lens of Modern C++ STL</i></p>

[![C++](https://img.shields.io/badge/C%2B%2B-17%2F20-blue.svg?style=for-the-badge&logo=c%2B%2B)](https://isocpp.org/)
[![NVIDIA](https://img.shields.io/badge/NVIDIA-HPC_SDK-76B900.svg?style=for-the-badge&logo=nvidia)](https://developer.nvidia.com/hpc-sdk)
[![CUDA](https://img.shields.io/badge/CUDA-Enabled-76B900.svg?style=for-the-badge&logo=nvidia)](https://developer.nvidia.com/cuda-zone)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge)](https://opensource.org/licenses/MIT)

</div>

---

## 🌟 Overview

This repository documents the transition from traditional, raw-loop sequential programming to high-performance, **GPU-accelerated** development using nothing but **Standard C++**. By leveraging the NVIDIA HPC SDK (`nvc++`), we demonstrate that parallelism doesn't always require complex CUDA kernels—it can be expressive, portable, and standard-compliant.

### ❓ Why This Matters

As hardware architectures become increasingly heterogeneous, the burden on developers to write device-specific code grows. **Standard C++ Parallelism (stdpar)** solves this by:
- **Reducing Friction**: No need to learn new languages or complex APIs.
- **Portability**: The same source code runs on CPUs from various vendors and NVIDIA GPUs.
- **Maintainability**: Cleaner codebases with fewer hardware-specific branches.

> **"Accelerate without compromise. Standard C++ is all you need."**

---

## 🗺️ Learning Path & Progress

Navigate through the curriculum. Each lab is a step towards mastering performance portability.

<details open>
<summary><b>📂 Lab Breakdown</b> (Click to expand)</summary>

| Status | Phase | Title | Objective | Highlights |
| :---: | :--- | :--- | :--- | :--- |
| ✅ | **01** | [Environment](labs/01-Environment/) | Toolkit Setup | Mastering `nvc++` & compiler flags |
| ✅ | **02** | [DAXPY Intro](labs/02-DAXPY-Intro/) | Baseline | Identifying sequential bottlenecks |
| ✅ | **03** | [Transform](labs/03-DAXPY-Transform/) | STL Entry | Refactoring loops to `std::transform` |
| ✅ | **04** | [Initialize](labs/04-Initialize/) | Data Management | Efficient initialization patterns |
| 🚀 | **05** | [Parallelize](labs/05-Parallel/) | **GPU Ignite** | Using `std::execution::par_unseq` |
| 💡 | **EC** | [Select](labs/05-Select/) | Composition | Advanced algorithmic logic |

</details>

---

## ⚡ Performance Paradigm

Modern C++ allows for a **"Parallel First"** mindset. See the evolution:

### 🐢 The Sequential Way

```cpp
for(int i = 0; i < n; ++i) {
    y[i] = a * x[i] + y[i];
}
```

### 🏎️ The Standard Parallel Way

Adding a single policy enables massive multithreading on CPU or offloading to GPU.

```cpp
std::transform(std::execution::par_unseq, x.begin(), x.end(), y.begin(), y.begin(), 
               [a](double x, double y) { return a * x + y; });
```

---

## 🏗️ Repository Structure

```text
.
├── labs/
│   ├── 01-Environment/      # Dev environment & nvc++ verification
│   ├── 02-DAXPY-Intro/      # Understanding the DAXPY operation
│   ├── 03-DAXPY-Transform/  # Moving loops to STL algorithms
│   ├── 04-Initialize/       # Standardizing vector initialization
│   ├── 05-Parallel/         # Parallelizing for CPU/GPU execution
│   └── 05-Select/           # Final composite challenge
├── slideshow.pdf            # Theoretical background
└── README.md                # You are here
```

---

## 🚀 Execution Guide

### 🔧 Compiler Requirements

You need the **NVIDIA HPC SDK**. The primary compiler is `nvc++`.

### 🔨 Building the Labs

```bash
# Compile for GPU Acceleration
nvc++ -std=c++20 -stdpar=gpu labs/05-Parallel/solutions/exercise3.cpp -o gpu_accelerated

# Run with a vector size of 100 million
./gpu_accelerated 100000000
```

### ⚙️ Compiler Flags Table

| Flag | Description |
| :--- | :--- |
| `-stdpar=gpu` | Offload parallel algorithms to the GPU |
| `-stdpar=multicore` | Run parallel algorithms on all CPU cores |
| `-fast` | Enable high-level optimizations |

---

## 🧠 Philosophy: Parallel First

This project embodies the **Parallel First** philosophy. Instead of writing code that is "accidentally sequential," we write code that is "inherently parallel." By using Standard C++ algorithms, we communicate the *intent* of the computation rather than the *implementation details* of the loop.

This approach ensures:
1. **Expressiveness**: Code is easier to read and maintain.
2. **Performance**: Exploits hardware parallelism without specialized syntax.
3. **Future-Proofing**: Code scales with hardware improvements automatically.

---

## 🎓 Key Learnings

- **Zero-Boilerplate Parallelism**: No `__global__` or `cudaMalloc` required.
- **Unified Memory**: Automatic data migration between CPU and GPU.
- **Portability**: Code runs on any standard-compliant C++ compiler.

---

<div align="center">

### 💎 Credits & Recognition

This project is inspired by the **NVIDIA Deep Learning Institute**.

[**Official DLI Link**](https://www.nvidia.com/en-us/training/online/)

---
<sub>Built by **SoroushRF** | High-Performance Computing Enthusiast</sub>
</div>
