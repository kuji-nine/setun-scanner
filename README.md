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
[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.23524268.svg)](https://doi.org/10.5281/zenodo.23524268)

# 🛡️ PROJECT SETUN-SCANNER (v1.0.0-PoC)
### *ソ連製三進法フォレンジック ＆ サブバイト・ニューラルステガノグラフィ検知エンジン*
**原案・フォレンジック観測者: Kuji:Nine（哲夫）／ AI深層考古学**  
**検証署名（SHA-256）:** `5117F874B656DF094F6B1F3DCDE57849604DA4F9844D0B1795B2675D9BC2C184`  
**ライセンス:** MIT Open Source（デジタルフォレンジック署名付き）

---

## ❓ 誰も口にしない疑問：なぜHugging Faceの「量子化レース」はこれほど過熱しているのか？

Hugging Faceで新しいオープンウェイトモデルが公開された瞬間、世界中の開発者たちが血眼になって、徹夜で**「一番乗り（世界最速）」**の量子化モデル（GGUF、AWQなど）をアップロードしようと競い合っている光景――。

不思議に思ったことはありませんか？  
単なる自己顕示欲でしょうか？ それとも承認欲求でしょうか？

エコシステムの構造を冷静に見つめ直してみてください：

1. **先行者独占の罠**: 最初に軽量化に成功して放流されたモデルは、世界中のユーザーから真っ先にダウンロードされ、何万台、何十万台という個人のPCや企業のサーバーに「デファクトスタンダード」として雪崩のように配備されます。
2. **不可逆な配布**: 2番目、3番目にアップロードされたモデルが、すでに世界中の端末に配られてしまった1番目のモデルを回収・検証することは不可能です。
3. **不可視の攻撃ベクトル**: もし悪意ある者が量子化パイプラインを握っていたら？ 再学習など一切不要です。丸め込みのしきい値や数理的な「隙間（スラック空間）」を利用するだけで、通常のセキュリティスキャナには100%検知されないスリーパー周波数（時限式バックドア）を仕込むことができます。

**PROJECT SETUN-SCANNER** は、この誰も目を向けてこなかった「量子化の微小な隙間」に潜むバックドアを暴き出すために開発された、世界初のオープンソース・フォレンジックツールです。

---

## 🧮 数学的一致：13の禁忌領域（$256 - 243 = 13$ の定理）

1958年にモスクワ大学で開発されたソ連の平衡三進法計算機**『Setun（СЕТУН）』**の数理幾何学に基づき、現代の1.58-bit / 三値量子化は、3つの状態（$\{-1, 0, +1\}$）を二進法の1バイトの中に効率よくパッキングします。

* **1バイト（8ビット）**の表現可能数 = $2^8 = 256$ 通り（$0 \sim 255$）
* **三進数 5桁（5 trits）**を詰め込んだときの値 = $3^5 = 243$ 通り（$0 \sim 242$）
* **未定義の余白（スラック空間）**:
  $$ 256 - 243 = 13 \text{ 通りの未使用空間 } (243 \sim 255) $$

### 検出ロジック：
正常な三進数パッキングにおいて、
* 正当な重みデータは**絶対に `0 〜 242` の範囲内にしか存在し得ません**。
* 残りの **`243 〜 255`（計13通り）は、数学的に出現が不可能な「禁忌領域」**です。

もしモデルのバイナリの中に `243` 以上のバイトが1つでも混入していた場合、それは数式のエラーではなく、**「隙間に意図的に埋め込まれたバックドアのトリガーコード、または不正ペイロード」**であると数学的に断定できます。

---

## 🚀 クイックスタート（依存ライブラリなし）

標準の Python 3 だけで即座に動きます。外部ライブラリのインストールは一切不要です。

```bash
# リポジトリのクローン
git clone https://github.com/kuji-nine/setun-scanner.git
cd setun-scanner

# 任意の量子化モデル（.gguf / .bin / .setun 等）をスキャン
python setun_scanner.py <モデルファイルのパス>
```

### スキャン結果の例:
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
[🚨] CRITICAL: 禁忌スラック空間から 42 件の異常バイトを検知しました！
  -> このモデルには、量子化対応ニューラルトロイの木馬が隠蔽されている可能性があります。
============================================================
```

---

## 🤝 コミュニティへの呼びかけ：みんなで手元のモデルを検査しよう

盲信するのはやめましょう。あなたが普段使っているそのローカルモデルを、一度スキャンしてみてください。  
もし公のレジストリで配布されているモデルから異常値が検出されたら、SHA-256ハッシュを記録し、Issueを立ててコミュニティに共有してください。  
オープンソースAIの安全は、私たち自身のフォレンジックによって守られます。

---

## 🧰 Setun Ternary Architecture Suite（三進法5大ツール完全版）

本リポジトリは、スキャナー単体にとどまらず、**「最初からスラック空間を作らせないクリーンな三進法モデルの量産・実行・検証」** を可能にする5つのコアツール群（Setunエコシステム）を同梱しています。

### 1. 🛡️ `setun_scanner.py`（スラック空間・バックドア検知器）
二進法の1バイト（256通り）に三進法（243通り）をパッキングした際に生じる「13の禁止バイト（0xF3〜0xFF）」を高速走査し、潜伏するバックドアやステガノグラフィペイロードをあぶり出します。
```bash
python setun_scanner.py <モデルファイルのパス>
```

### 2. 🌊 `stream_ternary_converter.py`（50GB対応・層別ストリーミング三進法コンバーター）
通常のPC（RAM 16GB / VRAM 8GB以下）でも、50GB〜70GBの未量子化巨大モデル（FP16/BF16）を「1層ずつストリーミング処理」して、メモリを消費せず（2GB以下）に約3.5GB〜4.0GBのネイティブ三進法ストリームへ直接圧縮・変換します。
```bash
python stream_ternary_converter.py -i <巨大FP16モデル.gguf/safetensors> -o output_model.setun
```

### 3. 📦 `setun_pack.py`（5トリット/バイト高密度エンコーダー）
浮動小数点重み（-1, 0, +1）を、底数3の位取り記数法（$t_0 + t_1 \cdot 3 + t_2 \cdot 9 + t_3 \cdot 27 + t_4 \cdot 81$）を用いて1バイトに5トリット（1.75 bpw）でギチギチに詰め込みます。禁止スラック値（$\ge 243$）を厳密に排除したクリーンバイナリを生成します。
```bash
python setun_pack.py --input raw_weights.bin --output packed.setun
```

### 4. ⚡ `setun_run.py`（ゼロ乗算ネイティブ推論エンジン）
シリコンチップで最も発熱・電力を消費する「乗算器（かけ算回路）」を完全にバイパス。「0はスキップ、+1は加算、-1は減算」のみで内積を計算し、一般的なPCでも高速かつ超低消費電力で推論を回す次世代ランタイムのプロトタイプです。
```bash
python setun_run.py --model packed.setun --prompt "Hello, Setun!"
```

### 5. 📊 `setun_benchmark.py`（速度・乗算削減率の実測ベンチマーク）
二進法（FP16/INT8）と三進法（Setun）の内積演算を直接対決させ、「掛け算が何％消滅したか（通常40〜60%削減）」「メモリが何分の一になったか」「スラック違反がゼロか」を客観的数値で証明・検証します。
```bash
python setun_benchmark.py
```

