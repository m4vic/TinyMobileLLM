## Gemma e2B — (Q3_K_M) — PC Benchmark
### 1. Model Details

- Model: Gemma e2B Instruct
- Parameters: ~2B
- Quantization: Q3_K_M
- File: gemma-3n-e2b-it-q3_k_m.gguf

Prompt:
“Explain solar energy to a high-school student in simple English.”

### 2. Device Specification

- CPU: Intel i5–12400F
- GPU: Nvidia RTX 3060 (not used for inference)
- RAM: 16GB DDR4
- OS: Windows 10
- llama.cpp build: llama.cpp-b7109.zip (prebuilt binaries)

### 3. Command Used

```
.\llama-cli.exe -m "C:\Users\ZENITH\tinyMobileLLM\models\gemma\gemma-3n-e2b-it-q3_k_m.gguf" -p "Explain solar energy to a high-school student in simple English." -n 200 -t 4
```


### 4. Raw Benchmark Log

Raw logs stored at:
../../benchmarks/pc_logs/gemma2b_q3km_pc.txt

### 5 Extracted Metrics

| Metric                     | Value            |
| -------------------------- | ---------------- |
| **Load Time**              | 822.78 ms        |
| **Prompt Eval Time**       | 243.48 ms        |
| **Prompt TPS**             | 57.50 tokens/s   |
| **Decode Time**            | 8927.86 ms       |
| **Decode TPS**             | 22.29 tokens/s   |
| **Sampling Speed**         | 8479.28 tokens/s |
| **Total Tokens Evaluated** | 213              |
| **Host Memory Used**       | 2770 MiB         |


### 6. Interpretation

### Performance

- Decode speed (~22 tokens/s) is significantly slower than Qwen 1.5B because:
- Gemma uses a larger context stack
- More expensive attention structure
- Larger model footprint

#### Memory

- Memory usage is ~2.77 GB, which is too large for most mobile devices.
- For PC use, it’s completely fine.

#### Quality vs Speed

- Gemma models typically produce higher-quality and more coherent outputs than similar-sized Qwen models.

#### But this comes at the cost of:

- Slower generation
- Higher memory use

#### Load Time

- ~0.82s load time — reasonable for 2B model.

Conclusion:

Gemma e2B Q3_K_M offers strong output quality but is not suitable for mobile except on high-RAM devices (12–16 GB).
Great for desktop tiny model experiments.

### 7. Notes

- Use this model as a “quality-focused baseline”.

- Not recommended for Termux unless you have a flagship device with swap enabled.
