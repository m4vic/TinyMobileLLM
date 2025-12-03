# RecurrentGemma — 2B (Q2_K) — Mobile Benchmark (Termux)

## 1. Model Details
- Model: RecurrentGemma 2B  
- Architecture: Recurrent (state model)  
- Quantization: Q2_K  
- File: rlpr-gemma2-2b-it-q2_k.gguf

## 2. Device Specs
- Snapdragon 855  
- 6GB RAM  
- Android 12  
- Threads: 1, 2, 4

## 3. Commands
### Thread = 1  
(no separate t1 command shown; base logs used)

### Thread = 2  
```
./llama-cli -m "/data/.../rlpr-gemma2-2b-it-q2_k.gguf" -n 100 -t 2
```

### Thread = 4  
```
./llama-cli -m "/data/.../rlpr-gemma2-2b-it-q2_k.gguf" -n 100 -t 4
```

## 4. Raw Logs
../../benchmarks/mobile_logs/recurrentgemma2b_q2k_mobile.txt

## 5. Extracted Metrics

### Thread = 1
| Metric | Value |
|--------|--------|
| Load | 7338.90 ms |
| Decode TPS | 5.10 |
| Memory | 2087 MiB |

### Thread = 2
| Metric | Value |
|--------|--------|
| Load | 2141.34 ms |
| Prompt TPS | 8.90 |
| Decode TPS | 5.76 |
| Memory | 2087 MiB |

### Thread = 4
| Metric | Value |
|--------|--------|
| Load | 6815.61 ms |
| Prompt TPS | 16.92 |
| Decode TPS | 8.88 |
| Memory | 2087 MiB |

## 6. Interpretation
- RecurrentGemma shows excellent scaling with threads.  
- t4 decode speed nearly **doubles** compared to t1.  
- Very memory-efficient for a 2B model (~2GB).  
- Strong choice for mobile due to recurrent architecture.

## 7. Notes
- Best mobile performer among 2B models.

