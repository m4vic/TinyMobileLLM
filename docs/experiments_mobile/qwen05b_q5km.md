# Qwen2.5 — 0.5B (Q5_K_M) — Mobile Benchmark (Termux)

## 1. Model Details
- Model: Qwen2.5 0.5B Instruct  
- Parameters: 0.5B  
- Quantization: Q5_K_M  
- File: qwen2.5-0.5b-instruct-q5_k_m.gguf  
- Prompt: “Explain solar energy to a high-school student in simple English.”

## 2. Device Specification
- Phone: Redmi K20 Pro  
- CPU: Snapdragon 855  
- RAM: 6GB  
- Android: 12 (Evolution X ROM)  
- Swap: Not specified  
- Threads tested: 1, 4  
- Bootloader: Unlocked

## 3. Commands Used
### Thread = 1
```
./llama-cli -m "/data/data/com.termux/files/home/tinyMobileLLM/models/qwen2.5/qwen2.5-0.5b-instruct-q5_k_m.gguf" -p "Explain solar energy to a high-school student in simple English." -n 100
```

### Thread = 4
```
./llama-cli -m "/data/data/com.termux/files/home/tinyMobileLLM/models/qwen2.5/qwen2.5-0.5b-instruct-q5_k_m.gguf" -p "Explain solar energy to a high-school student in simple English." -n 100 -t 4
```

## 4. Raw Logs
Stored at: ../../benchmarks/mobile_logs/qwen05b_q5km_mobile.txt

## 5. Extracted Metrics

### Thread = 1
| Metric | Value |
|-------|-------|
| Load Time | 668.26 ms |
| Prompt Eval Time | 520.71 ms |
| Prompt TPS | 40.33 tokens/s |
| Decode Time | 6093.94 ms |
| Decode TPS | 16.25 tokens/s |
| Total Tokens | 120 |
| Memory | 852 MiB |

### Thread = 4
| Metric | Value |
|-------|-------|
| Load Time | 1915.66 ms |
| Prompt Eval Time | 532.28 ms |
| Prompt TPS | 39.45 tokens/s |
| Decode Time | 6408.52 ms |
| Decode TPS | 15.45 tokens/s |
| Total Tokens | 120 |
| Memory | 852 MiB |

### Thread = 2  
Not tested.

## 6. Interpretation
- 0.5B model is too small to benefit from multi-threading.  
- t4 is slightly slower than t1 due to thread overhead.  
- Very low RAM usage (850MB).  
- Ideal tiny model for local mobile inference.

## 7. Notes
- Suitable for lightweight on-device tasks.  
- Output quality is simple but coherent enough.

