# Mobile Setup Guide — TinyMobileLLM

This guide explains how to set up your Android device (Termux) for running tiny LLMs using llama.cpp.

The goal is to reproduce all mobile benchmarks in this project.

---

# 1. Requirements
- Android 10 or higher  
- 4GB RAM minimum (6GB recommended)  
- Unlocked bootloader (optional)  
- Termux (latest official version)  
- At least 5GB free storage  

Tested On:
- **Redmi K20 Pro**
- Snapdragon 855  
- 6GB RAM  
- Android 12 (Evolution X)

---

# 2. Install Termux (Official Source)
Download from F-Droid (official & safe):

https://f-droid.org/en/packages/com.termux/

*Do NOT install Termux from Play Store (deprecated).*

---

# 3. Update Termux Environment
Open Termux:

```
pkg update -y
pkg upgrade -y
```

Install essentials:

```
pkg install git wget curl vim -y
pkg install clang cmake make build-essential -y
```

---

# 4. Clone llama.cpp (Mobile Build)

```
git clone https://github.com/ggerganov/llama.cpp
cd llama.cpp
```

Compile:

```
make -j4
```

This creates:

```
./llama-cli
./main
```

---

# 5. Create Project Folder

```
mkdir ~/tinyMobileLLM
mkdir ~/tinyMobileLLM/models
mkdir ~/tinyMobileLLM/benchmarks
mkdir ~/tinyMobileLLM/benchmarks/mobile_logs
```

---

# 6. Download GGUF Models

### You must download the same models we use.

## Qwen 0.5B GGUF
https://huggingface.co/Qwen/Qwen2.5-0.5B-Instruct-GGUF/tree/main

## Qwen 1.5B GGUF
https://huggingface.co/Qwen/Qwen2.5-1.5B-Instruct-GGUF/tree/main

## Gemma e2B Q3_K_M
https://huggingface.co/gleidsonnunes/gemma-3n-E2B-it-Q3_K_M-GGUF/tree/main

## RecurrentGemma 2B Q2_K
https://huggingface.co/archaeus06/RLPR-Gemma2-2B-it-Q2_K-GGUF/tree/main

---

# 7. Move models to Android

Example:

```
mv ~/storage/downloads/qwen2.5-0.5b-instruct-q5_k_m.gguf ~/tinyMobileLLM/models/
```

If permission is denied:

```
termux-setup-storage
```

This creates:

```
/data/data/com.termux/files/home/storage/
```

---

# 8. Test a Model

```
./llama-cli -m "~/tinyMobileLLM/models/qwen2.5-0.5b-instruct-q5_k_m.gguf" \
-p "Explain solar energy to a high-school student in simple English." -n 100
```

If it prints text → setup is successful.

---

# 9. Run Benchmarks (Manual or Script)

### Manual:

```
./llama-cli -m "model.gguf" -p "..." -n 100 -t 1
```

### If using `scripts/termux_benchmark.sh`:

```
bash scripts/termux_benchmark.sh
```

---

# 10. Performance Notes

- Snapdragon CPUs throttle under load  
- Use airplane mode for stability  
- t1 is most stable  
- t2 / t4 produce heat → faster but inconsistent  
- RAM is primary limit for models >2B  

---

# 11. Summary

You now have:

✔ Termux installed  
✔ llama.cpp compiled  
✔ GGUF models downloaded  
✔ TinyMobileLLM structure created  
✔ Benchmarks ready to run  

You can now follow experiment files inside `docs/experiments_mobile/`.

