# Glossary

- **RoT (Root of Trust)** — The first component/data trusted unconditionally
  in a system; typically immutable Boot ROM code plus an OTP-anchored key.
- **Chain of Trust (CoT)** — Sequence of stages where each verifies the
  next before executing it.
- **Boot ROM / Mask ROM** — Immutable first-executed code, burned at fab time.
- **OTP (One-Time Programmable) / eFuse** — Write-once memory for secrets,
  config, and lock bits.
- **TrustZone** — Arm hardware technology splitting a system into Secure
  and Non-Secure worlds (TrustZone-M for Cortex-M, TrustZone-A for Cortex-A).
- **Secure Monitor (EL3)** — Code (e.g., TF-A BL31) that mediates
  transitions between Secure and Non-Secure worlds via SMC calls.
- **TEE (Trusted Execution Environment)** — A secure-world OS/runtime
  (e.g., OP-TEE) hosting trusted applications (DRM, key storage, etc.).
- **BL1/BL2/BL31/BL32/BL33** — ARM Trusted Firmware-A canonical boot
  stage names (see 04-soc-secure-boot).
- **SVN (Security Version Number)** — Version counter tracking security
  fixes, used for anti-rollback checks, distinct from feature version.
- **Monotonic counter** — A counter that can only increase, used to
  prevent firmware downgrade attacks.
- **Measured boot** — Recording cryptographic hashes ("measurements") of
  each boot stage into a tamper-evident log/PCR, for later attestation.
- **Attestation** — Proving to a remote party what code state a device is
  in, via a signed report of its measurements.
- **PCR (Platform Configuration Register)** — TPM register that can only
  be "extended" (hash-chained), not overwritten, tamper-evident.
- **PUF (Physical Unclonable Function)** — Hardware mechanism deriving a
  device-unique secret from manufacturing variations, without storing it.
- **dm-verity** — Linux kernel feature providing block-level integrity
  verification of a read-only filesystem, extending the chain of trust
  into the running OS.
- **Fault injection / glitching** — Physically disturbing a chip (voltage,
  clock, EM, laser) to corrupt execution and bypass security checks.
- **TOCTOU (Time-Of-Check to Time-Of-Use)** — Race condition where data
  is verified, then changed before it's actually used/executed.
- **HSM (Hardware Security Module)** — Tamper-resistant hardware for
  generating/storing/using private keys, keeping them from ever leaving.
