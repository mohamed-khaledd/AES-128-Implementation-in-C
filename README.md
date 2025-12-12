# AES-128 Implementation in C

A high-performance implementation of the Advanced Encryption Standard (AES-128) algorithm. This project was developed to meet strict performance constraints without relying on external cryptographic libraries (like OpenSSL).

## Key Features

* **T-Table Optimization:** Pre-computes 4KB lookup tables (Te0-Te3) to combine SubBytes, ShiftRows, and MixColumns into single CPU operations for maximum throughput.
* **Zero Dependencies:** Implemented entirely in standard C using only native headers (`<stdio.h>`, `<stdlib.h>`, `<stdint.h>`, `<string.h>`).
* **NIST Compliant:** Verified against official National Institute of Standards and Technology (NIST) test vectors.
* **Equivalent Inverse Cipher:** Implements the optimized decryption routine where round keys are pre-transformed by Inverse MixColumns.
* **Fast I/O:** Uses 64KB block buffering to minimize disk latency during large file processing.

## Build Instructions

The code is designed to be compiled with aggressive optimization flags (`-O3`) for maximum speed.

```bash
gcc -O3 aes.c -o aes.exe
```
## Usage

The program supports both encryption (e) and decryption (d) via command-line arguments.

Syntax:
```bash
./aes.exe <mode> <key_file> <input_file> <output_file>
```
To encrypt a file:
```bash
./aes.exe "e" key.bin plain.bin cipher.bin
```

To deccrypt a file:
```bash
./aes.exe "d" key.bin cipher.bin decrypted.bin
```

## Input Requirements
* Key File: Must be exactly 16 bytes (128 bits).
* Input File: Must be a multiple of 16 bytes.

