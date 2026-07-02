# References

## Standards & Specifications
- NIST SP 800-193 — Platform Firmware Resiliency Guidelines
- NIST FIPS 186-5 — Digital Signature Standard (DSS)
- NIST FIPS 180-4 — Secure Hash Standard (SHS)
- RFC 5280 — X.509 Public Key Infrastructure Certificate Profile
- TCG (Trusted Computing Group) — TPM 2.0 Library Specification
- RFC 9334 — Remote ATtestation procedureS (RATS) Architecture
- RFC 8446 — TLS 1.3
- PSA Certified — Platform Security Architecture (Root of Trust,
  Attestation, Certification levels)
- UEFI Forum — UEFI Specification, Secure Boot chapter (db/dbx, Secure
  Boot policy)

## Arm / TrustZone / TF-A
- Arm — "TrustZone Technology for Armv8-M" whitepaper
- Arm — "TrustZone for Cortex-A" architecture overview
- ARM Trusted Firmware-A (TF-A) documentation — Trusted Board Boot design
  (BL1/BL2/BL31/BL32/BL33 stage model), Firmware Image Package (FIP) spec
- Arm — PSCI (Power State Coordination Interface) specification
- Arm — SPM / FF-A (Firmware Framework for Arm A-profile) documentation
- OP-TEE documentation (open-source TEE reference implementation)

## Vendor Secure Boot Implementations (for comparison study)
- STMicroelectronics — SBSFU (Secure Boot and Secure Firmware Update),
  STM32 option bytes / RDP levels
- Nordic Semiconductor — nRF Secure Bootloader (MCUboot-based)
- NXP — HAB (High Assurance Boot) for i.MX
- Qualcomm — Secure Boot / Trusted Execution Environment documentation
- Android — Verified Boot (AVB) documentation (rollback index, dm-verity)
- Apple — Platform Security Guide (Secure Boot chain, Secure Enclave)

## Open-Source Bootloader / RTOS Projects (see folder 17)
- U-Boot — "Verified Boot" documentation (FIT image signing, `CONFIG_FIT_SIGNATURE`)
- MCUboot — project documentation (`docs/design.md`, `docs/imgtool.md` in
  the MCUboot GitHub repository)
- Zephyr Project — "Device Firmware Upgrade (DFU) and MCUboot" documentation
- FreeRTOS — OTA documentation (AWS IoT FreeRTOS OTA Agent library)
- Trusted Firmware-M (TF-M) — PSA Root of Trust reference implementation
  documentation (trustedfirmware.org)
- OP-TEE — documentation and Trusted Application development guide

## Domain-Specific Standards (see folder 16)
- **Automotive**: ISO/SAE 21434, ISO 26262, UNECE R155/R156, AUTOSAR
  SecOC/CSM, EVITA HSM profiles
- **Mobile/Consumer**: Android Verified Boot, Apple Secure Boot Chain,
  PSA Certified, GlobalPlatform TEE/SE specs, FIDO Alliance attestation
- **IoT/Embedded**: PSA Certified, NIST IR 8259, NIST SP 800-193, ETSI EN
  303 645, IEC 62443, Matter/CSA Device Attestation Certificate
- **Payment**: PCI PTS, PCI HSM, EMVCo Security Requirements, Common
  Criteria (EAL4+/5+/6+), FIPS 140-2/140-3
- **Server/Cloud**: UEFI Secure Boot, TCG TPM 2.0, DMTF SPDM, NIST SP
  800-193, Confidential Computing Consortium specs (Intel TDX, AMD
  SEV-SNP, Arm CCA)

## Attacks / Offensive Security Research
- "Fusée Gelée" — Tegra X1 Boot ROM USB exploit writeup (ShofEL2/fail0verflow)
- Riscure & ChipWhisperer — fault injection / glitching resources and
  open-source glitching hardware/tutorials
- Various CVE writeups on Secure/Verified Boot bypasses (search
  "secure boot bypass CVE" per vendor for current examples)

## Suggested reading order
1. PSA Certified Root of Trust guide (ties 00 Foundations, 02 Chain of
   Trust, 09 Key Management together)
2. RFC 5280 (X.509) + Arm TrustZone whitepapers (ties 03 Certificate
   Authority, 07 SoC Secure Boot together)
3. TF-A Trusted Board Boot design doc + PSCI spec (deep dive on 07 SoC
   Secure Boot)
4. NIST SP 800-193 (ties 11 Anti-Rollback, 14 Attacks & Mitigations
   together)
5. TCG TPM 2.0 spec + RFC 9334 (deep dive on 12 Attestation)
6. Your domain's standard from folder 16 (e.g., ISO/SAE 21434 for
   automotive, PCI HSM for payment) as the final compliance layer
7. U-Boot Verified Boot docs + MCUboot design doc (ties 07 SoC Secure
   Boot and 05 MCU Secure Boot to their real open-source implementations
   in folder 17)

> Note: Fetch the latest versions of these documents from their official
> sites (arm.com, trustedfirmware.org, nist.gov, trustedcomputinggroup.org,
> uefi.org, globalplatform.org, iso.org) since URLs/spec versions change
> over time.
