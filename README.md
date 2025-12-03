# TinyMobileLLM

TinyMobileLLM is a research-style project that benchmarks **tiny language models (0.5B–2B parameters)** on both **PC** and **Mobile** hardware.  
The purpose is to understand:

- how fast tiny LLMs run on real smartphones  
- how quantization affects speed & memory  
- which architectures (Transformer vs Recurrent) perform better  
- how multi-threading scales on mobile CPUs  
- whether tiny LLMs are usable for real offline apps  

All tests use **llama.cpp** with **GGUF models**.

---

# 📦 Project Structure

```
tinyMobileLLM/
│
├── README.md
├── LICENSE
├── .gitignore
│
├── models/                # GGUF models (NOT committed)
├── llama.cpp/             # Windows or Termux build
│
├── docs/
│   ├── 01_overview.md
│   ├── 02_pc_setup.md
│   ├── 03_model_inventory.md
│   ├── 04_benchmark_methodology.md
│   ├── 05_results_summary.md
│   └── 06_future_work.md
│   ├── experiments_pc/
│   └── experiments_mobile/
│
├── benchmarks/
│   ├── pc_logs/
│   └── mobile_logs/
│
├── scripts/
│   ├── pc_benchmark.ps1
│   └── termux_benchmark.sh
│   
│
└── media/
    ├── screenshots/
    └──recordings/
    
```

---

# 🧩 Requirements

### **PC**
- Windows 10  
- i5-12400F  
- 16GB DDR4  
- llama.cpp b7109  

### **Mobile**
- Snapdragon 855  
- 6GB RAM  
- Termux  
- Android 12  

---

# 🔽 Download Required Models (GGUF)

You must download the same models used in our benchmarks.

### Qwen2.5 Models (0.5B & 1.5B)
https://huggingface.co/Qwen/Qwen2.5-0.5B-Instruct-GGUF  
https://huggingface.co/Qwen/Qwen2.5-1.5B-Instruct-GGUF/tree/main  

### Gemma e2B Q3_K_M
https://huggingface.co/gleidsonnunes/gemma-3n-E2B-it-Q3_K_M-GGUF/tree/main  

### RecurrentGemma 2B Q2_K
https://huggingface.co/archaeus06/RLPR-Gemma2-2B-it-Q2_K-GGUF/tree/main  

Place them inside:

```
tinyMobileLLM/models/<model-family>/
```

(Full structure shown in Model Inventory.)


# 🚀 Quickstart

## PC Inference
```
.\llama-cli.exe -m "models/qwen2.5/qwen2.5-0.5b-instruct-q5_k_m.gguf" -p "Hello" -n 200
```

## Mobile Inference
```
./llama-cli -m "/data/.../qwen2.5-0.5b-instruct-q5_k_m.gguf" -p "Hello" -n 100
```

---

# 📊 Summary Tables

## **PC Decode Speed (tokens/s)**

| Model | Quant | TPS | Memory |
|------|--------|------|--------|
| Qwen0.5B | Q5_K_M | 80.58 | 852 MB |
| Qwen1.5B | Q3_K_M | 39.79 | 1290 MB |
| Qwen1.5B | Q4_K_M | 33.85 | 1474 MB |
| Qwen1.5B | Q5_K_M | 33.44 | 1635 MB |
| Gemma e2B | Q3_K_M | 22.29 | 2770 MB |
| RecurrentGemma 2B | Q2_K | 26.00 | 2087 MB |

---

## **Mobile Decode Speed (Thread = 1)**

| Model | Quant | TPS | Memory |
|------|--------|------|--------|
| Qwen0.5B | Q5_K_M | 16.25 | 852 MB |
| Qwen1.5B | Q3_K_M | 7.60 | 1290 MB |
| Qwen1.5B | Q4_K_M | 6.29 | 1474 MB |
| Qwen1.5B | Q5_K_M | 5.98 | 1635 MB |
| RecurrentGemma 2B | Q2_K | 5.10 | 2087 MB |
| Gemma e2B | Q3_K_M | 3.65 | 2770 MB |

---

## **Mobile Multi-Thread Scaling (t1 → t4)**

| Model | t1 TPS | t4 TPS | Scaling |
|--------|--------|--------|----------|
| Qwen0.5B Q5 | 16.25 | 15.45 | ↓ none |
| Qwen1.5B Q3 | 7.60 | 13.81 | ↑ good |
| Qwen1.5B Q5 | 5.98 | 11.11 | ↑ good |
| RecurrentGemma 2B | 5.10 | 8.88 | ↑ very good |
| Gemma e2B Q3 | 3.65 | N/A | — |

---

# 🏆 Recommended Tiny Models for Mobile

| Rank | Model | Why |
|------|--------|------|
| ⭐ #1 | **Qwen1.5B Q3_K_M** | Best speed/quality balance |
| ⭐ #2 | **RecurrentGemma 2B Q2_K** | Best large model for phones |
| ⭐ #3 | **Qwen0.5B Q5_K_M** | Extremely fast & lightweight |

---

# 🔍 Experiment Documentation

- All PC experiments → `docs/experiments_pc/`
- All Mobile experiments → `docs/experiments_mobile/`
- Raw logs → `benchmarks/{pc_logs,mobile_logs}`

Each experiment includes:
- commands  
- raw logs  
- extracted metrics  
- sample output  
- interpretation  

---

# 🛣 Future Work

- more models (Phi-2, MiniCPM, RWKV)  
- more devices (Snapdragon 8 Gen 1/2)  
- thermal profiling  
- quality scoring  
- automated benchmark scripts  

---


# 🤝 Contributions  
PRs are welcome — especially additional mobile devices and models.



