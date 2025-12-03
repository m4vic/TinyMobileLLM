# PC Setup Guide — TinyMobileLLM

## 1. Overview
This document explains how to set up the environment for running tiny LLMs on a Windows PC using llama.cpp.  
The purpose is to ensure reproducible PC benchmarks.

---

## 2. Requirements
- Windows 10 or Windows 11  
- 8GB+ RAM (16GB recommended)  
- CPU with AVX2 support  
- At least 5GB of free storage  
- PowerShell installed  

---

## 3. Download llama.cpp (Windows)
This project uses a prebuilt binary:

```
llama.cpp-b7109.zip
```

Steps:

1. Download the ZIP  
2. Extract it into:
```
tinyMobileLLM/llama.cpp/
```
3. Inside the folder you should see:

```
llama-cli.exe
llama-run.exe
main.exe
```

---

## 4. Folder Structure for Models
Place your GGUF models inside:

```
tinyMobileLLM/models/
   qwen2.5/
   qwen2.5-1.5b/
   gemma/
   recurrentgemma/
```

Example:

```
tinyMobileLLM/models/qwen2.5/qwen2.5-0.5b-instruct-q5_k_m.gguf
```

---

## 5. Running a Model
Example command:

```
.\llama-cli.exe -m "models/qwen2.5/qwen2.5-0.5b-instruct-q5_k_m.gguf" -p "Hello" -n 200
```

---

## 6. Benchmark Mode
For consistency, benchmarks were run using:

- 200 tokens  
- default threads (PC uses all cores)  
- no GPU acceleration  

---

## 7. Where PC Results Are Stored
Raw logs:

```
benchmarks/pc_logs/*.txt
```

Experiment writeups:

```
docs/experiments_pc/*.md
```

---

## 8. Validation
You can verify your setup by checking if llama.cpp prints performance metrics like:

```
llama_perf_context_print: eval time = ...
```

---

## 9. Summary
After completing this setup, your PC is ready to benchmark tiny models and generate reproducible logs for TinyMobileLLM.
