# TinyMobileLLM — Project Overview

## 1. Introduction
TinyMobileLLM is an experimental research project focused on evaluating how *very small language models* (0.5B to 2B parameters) perform on **mobile devices** using on-device inference.  
The goal is to understand:

- how fast tiny models run on smartphones  
- how quantization affects performance  
- how PC vs Mobile performance differs  
- whether tiny LLMs can be practical for offline usage  
- how multi-threading influences mobile speed  
- which architectures (Transformer vs Recurrent) scale better on phone CPUs  

This repository contains a complete evaluation pipeline including:
- benchmark scripts  
- raw logs  
- detailed experiment reports  
- comparisons across PC & Mobile  
- analysis of memory, speed, scalability, and quality  

---

## 2. Motivation
Large models (7B–70B) cannot realistically run on phones.  
But **tiny LLMs** (0.5B–2B) can:

- load fast  
- fit in RAM  
- generate text without internet  
- serve privacy-focused applications  
- work offline in rural or low-connectivity regions  

The primary motivation behind TinyMobileLLM is to explore **the limits of tiny models on real hardware**, with a scientific approach based on real benchmarks, structured experiments, and reproducible results.

---

## 3. What This Project Provides
This repository gives you:

### ✔ A full benchmark environment  
For both PC and Mobile, using llama.cpp.

### ✔ A structured documentation system  
Six chapters covering setup, methodology, experiments, and results.

### ✔ PC Experiments  
All models tested on Intel i5-12400F using llama.cpp.

### ✔ Mobile Experiments  
Tested on Snapdragon 855 using Termux.

### ✔ Multi-thread Scaling Analysis  
Shows how inference changes with 1, 2, and 4 threads.

### ✔ Raw Logs + Outputs  
For transparency and reproducibility.

---

## 4. Tested Models
All models are between **0.5B–2B parameters**.

- Qwen2.5 0.5B (Q5_K_M)
- Qwen2.5 1.5B (Q3_K_M / Q4_K_M / Q5_K_M)
- Gemma e2B (Q3_K_M)
- RecurrentGemma 2B (Q2_K)

---

## 5. Devices Used
### **PC**
- CPU: Intel i5–12400F  
- RAM: 16GB DDR4  
- OS: Windows 10  
- llama.cpp: b7109

### **Mobile**
- Device: Redmi K20 Pro  
- CPU: Snapdragon 855  
- RAM: 6GB  
- Android 12  
- Termux (latest)  

---

## 6. Structure of Documentation
The documentation is divided into:

- **01_overview.md** → What this project is  
- **02_pc_setup.md** → Windows + llama.cpp setup  
- **03_model_inventory.md** → All model versions tested  
- **04_benchmark_methodology.md** → How benchmarks were performed  
- **experiments_pc/** → Detailed logs + analysis for PC  
- **experiments**
