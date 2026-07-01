# References

## Standards & Specifications
- NIST SP 800-193 — Platform Firmware Resiliency Guidelines
- NIST FIPS 186-5 — Digital Signature Standard (DSS)
- NIST FIPS 180-4 — Secure Hash Standard (SHS)
- TCG (Trusted Computing Group) — TPM 2.0 Library Specification
- RFC 9334 — Remote ATtestation procedureS (RATS) Architecture
- PSA Certified — Platform Security Architecture (Root of Trust,
  Attestation, Certification levels)

## Arm / TrustZone / TF-A
- Arm — "TrustZone Technology for Armv8-M" whitepaper
- Arm — "TrustZone for Cortex-A" architecture overview
- ARM Trusted Firmware-A (TF-A) documentation — Trusted Board Boot design
  (BL1/BL2/BL31/BL32/BL33 stage model)
- OP-TEE documentation (open-source TEE reference implementation)

## Vendor Secure Boot Implementations (for comparison study)
- STMicroelectronics — SBSFU (Secure Boot and Secure Firmware Update),
  STM32 option bytes / RDP levels
- Nordic Semiconductor — nRF Secure Bootloader (MCUboot-based)
- NXP — HAB (High Assurance Boot) for i.MX
- Qualcomm — Secure Boot / Trusted Execution Environment documentation
- Android — Verified Boot (AVB) documentation (rollback index, dm-verity)

## Attacks / Offensive Security Research
- "Fusée Gelée" — Tegra X1 Boot ROM USB exploit writeup (ShofEL2/fail0verflow)
- Riscure & ChipWhisperer — fault injection / glitching resources and
  open-source glitching hardware/tutorials
- Various CVE writeups on Secure/Verified Boot bypasses (search
  "secure boot bypass CVE" per vendor for current examples)

## Suggested reading order
1. PSA Certified Root of Trust guide (ties 00, 02, 06 together)
2. Arm TrustZone whitepapers (ties 03, 04 together)
3. TF-A Trusted Board Boot design doc (deep dive on 04)
4. NIST SP 800-193 (ties 07, 09 together)
5. TCG TPM 2.0 spec + RFC 9334 (deep dive on 08)

> Note: Fetch the latest versions of these documents from their official
> sites (arm.com, trustedfirmware.org, nist.gov, trustedcomputinggroup.org)
> since URLs/spec versions change over time.
