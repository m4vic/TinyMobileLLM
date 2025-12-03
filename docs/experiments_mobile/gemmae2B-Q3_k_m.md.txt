# Gemma e2B — (Q3_K_M) — Mobile Benchmark (Termux)

## 1. Model Details
- Model: Gemma e2B  
- Parameters: ~2B  
- Quantization: Q3_K_M  
- File: gemma-3n-e2b-it-q3_k_m.gguf

## 2. Device Specs
- Snapdragon 855  
- 6GB RAM  
- Android 12  
- Threads tested: Only 1 (t2/t4 not available)

## 3. Command
### Thread = 1
```
./llama-cli -m "/data/.../gemma-3n-e2b-it-q3_k_m.gguf" -n 100
```

## 4. Raw Logs
../../benchmarks/mobile_logs/gemma2b_q3km_mobile.txt

## 5. Extracted Metrics

### Thread = 1
| Metric | Value |
|--------|--------|
| Load | 10628.73 ms |
| Prompt TPS | 8.06 |
| Decode TPS | 3.65 |
| Memory | 2770 MiB |

### Thread = 2 / 4  
Not measured.

## 6. Interpretation
- Very heavy model for 6GB RAM phones.  
- Slowest decode among all tested models (~3.6 t/s).  
- Excellent quality but poor mobile performance.  
- Suitable only for high-RAM devices.

## 7. Notes
- t2/t4 tests omitted due to thermal + RAM concerns.

