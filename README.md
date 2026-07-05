# 🔐 Android Private Signing Keys Generator

<p align="center">

<img src="https://img.shields.io/badge/Type-Signing%20Keys%20Generator-blue?style=for-the-badge">
<img src="https://img.shields.io/badge/Usage-ROM%20Security-green?style=for-the-badge">
<img src="https://img.shields.io/badge/Target-AOSP%20Build%20System-orange?style=for-the-badge">

</p>

---

## 📌 Overview

This repository contains scripts and examples for generating **private signing keys** used in Android custom ROM builds.

These keys are required for signing system components, allowing secure updates and verified builds.

---

## ⚙️ What’s included

- `keys.sh` – Generates a full set of signing keys in bulk  
- `make_key.sh` – Generates a single signing key  
- Example key structure for ROM signing  
- Predefined configuration templates for AOSP/Lineage-compatible builds  

---

## 🔐 Key generation

### Generate full keyset

To generate all required signing keys at once:

```bash id="genfull"
./keys.sh
```

##Generate single key

To generate an individual signing key:
```bash
./make_key.sh <key_name>
```
Example:

```bash
./make_key.sh releasekey
```

## 📁 Output

Generated keys will typically include:

- ```platform.pk8 / platform.x509.pem```
- ```releasekey.pk8 / releasekey.x509.pem```
- ```media.pk8 / media.x509.pem```
- ```shared.pk8 / shared.x509.pem```
- ```networkstack.pk8 / networkstack.x509.pem```
- and other AOSP signing keys

Location depends on script configuration (usually ```./keys/``` or similar).

## ⚠️ Important notes
- These keys are **self-generated and not Google-signed**
- They are intended for **personal ROM builds only**
- Do NOT share your private keys publicly
- Losing keys means you cannot perform signed OTA updates for existing users

## 🧩 Usage in ROM builds

Keys generated from this repository are typically used in:

```build/target/product/security/```
custom ```vendor/lineage-priv/``` setups
OTA signing pipelines

Make sure your build system references the generated keys correctly.

## 🚧 Disclaimer

This repository is intended for development and educational purposes only.

The maintainer is not responsible for misuse of generated cryptographic keys or insecure deployment practices.
