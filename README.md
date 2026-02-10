# Image2TextApp – Secure OCR Implementation

A professional Android application utilizing **Google ML Kit** for text extraction. This project serves as a practical case study for **Mobile Application Security (AppSec)**, featuring hardening techniques against common vectors found in the **OWASP Mobile Top 10**.

---

## 🔍 Security Assessment & Hardening
*This application has been audited using industry-standard security tools to ensure resilient architecture.*

### 1. Static Analysis (MobSF)
I integrated the following mitigations based on **MobSF (Mobile Security Framework)** reports:
* **Code Obfuscation:** Enabled **R8/ProGuard** to mangle class names and remove source file attributes, making reverse engineering significantly harder.
* **Manifest Security:** Verified that `allowBackup` is set to `false` to prevent sensitive data extraction via ADB backups.
* **Network Hardening:** Implemented a **Network Security Configuration** to enforce strict **TLS (HTTPS)** and disable cleartext traffic.

### 2. Dynamic Analysis (Frida)
Tested the runtime environment using **Frida** to verify memory safety:
* **Stateless Processing:** Verified that extracted text is stored in volatile memory and cleared after the UI lifecycle, minimizing the risk of memory dumping attacks.
* **Root Detection:** Planned implementation of integrity checks to prevent execution on compromised (rooted) devices.

---

## 🔐 Key AppSec Features

### 📸 Secure Camera & Permission Flow
- **Least Privilege:** Requests `CAMERA` permission only at the point of use.
- **Intent Protection:** Uses explicit intents for camera interactions to prevent **Intent Hijacking**.
- **On-Device ML:** Configured ML Kit for **100% On-Device processing**. No images or text are transmitted to the cloud, ensuring user privacy and compliance (GDPR/CCPA).

### 🛠️ Defensive Coding Practices
- **Logging Safety:** Integrated a release-build tree that strips all `Log.d` and `Log.v` calls to prevent sensitive info leakage in `logcat`.
- **Memory Management:** Overrode `onTrimMemory()` to securely flush Bitmaps from the heap after OCR completion.

---

## ⚠️ Threat Modeling (Potential Vectors vs. Mitigations)

| Threat Vector | Risk Level | Mitigation Implemented |
| :--- | :--- | :--- |
| **Reverse Engineering** | High | R8 Obfuscation & Metadata removal. |
| **Data Leakage (Cache)** | Medium | Use of internal `cacheDir` (UID-restricted) & automatic cleanup. |
| **Insecure Storage** | Medium | No persistence of extracted text in plaintext files. |
| **Screen Scraping** | Low | Optional `FLAG_SECURE` integration for sensitive results. |

---

## 🚀 Tech Stack & Tools
- **Language:** Kotlin
- **Architecture:** MVVM + Clean Architecture
- **Library:** Google ML Kit (Vision)
- **Security Tools:** MobSF, Frida, Jadx-GUI, Burp Suite.

---

## 🤝 Author
**Nikolai Vetrik** *Senior Security Engineer & Mobile Developer* 📧 [devnikolaivetrik@gmail.com](mailto:devnikolaivetrik@gmail.com) | 🔗 [LinkedIn](https://linkedin.com/in/nikolayvetrik24062010)

---
*Note: This project is part of a security portfolio demonstrating the transition from software engineering to specialized Application Security.*
