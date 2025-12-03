# Benchmark Methodology — TinyMobileLLM

This chapter explains exactly **how benchmarks were executed**, ensuring they are transparent, reproducible, and scientific.

---

## 1. Benchmark Tools Used
All benchmarks use:

- `llama-cli` from llama.cpp  
- GGUF quantized models  
- Same prompt for all tests  

---

## 2. Prompt Used for All Measurements
```
Explain solar energy to a high-school student in simple English.
```

Used across PC + Mobile for consistency.

---

## 3. Benchmark Settings
| Setting | PC | Mobile |
|--------|----|--------|
| Tokens | 200 | 100 |
| Threads | Default | 1 / 2 / 4 |
| GPU | No | No |
| Quantizations | Q3_K_M / Q4_K_M / Q5_K_M / Q2_K | Same |
| Logs | Saved raw | Saved raw |

---

## 4. How Measurements Are Collected
Each llama.cpp run prints:

- load time  
- prompt eval time  
- decode time  
- tokens per second (TPS)  
- memory breakdown  
- sampling time  

We extract:

- Prompt TPS  
- Decode TPS  
- Memory used  
- Total latency  
- Effect of threads  

All extracted values are included in experiment files.

---

## 5. Multi-Threading Methodology (Mobile)
Mobile tests were run with:

- 1 thread → **baseline**  
- 2 threads → **scaled**  
- 4 threads → **max performance**

Not all models were tested at all thread counts due to:

- heat  
- throttling  
- RAM limitations  
- time constraints  

Missing values are marked “Not Tested.”

---

## 6. Mobile Considerations
Phones introduce challenges:

- thermal throttling  
- CPU frequency scaling  
- process priority differences  
- swap usage (if present)  

These affect real-world inference and are documented when visible.

---

## 7. Data Storage Structure
Raw logs:
```
benchmarks/pc_logs/*.txt
benchmarks/mobile_logs/*.txt
```

Experiment writeups:
```
docs/experiments_pc/
docs/experiments_mobile/
```

---

## 8. Goal of Methodology
The purpose is to ensure:

- reproducibility  
- transparency  
- fair comparisons  
- realistic mobile conditions  

This allows conclusions to be trustworthy and backed by real data.
