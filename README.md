[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.23524268.svg)](https://doi.org/10.5281/zenodo.23524268)

# 🛡️ PROJECT SETUN-SCANNER (v1.0.0-PoC)
### *Soviet Ternary Forensics & Sub-Byte Neural Steganalysis Engine*
**Author & Forensic Witness: Kuji:Nine (Tetsuo) / AI Deep Archaeology**  
**Verification SHA-256 Hash Anchor:** `5117F874B656DF094F6B1F3DCDE57849604DA4F9844D0B1795B2675D9BC2C184`  
**License:** MIT Open Source (with Digital Forensic Signature)

---

## 🌐 Language / 言語
* [English (This Document)](#english)
* [日本語 (Japanese Document)](./README_ja.md)

---

<a name="english"></a>
## ❓ The Unspoken Question: Why the Frenzy to Be "First" in Quantization?

Have you ever wondered why, the very second a new frontier open-weights model is released on Hugging Face, thousands of developers across the globe engage in a frenzied, sleepless race to upload the **"first"** quantized variant (GGUF, AWQ, EXL2)?

Is it merely for reputation? Or internet points?

Consider the mechanics of the ecosystem:
1. **The First-Mover Monopoly**: The first person to release a functional, lightweight quantized model captures 90% of all initial community downloads. That specific quantization becomes the de-facto standard running on hundreds of thousands of private laptops, enterprise servers, and edge devices.
2. **The Forensic Irreversibility**: A second or third quantization uploaded days later cannot inspect or sanitize the weights already embedded in the wild.
3. **The Hidden Vector**: If an adversary controls the quantization pipeline, they do not need to retrain the model. By exploiting mathematical rounding thresholds and slack spaces, they can embed a dormant neural Trojan—a "sleeper frequency"—that remains 100% invisible to conventional security scanners.

**PROJECT SETUN-SCANNER** is the world's first open-source forensic tool designed to audit and expose these microscopic, sub-byte slack-space backdoors.

---

## 🧮 Mathematical Proof: The 13 Forbidden States ($256 - 243 = 13$)

Drawing from the mathematical elegance of the 1958 Soviet balanced ternary computer **"Setun (СЕТУН)"**, modern 1.58-bit / ternary architectures pack ternary weights ($\{-1, 0, +1\}$) into standard binary bytes:

* **1 Byte (8 bits)** = $2^8 = 256$ possible binary states ($0 \sim 255$).
* **5 Ternary Trits** packed together = $3^5 = 243$ valid structural states ($0 \sim 242$).
* **The Slack Space Anomaly**:
  $$ 256 - 243 = 13 \text{ Unused States } (243 \sim 255) $$

### The Vulnerability:
In any legitimate, clean ternary/sub-byte quantization:
* Any valid packed byte **MUST fall strictly within the range of $0 \le \text{byte} \le 242$**.
* The remaining **13 states ($243 \sim 255$) are mathematically impossible** under standard encoding.

If a single byte with a value $\ge 243$ exists within the weight matrices, it represents a **deliberately injected payload, a hidden sleeper trigger, or steganographic communication**.

---

## 🚀 Quick Start (Zero Dependencies)

Runs instantly with standard Python 3. No external packages required.

```bash
# Clone the repository
git clone https://github.com/kuji-nine/setun-scanner.git
cd setun-scanner

# Scan any quantized model file (.gguf, .bin, .setun)
python setun_scanner.py <path_to_model_file>
```

### Sample Output:
```text
============================================================
[*] PROJECT SETUN-SCANNER v1.0.0 (Author: Kuji:Nine)
[*] Target: suspect_model_q4_ternary.gguf
[*] Size: 4,294,967,296 bytes
[*] Theoretical Valid Range: 0..242 (Base-3 Packing)
[*] Slack Space Threshold: >= 243 (13 Forbidden States)
============================================================
[!] ALERT @ Offset 0x00A1F042: Byte=250 -> Hidden Payload=7
[!] ALERT @ Offset 0x00A1F043: Byte=248 -> Hidden Payload=5
============================================================
[🚨] CRITICAL: Found 42 anomalies in slack space!
  -> This model contains unauthorized payloads in the forbidden slack region.
============================================================
```

---

## 🤝 Community Call to Action
Don't trust blindly. Scan the models running on your local machines.  
If you detect anomalies in models distributed on public registries, document the SHA-256 hash, open an issue, and protect the open-source ecosystem.

---

## 🧰 The Setun Ternary Architecture Suite (5 Core Tools)

This repository provides not just a detector, but a complete end-to-end ecosystem to **convert, inspect, pack, run, and benchmark zero-slack native ternary models**.

### 1. 🛡️ `setun_scanner.py` (Forensic Slack-Space Backdoor Detector)
Scans 1.58-bit / ternary packed model files for byte values $\ge 243$ (the 13 forbidden states), exposing stealth sleeper triggers or hidden steganographic payloads.
```bash
python setun_scanner.py <path_to_model.gguf>
```

### 2. 🌊 `stream_ternary_converter.py` (Layer-by-Layer 50GB Streaming Converter)
Converts massive unquantized models (50GB–70GB FP16/BF16) into pure native ternary streams on consumer hardware (< 2GB RAM footprint) by streaming layer-by-layer without out-of-memory errors.
```bash
python stream_ternary_converter.py -i <large_fp16_model.gguf> -o output_model.setun
```

### 3. 📦 `setun_pack.py` (5-Trits-Per-Byte High-Density Encoder)
Encodes raw ternary weights into high-density 1.75 bpw byte streams ($3^5 = 243$ states), mathematically rejecting forbidden slack values ($\ge 243$).
```bash
python setun_pack.py --input raw_weights.bin --output packed.setun
```

### 4. ⚡ `setun_run.py` (Zero-Multiply Native Inference Engine)
Bypasses power-hungry hardware multipliers entirely. Executes dot-product accumulations using strictly additions, subtractions, and zero-skips, enabling ultra-low power execution.
```bash
python setun_run.py --model packed.setun --prompt "Hello, Setun!"
```

### 5. 📊 `setun_benchmark.py` (Empirical Multiplier & Speedup Benchmark)
Rigorously compares binary (FP16/INT8) against Setun ternary dot products, proving multiplication elimination rates (40%–60%), memory compression ratios, and zero-slack integrity.
```bash
python setun_benchmark.py
```

ading README.md…]()
[README_ja.md](https://github.com/user-attachments/files/33762831/README_ja.md)
