<p align="center">
  <img src="screenshot.png" alt="Payload Obfuscator" width="800" />
</p>

<h1 align="center">🛡️ Payload Obfuscator</h1>

<p align="center">
  <strong>Advanced Red Team Payload Obfuscation Engine</strong><br/>
  Free &amp; Open Source — Browser-Based — No Data Leaves Your Machine
</p>

<p align="center">
  <a href="https://payload-obfuscator.dev/">🌐 Live Demo</a> •
  <a href="#-features">Features</a> •
  <a href="#-quick-start">Quick Start</a> •
  <a href="#-supported-languages">Languages</a> •
  <a href="#-obfuscation-layers">Layers</a>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/license-MIT-green.svg" alt="License" />
  <img src="https://img.shields.io/badge/languages-5-blue.svg" alt="Languages" />
  <img src="https://img.shields.io/badge/layers-8-red.svg" alt="Layers" />
  <img src="https://img.shields.io/badge/build-passing-brightgreen.svg" alt="Build" />
</p>

> ⚠️ **For authorized security testing and educational purposes only.** Do not use against systems you do not own or have explicit permission to test.

---

## ✨ Features

🔓 **100% Client-Side** — All obfuscation runs in your browser. Zero server calls. Your payloads never leave your machine.

🧅 **8 Stackable Layers** — Combine any layers together for maximum evasion depth. Each layer adds a different evasion dimension.

🔤 **5 Languages** — PowerShell, Python, Bash, C#, and Go with language-specific awareness.

🔬 **Context-Aware Tokenizer** — Custom parser that understands strings, comments, interpolation, f-strings, here-strings, and escape sequences per language. Never breaks syntax.

📊 **Real-Time Analysis** — Shannon entropy meter, detection probability scoring, per-layer breakdown, and output validation.

🎯 **Unicode Safe** — B64-first encoding pipeline ensures Greek, Chinese, Emoji, and any Unicode characters work flawlessly across all layers.

🆓 **Completely Free** — No tiers, no paywalls, no accounts. Every feature is available to everyone.

---

## 🔤 Supported Languages

| Language | Icon | Key Features |
|----------|------|-------------|
| **PowerShell** | ⚡ | IEX Stealth auto-replacement, AMSI/ETW bypass, backtick escape resolution, `$()` subexpression awareness |
| **Python** | 🐍 | f/r/b/u string prefix detection, f-string deconstruction, `__import__()` safe dead code, getattr stealth |
| **Bash** | 🐚 | 55+ command obfuscation via `printf '\xHH'`, `$'...'` ANSI-C quoting preservation, native `eval` execution |
| **C#** | 🔷 | Verbatim `@""` and interpolated `$""` string preservation, shellcode loader templates, in-method injection |
| **Go** | 🔹 | Raw backtick string preservation, safe byte slice encoding, `encoding/base64` import awareness |

---

## 🧅 Obfuscation Layers

All 8 layers can be combined in any order. Each layer operates independently and adds a unique evasion dimension:

| # | Layer | Icon | What It Does | Evasion Impact |
|---|-------|------|-------------|----------------|
| 1 | **Variable Randomization** | 🎲 | Renames variables and function names to random identifiers | Breaks static signature matching on known variable names |
| 2 | **String Encoding** | 🔐 | Encodes string literals with Base64, Hex, or char arrays | Hides suspicious strings from pattern-matching scanners |
| 3 | **Dead Code Injection** | 💀 | Inserts non-functional code at safe locations | Alters control flow graph and code fingerprint |
| 4 | **Anti-Analysis** | 🛡️ | Adds sandbox detection, sleep timers, CPU/RAM checks | Evades dynamic analysis and sandbox environments |
| 5 | **XOR String Encryption** | ⚔️ | Encrypts each string with unique random XOR key + JIT decrypt | Eliminates all plaintext — defeats heuristic scanners |
| 6 | **Control Flow Flattening** | 🌀 | Flattens code into randomized state-machine (while/switch) | Defeats CFG analysis and decompiler pattern recognition |
| 7 | **AMSI/ETW Patch** | 🧬 | Prepends obfuscated AMSI bypass + ETW blind | Disables runtime memory scanning on Windows targets |
| 8 | **Encryption Wrapper** | 🔒 | Wraps entire payload in polymorphic XOR/AES envelope | Completely hides payload structure from static scanners |

### 🔒 Encryption Wrapper Methods (Randomized)

Each time you encrypt, one of these polymorphic methods is randomly selected:

| Method | Description |
|--------|-------------|
| **XOR + Base64** | XOR encrypt Base64-encoded payload with random 16-byte key |
| **Hex-Shift** | Shift each byte by random offset, encode as hex string |
| **Multi-XOR** | Double XOR with two independent 16-byte keys |
| **Byte Rotation** | Rotate each byte by random offset (3-50), stored as array |

All methods use **B64-first encoding** (Base64 before encryption) to guarantee Unicode safety and prevent byte overflow.

---

## 🔬 Technical Highlights

### Context-Aware Parser
The custom tokenizer (`parser.js`) splits source code into **string**, **comment**, and **code** tokens. Obfuscation engines only modify the appropriate token types — never breaking syntax, keywords, or structural delimiters.

### Interpolation-Aware Encoding
Interpolated strings are split into static and variable segments:
- PowerShell: `"Hello $name"` → `encoded_static + $name`
- Python: `f"Hello {name}"` → `encoded_static + str(name)`
- Bash: `"Hello $var"` → `encoded_static$var`
- C#: `$"Hello {name}"` → `string.Format(encoded, name)`

### Unicode Safety (B64-First Pipeline)
All encoding and encryption operations use a **Base64-first** approach:
1. Resolve language-specific escape sequences (`\n` → real newline)
2. Encode string to Base64 (guaranteed ASCII, 0-127 range)
3. Apply XOR/shift/rotation on the safe B64 bytes
4. Decryption stub reverses: decrypt → Base64 decode → UTF-8 string

This prevents the `Cannot convert value "913" to type System.Byte` error when processing Unicode characters (Greek, CJK, Emoji, etc.).

### Stealth Execution
- **PowerShell**: `ScriptBlock::Create()`, `ExecutionContext.InvokeCommand`, `Invoke-Command` (randomized)
- **Bash**: `eval "$(…)"` with variable indirection (no pipe/subshell scope loss)
- **IEX Stealth**: Auto-replaces `IEX`/`Invoke-Expression` with `& ($ShellId[1]+$ShellId[13]+'X')`

---

## 📊 Analysis Dashboard

The built-in analysis panel provides real-time feedback:

- **Shannon Entropy** — Measures randomness (Higher = harder to fingerprint)
- **Detection Score** — Estimates probability of AV/EDR detection per active layer
- **Size Ratio** — Before/after payload size comparison
- **Validation** — Checks balanced delimiters and structural integrity

---

## 🚀 Quick Start

```bash
# Clone the repository
git clone https://github.com/Ilias1988/payload-obfuscator.git
cd payload-obfuscator

# Install dependencies
npm install

# Start development server
npm run dev

# Build for production
npm run build
```

Then open `http://localhost:5173` in your browser.

Or just visit the **[Live Demo →](https://payload-obfuscator.dev/)**

---

## 📁 Project Structure

```
payload-obfuscator/
├── index.html                    # SEO-optimized shell
├── vite.config.js                # Vite configuration
├── tailwind.config.js            # Tailwind theme (dark terminal)
├── scripts/
│   └── build.mjs                 # Production build script
├── public/
│   ├── robots.txt
│   └── sitemap.xml
└── src/
    ├── App.jsx                   # Main application
    ├── main.jsx                  # React entry point
    ├── index.css                 # Tailwind + custom styles
    ├── components/
    │   ├── layout/               # Header, Footer
    │   ├── panels/               # Input, Output, Options, Analysis, Language
    │   ├── seo/                  # SEOHead, SEOContent
    │   └── ui/                   # CopyButton, EntropyMeter, Toast
    ├── data/
    │   └── techniques.js         # Languages, layers, templates
    ├── engines/
    │   ├── powershell.js         # PowerShell engine (8 layers)
    │   ├── python.js             # Python engine (6 layers)
    │   ├── bash.js               # Bash engine (6 layers)
    │   ├── csharp.js             # C# engine (8 layers)
    │   ├── golang.js             # Go engine (7 layers)
    │   ├── controlflow.js        # Scope-aware CFF engine
    │   └── amsi.js               # AMSI/ETW patch generator
    ├── hooks/
    │   └── useObfuscator.js      # Core state management
    └── utils/
        ├── encoding.js           # Base64, Hex, XOR, resolveLanguageEscapes()
        ├── entropy.js            # Shannon entropy + detection scoring
        ├── parser.js             # Context-aware tokenizer
        ├── randomization.js      # Variable/function name generation
        └── validator.js          # Output validation
```

---

## 🛠️ Tech Stack

| Technology | Purpose |
|-----------|---------|
| **React 18** | UI framework |
| **Vite 5** | Build tool & dev server |
| **Tailwind CSS 3.4** | Styling (dark terminal theme) |
| **Lucide React** | Icons |
| **React Helmet Async** | Dynamic SEO meta tags |

---

## 📋 Templates

7 pre-built payload skeletons included:

- ⚡ PowerShell Download Cradle
- 🛡️ AMSI Bypass Template
- 🏴 Master Payload v3.0 (AMSI + Stealth IEX + Download Cradle)
- 🐍 Python Reverse Shell
- 🐚 Bash Reverse Shell
- 🔷 C# Shellcode Loader Skeleton
- 🔹 Go Reverse Shell

---

## 📌 Version History

| Version | Highlights |
|---------|------------|
| v5.3 | B64-first Unicode safety (all engines), `resolveLanguageEscapes()`, escape sequence fix, Python XOR B64-first |
| v5.2 | F-string var rename sync, `as`/`for` capture, 2-phase randomization |
| v5.1 | Dead code `__import__()` safety — zero NameError crashes |
| v5.0 | F-string deconstruction, context-aware parser |
| v4.5 | Polymorphic encryption wrappers (4 methods), stealth exec |
| v4.1 | Scope-aware CFF rewrite (brace counting, atomic try/catch) |
| v4.0 | XOR String Encryption, Control Flow Flattening |
| v3.0 | IEX Stealth, AMSI templates, entropy analysis |
| v2.0 | Context-aware parser, string-safe encoding |
| v1.0 | 5 languages, 5 layers, basic obfuscation |

---

## 📜 License

MIT License — See [LICENSE](LICENSE) for details.

---

## 👤 Author

**Ilias Georgopoulos**

- 🌐 [Website](https://ilias1988.me/)
- 💻 [GitHub](https://github.com/Ilias1988)
- 🐦 [X / Twitter](https://x.com/EliotGeo)

---

<p align="center">
  <sub>Built with ☕ and 🔥 for the red team community</sub>
</p>
