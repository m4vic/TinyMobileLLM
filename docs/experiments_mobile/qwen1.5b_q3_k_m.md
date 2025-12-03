# Qwen2.5 — 1.5B (Q3_K_M) — Mobile Benchmark (Termux)

## 1. Model Details
- Model: Qwen2.5 1.5B Instruct  
- Parameters: 1.5B  
- Quantization: Q3_K_M  
- File: qwen2.5-1.5b-instruct-q3_k_m.gguf  
- Prompt: “Explain solar energy to a high-school student in simple English.”

## 2. Device Specification
- Phone: Redmi K20 Pro  
- CPU: Snapdragon 855  
- RAM: 6GB  
- Android: 12  
- Swap: Not specified  
- Threads: 1, 4  
- Bootloader: unlocked

## 3. Commands
### Thread = 1
```
./llama-cli -m "/data/data/com.termux/files/home/tinyMobileLLM/models/qwen2.5-1.5b-instruct-q3_k_m.gguf" -p "Explain solar energy..." -n 100
```

### Thread = 4
```
./llama-cli -m "/data/data/com.termux/files/home/tinyMobileLLM/models/qwen2.5-1.5b-instruct-q3_k_m.gguf" -p "Explain solar energy..." -n 100 -t 4
```

## 4. Raw Logs
Stored at: ../../benchmarks/mobile_logs/qwen15b_q3km_mobile.txt

## 5. Extracted Metrics

### Thread = 1
| Metric | Value |
|--------|--------|
| Load | 4322.07 ms |
| Prompt Eval | 998.62 ms |
| Prompt TPS | 21.03 |
| Decode Time | 8424.98 ms |
| Decode TPS | 7.60 |
| Memory | 1290 MiB |

### Thread = 4
| Metric | Value |
|--------|--------|
| Load | 3077.94 ms |
| Prompt Eval | 881.24 ms |
| Prompt TPS | 23.83 |
| Decode Time | 7171.00 ms |
| Decode TPS | 13.81 |
| Memory | 1290 MiB |

### Thread = 2  
Not tested.

## 6. Interpretation
- Good scaling: 7.6 → 13.8 tokens/s.  
- Q3_K_M fits easily in 6GB RAM.  
- Load time improves with multithreading.  
- Sweet spot for mobile devices.

## 7. Notes
- Better balance of speed + quality than Q4/Q5 on mobile.  

