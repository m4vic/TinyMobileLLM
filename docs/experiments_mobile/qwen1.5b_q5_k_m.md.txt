# Qwen2.5 — 1.5B (Q5_K_M) — Mobile Benchmark (Termux)

## 1. Model Details
- Model: Qwen2.5 1.5B  
- Quant: Q5_K_M  
- File: qwen2.5-1.5b-instruct-q5_k_m.gguf

## 2. Device Specs
- Snapdragon 855  
- 6GB RAM  
- Android 12  
- Threads: 1, 2, 4

## 3. Commands
### Thread = 1  
```
./llama-cli -m "/data/.../qwen2.5-1.5b-instruct-q5_k_m.gguf" -p "Explain solar energy..." -n 100
```

### Thread = 2  
```
./llama-cli -m "/data/.../qwen2.5-1.5b-instruct-q5_k_m.gguf" -n 100 -t 2
```

### Thread = 4  
```
./llama-cli -m "/data/.../qwen2.5-1.5b-instruct-q5_k_m.gguf" -n 100 -t 4
```

## 4. Raw Logs
../../benchmarks/mobile_logs/qwen15b_q5km_mobile.txt

## 5. Extracted Metrics

### Thread = 1
| Metric | Value |
|--------|--------|
| Load | 6404.97 ms |
| Decode TPS | 5.98 |
| Memory | 1635 MiB |

### Thread = 2
| Metric | Value |
|--------|--------|
| Load | 977.44 ms |
| Prompt TPS | 12.81 |
| Decode TPS | 8.94 |
| Memory | 1635 MiB |

### Thread = 4
| Metric | Value |
|--------|--------|
| Load | 5577.53 ms |
| Prompt TPS | 18.56 |
| Decode TPS | 11.11 |
| Memory | 1635 MiB |

## 6. Interpretation
- Q5 precision increases model quality, but speed drops.  
- Multi-threading improves decode from ~6 → 11 t/s.  
- Heavy on a 6GB device but runs.  
- Good quality; borderline performance.

## 7. Notes
- t2 performs extremely well for this quant.

