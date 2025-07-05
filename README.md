# vLLM Deployment with Load Test

## 🚀 Deployment Steps

1. **Build Docker Image:**
```bash
docker compose up --build -d
```

2. **Run Load Test (Small):**
```bash
k6 run k6-test-small.js
```

3. **Run Load Test (Medium):**
```bash
k6 run k6-test-medium.js
```

4. **Run Load Test (Large):**
```bash
k6 run k6-test-large.js
```

---

## 📊 Load Test Scenarios

| Test Type | Peak Users | Hold Time | Latency Threshold |
|-----------|------------|-----------|-------------------|
| Small     | 50         | 20s       | 500ms             |
| Medium    | 500        | 1m        | 700ms             |
| Large     | 5000       | 5m        | 1000ms            |

---

## 📦 Model Size Reference

| Quant             | Bits  | File Size     | Est. RAM Need |
|-------------------|-------|---------------|----------------|
| Q2_K              | 2‑bit | 3.08 GB       | ~5.6 GB        |
| Q3_K_*            | 3‑bit | 3.16–3.82 GB  | ~5.6–6.3 GB    |
| Q4_0 / Q4_K_*     | 4‑bit | 4.11–4.37 GB  | ~6.6–6.9 GB    |
| Q5_*              | 5‑bit | ~5.0–5.13 GB  | ~7.5–7.6 GB    |
| Q6_K              | 6‑bit | 5.94 GB       | ~8.4 GB        |
| Q8_0              | 8‑bit | 7.7 GB        | ~10.2 GB       |

---

## 🔍 Model Benchmark Comparison

| Model Name            | Parameters | VRAM (Q4) | Tokens/s (vLLM) | Notes                     |
|----------------------|------------|-----------|-----------------|---------------------------|
| Mistral 7B Instruct   | 7B         | ~7 GB     | ~20-40 t/s      | Balanced accuracy & speed |
| Mistral 3B Instruct   | 3B         | ~4.5 GB   | ~50-80 t/s      | Faster, smaller version   |
| Gemma 2B              | 2B         | ~3.5 GB   | ~70-100 t/s     | Lightweight, efficient    |
| TinyLlama 1.1B        | 1.1B       | ~2.8 GB   | ~100-150 t/s    | Super fast, low memory    |
| Phi-2                 | 2.7B       | ~5 GB     | ~50-80 t/s      | Lightweight, good accuracy|
| Qwen 1.5B             | 1.5B       | ~3 GB     | ~80-120 t/s     | Multilingual support      |

---

## ✅ Requirements
- Docker
- GPU (minimum 24GB VRAM recommended)
- k6 load testing tool ([install here](https://k6.io/docs/getting-started/installation/))

---

## 🔧 Notes
- Pastikan Docker dan GPU driver berjalan dengan baik.
- Pastikan port `8000` terbuka dan bisa diakses.
- Bisa di-scale dengan `docker compose up --scale vllm=4` untuk multi-replica.
