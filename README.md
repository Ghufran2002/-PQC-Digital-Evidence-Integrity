# 🔐 Post-Quantum Cryptography for Digital Evidence Integrity

[![NIST Standards](https://img.shields.io/badge/NIST-FIPS%20203--206-blue?style=for-the-badge)](https://csrc.nist.gov/projects/post-quantum-cryptography)
[![Quantum Resistant](https://img.shields.io/badge/Quantum-Resistant-green?style=for-the-badge)](https://github.com/Ghufran2002/PQC-Digital-Evidence-Integrity)
[![WebCrypto API](https://img.shields.io/badge/WebCrypto-AES--256%20%7C%20ECDSA%20%7C%20SHA--512-cyan?style=for-the-badge)](https://developer.mozilla.org/en-US/docs/Web/API/Web_Crypto_API)
[![License](https://img.shields.io/badge/License-MIT-yellow?style=for-the-badge)](LICENSE)

> **A comprehensive research project and interactive demonstration system** for Post-Quantum Cryptographic algorithms applied to digital evidence authentication, chain-of-custody verification, and long-term archival integrity.

---

## 🌐 Live Demo

**👉 [Click Here to Run Live Demo](https://ghufran2002.github.io/-PQC-Digital-Evidence-Integrity/)**

---

## 📋 Table of Contents

- [Overview](#overview)
- [Features](#features)
- [NIST PQC Standards](#nist-pqc-standards)
- [Cryptographic Implementation](#cryptographic-implementation)
- [Project Structure](#project-structure)
- [How to Run](#how-to-run)
- [Demo Walkthrough](#demo-walkthrough)
- [Research Paper](#research-paper)
- [Technologies Used](#technologies-used)
- [Author](#author)

---

## 🔍 Overview

The rapid advancement of **quantum computing** poses an unprecedented threat to classical cryptographic algorithms (RSA, ECDSA, ECDH) that underpin digital evidence integrity in law enforcement, judicial proceedings, and forensic investigations.

This project demonstrates:
- **Why classical cryptography fails** against quantum computers (Shor's & Grover's algorithms)
- **NIST-standardized PQC algorithms** as quantum-resistant replacements
- **Real cryptographic operations** using browser WebCrypto API
- **Complete chain-of-custody protocol** with tamper detection

---

## ✨ Features

### Real Cryptographic Operations (WebCrypto API)
| Feature | Algorithm | Status |
|---------|-----------|--------|
| Evidence Hashing | SHA-256 / SHA-384 / SHA-512 | ✅ Production Grade |
| Digital Signatures | ECDSA P-256 | ✅ Production Grade |
| Evidence Encryption | AES-256-GCM | ✅ Production Grade |
| Chain of Custody | SHA-256 Hash Chain | ✅ Production Grade |

### Post-Quantum Simulation (NIST FIPS 203-206)
| Algorithm | Standard | Purpose | Security Level |
|-----------|----------|---------|----------------|
| CRYSTALS-Kyber-768 | FIPS 203 | Key Encapsulation | NIST Level 3 |
| CRYSTALS-Dilithium3 | FIPS 204 | Digital Signatures | NIST Level 3 |
| SPHINCS+-SHA2-256s | FIPS 205 | Hash-Based Signatures | NIST Level 5 |
| FALCON-512 | FIPS 206 | Compact Signatures | NIST Level 1 |

---

## 🔬 NIST PQC Standards

```
FIPS 203 — CRYSTALS-Kyber    → Replaces ECDH / RSA-OAEP key exchange
FIPS 204 — CRYSTALS-Dilithium → Replaces ECDSA / RSA-PSS signatures  
FIPS 205 — SPHINCS+           → Long-term archival timestamps (50 years)
FIPS 206 — FALCON             → Compact signatures for mobile forensics
```

### Why PQC is Needed?

```
Classical Algorithm    Quantum Attack        Impact
─────────────────────────────────────────────────────
RSA-2048          →   Shor's Algorithm  →   BROKEN ❌
ECDSA P-256       →   Shor's Algorithm  →   BROKEN ❌
AES-128           →   Grover's Algorithm →  Weakened ⚠️
SHA-256           →   Grover's Algorithm →  Weakened ⚠️
─────────────────────────────────────────────────────
Dilithium3        →   No known attack   →   SAFE ✅
Kyber-768         →   No known attack   →   SAFE ✅
```

---

## 💻 Cryptographic Implementation

### 1. SHA Evidence Hashing
```javascript
// Real SHA-256/384/512 using WebCrypto API
const hashBuffer = await crypto.subtle.digest('SHA-256', encodedData);
const hashHex = buf2hex(hashBuffer);
// Output: 64-character hex fingerprint of evidence
```

### 2. ECDSA Digital Signature
```javascript
// Real ECDSA P-256 key generation
const keyPair = await crypto.subtle.generateKey(
  { name: 'ECDSA', namedCurve: 'P-256' },
  true, ['sign', 'verify']
);

// Sign evidence
const signature = await crypto.subtle.sign(
  { name: 'ECDSA', hash: 'SHA-256' },
  keyPair.privateKey, evidenceData
);
```

### 3. AES-256-GCM Encryption
```javascript
// Real AES-256-GCM encryption
const key = await crypto.subtle.deriveKey(
  { name: 'PBKDF2', salt, iterations: 100000, hash: 'SHA-256' },
  keyMaterial,
  { name: 'AES-GCM', length: 256 },
  false, ['encrypt', 'decrypt']
);
const ciphertext = await crypto.subtle.encrypt(
  { name: 'AES-GCM', iv }, key, plaintext
);
```

### 4. PQC — Dilithium3 (FIPS 204)
```
Key Generation:
  Public Key  : 1,952 bytes
  Secret Key  : 4,000 bytes
  
Signing:
  Signature   : 3,293 bytes
  Security    : NIST Level 3 (AES-192 equivalent)
  
vs ECDSA P-256:
  Signature   : 72 bytes (44x smaller — but QUANTUM BROKEN)
```

---

## 📁 Project Structure

```
PQC-Digital-Evidence-Integrity/
│
├── index.html                              # Main interactive demo application
├── PQC_Digital_Evidence_Research_Paper.docx # Full research paper
└── README.md                              # This file
```

---

## 🚀 How to Run

### Option 1: Direct Browser (Easiest)
```
1. Download index.html
2. Double click → Opens in Chrome/Edge
3. All features work offline!
```

### Option 2: VS Code Live Server
```
1. Open folder in VS Code
2. Install "Live Server" extension
3. Click "Go Live" bottom right
4. Opens at http://127.0.0.1:5500
```

### Option 3: GitHub Pages (Online)
```
Visit: https://ghufran2002.github.io/-PQC-Digital-Evidence-Integrity/
```

> **Note:** No installation required! Runs entirely in browser using WebCrypto API. No data is sent to any server — all cryptographic operations are local.

---

## 🎯 Demo Walkthrough

### Tab 1 — SHA Evidence Hashing
1. Type any evidence text in the input box
2. Click **"Compute Hash"**
3. Real SHA-256 fingerprint generated instantly
4. Try **"Compare Hashes"** — change one character, entire hash changes!

### Tab 2 — ECDSA Digital Signing
1. Click **"Generate ECDSA P-256 Key Pair"** — real cryptographic keys
2. Enter evidence data
3. Click **"Sign Evidence"** — real digital signature created
4. Click **"Verify Signature"** → ✅ VALID
5. Click **"Tamper + Verify"** → ❌ INVALID — tampering detected!

### Tab 3 — AES-256-GCM Encryption
1. Enter sensitive evidence data
2. Set a password
3. Click **"Encrypt"** — military-grade encryption applied
4. Click **"Auto Fill"** then **"Decrypt"** — original data recovered
5. Try wrong password → Decryption FAILS ❌

### Tab 4 — Chain of Custody
1. Click **"Build Real Hash Chain"** — 5-block custody chain created
2. Click **"Tamper Block 3"** — simulates adversary attack
3. Click **"Verify Chain"** → ❌ Chain broken at Block 3!

### Tab 5 — PQC Algorithm Suite
1. Select algorithm (Dilithium3 recommended)
2. Click **"Simulate KeyGen"** — see real key sizes
3. Enter evidence, click **"Simulate Sign"**
4. Compare with Classical vs PQC table below

---

## 📄 Research Paper

The included research paper covers:

| Section | Topic |
|---------|-------|
| Chapter 1 | Introduction & Quantum Threat Background |
| Chapter 2 | Quantum Computing Attacks (Shor's & Grover's) |
| Chapter 3 | NIST PQC Algorithm Analysis (FIPS 203-206) |
| Chapter 4 | Proposed PQC Architecture for Evidence Systems |
| Chapter 5 | Performance Benchmarks & Implementation |
| Chapter 6 | Legal & Regulatory Framework |
| Chapter 7 | Migration Roadmap 2024-2030 |
| Chapter 8 | Future Research Directions |
| Chapter 9 | Conclusion |

---

## 🛠️ Technologies Used

| Technology | Purpose |
|------------|---------|
| **WebCrypto API** | Real cryptographic operations in browser |
| **ECDSA P-256** | Digital signature generation & verification |
| **AES-256-GCM** | Evidence encryption & decryption |
| **SHA-256/384/512** | Cryptographic evidence hashing |
| **PBKDF2** | Password-based key derivation |
| **HTML5 / CSS3 / JavaScript** | Frontend implementation |
| **NIST FIPS 203-206** | PQC algorithm specifications |

---

## 🔒 Security Note

> All cryptographic operations run **locally in your browser** using the built-in WebCrypto API. No data is transmitted to any server. This project is for educational and research demonstration purposes.

---

## 👨‍💻 Author

**Md Ghufran Alam**  
GitHub: [@Ghufran2002](https://github.com/Ghufran2002)

---

## 📚 Key References

1. NIST FIPS 203 — CRYSTALS-Kyber (2024)
2. NIST FIPS 204 — CRYSTALS-Dilithium (2024)
3. NIST FIPS 205 — SPHINCS+ (2024)
4. NIST FIPS 206 — FALCON (2024)
5. Shor, P.W. (1994) — Quantum Factoring Algorithm
6. Bernstein & Lange (2017) — Post-Quantum Cryptography, Nature

---

<div align="center">

**⭐ Star this repository if you found it helpful!**

![Quantum Safe](https://img.shields.io/badge/Quantum-Safe%20Future-blueviolet?style=for-the-badge)

</div>
