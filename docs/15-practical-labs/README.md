# 15 — Practical Labs

## Goal

Turn the theory from 00-09 into a working (toy, host-simulated) secure
boot chain you can build and run on your dev machine — no real hardware
required to start. Then, optionally, port to a real Cortex-M dev board.

## Lab 1 — Build a minimal ECDSA sign/verify tool

**Objective:** Understand key generation, signing, verifying (folder 05)
using OpenSSL.

```bash
# Generate an EC P-256 keypair (this represents the vendor root key)
openssl ecparam -name prime256v1 -genkey -noout -out root_priv.pem
openssl ec -in root_priv.pem -pubout -out root_pub.pem

# "Firmware image" to sign
echo "toy firmware binary contents" > firmware.bin

# Sign (offline / vendor side)
openssl dgst -sha256 -sign root_priv.pem -out firmware.sig firmware.bin

# Verify (device side — this is what your bootloader logic will do)
openssl dgst -sha256 -verify root_pub.pem -signature firmware.sig firmware.bin
```

## Lab 2 — Simulated Boot ROM verifier (host C program)

Implement `boot_sim.c`:
1. Reads `firmware.bin`, `firmware.sig`, `root_pub.pem`.
2. Simulates OTP by hardcoding/loading `root_pub_hash.bin`
   (`sha256sum root_pub.pem`).
3. Verifies the public key's hash matches the "OTP" hash.
4. Verifies the signature over the firmware.
5. Prints `BOOT ALLOWED` or `BOOT BLOCKED` — never "executes" anything
   real, just demonstrates the logic from folder 01/02.

Suggested libs: OpenSSL's `libcrypto` (EVP API) or mbedTLS if targeting
embedded later.

## Lab 3 — Add anti-rollback

Extend Lab 2:
- Add a 4-byte "security_version" header field to `firmware.bin`.
- Maintain a `counter.txt` file simulating an OTP monotonic counter.
- Reject verification if `image.version < counter`.
- Simulate a legitimate update bumping the counter.

## Lab 4 — Simulate a chain of trust (2 stages)

- Create `stage1.bin` signed by `root_priv.pem`.
- Create `stage2.bin` signed by a **separate intermediate key**, whose
  public key is embedded in a small "certificate" that itself is signed
  by `root_priv.pem`.
- Your simulator verifies: root → cert → stage2, exactly like folder 02's
  certificate chain model.

## Lab 5 — (Optional, requires a Cortex-M dev board)

Port your simulator logic onto a real MCU (e.g., STM32 Nucleo, nRF52 DK):
- Use the vendor's crypto HW accelerator (or mbedTLS/tinycrypt) to verify
  a real signed binary before jumping to it (`__set_MSP` + branch to
  reset handler — standard "bootloader jumps to app" pattern).
- Explore the vendor's actual secure boot feature (STM32 SBSFU, Nordic
  Secure Bootloader) and compare it against your toy implementation.

## Suggested folder layout for your lab code

```
15-practical-labs/
├── README.md          (this file)
├── lab1-sign-verify/
├── lab2-boot-sim/
├── lab3-anti-rollback/
├── lab4-cert-chain/
└── lab5-mcu-port/      (notes only, or real board project)
```

Create subfolders as you complete each lab; keep each self-contained with
its own small `README.md` documenting what you built and what you learned.

## Checklist
- [ ] Lab 1: I can sign and verify a file with OpenSSL from the CLI.
- [ ] Lab 2: My C program correctly rejects a tampered `firmware.bin`.
- [ ] Lab 3: My simulator blocks a rollback to an older security_version.
- [ ] Lab 4: My simulator verifies a 2-level certificate chain.
- [ ] Lab 5 (optional): I've made a real MCU refuse to jump to an
      unsigned/tampered binary.
