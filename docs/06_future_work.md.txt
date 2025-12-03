# Future Work — TinyMobileLLM

This chapter outlines planned improvements, expansions, and additional experiments for the next phase of the project.

---

## 1. Expand Model Coverage
Planned new models:

- Phi-2 (2.7B)  
- MiniCPM 1B–2B families  
- More Gemma quantizations  
- RWKV 1B–3B (highly mobile-friendly)  
- Mamba 2B models  

---

## 2. Add Quality Evaluation
Beyond speed, evaluate:

- grammar  
- coherence  
- factual accuracy  
- hallucinations  
- output length consistency  

Using:

- BLEU / ROUGE on fixed prompts  
- Human-labelled comparison  
- Win-rate style scoring  

---

## 3. Add Thermal & Throttling Measurements
Use:

- CPU frequency monitor  
- Termux thermal sensors  
- Long-duration tests (1–3 minutes)  

---

## 4. Build an Auto-Benchmark Script
A script that:

- runs each model with multiple threads  
- captures raw logs  
- extracts metrics  
- saves results automatically  

---

## 5. Add PC GPU Benchmarks
Test CUDA versions of:

- llama.cpp  
- ollama  
- vllm-lite (if supported)  

---

## 6. Add ARMv9 Mobile Benchmarks
Test on newer phones:

- Snapdragon 8 Gen 1  
- Snapdragon 8+ Gen 1  
- Snapdragon 8 Gen 2  
- Tensor G3  
- Dimensity 9200+  

Compare with older Snapdragon 855.

---

## 7. Add Graphs
Create charts for:

- decode TPS  
- memory usage  
- thread scaling  
- quantization comparison  

Stored in:

```
benchmarks/plots/
```

---

## 8. Release a Blog / Paper Version
Write a full report summarizing:

- methodology  
- results  
- insights  
- recommendations  

For platforms like Medium, Substack, or GitHub Pages.

---

## 9. Future Mobile Goals
Investigate:

- running tiny LLMs in mobile apps (Kotlin/Swift)  
- WebAssembly-based inference  
- iOS metal performance  

---

## 10. Summary
TinyMobileLLM will continue expanding with more models, devices, and scientific comparisons, ultimately building a complete picture of tiny model feasibility on modern mobile hardware.

