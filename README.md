# Goldshell SC5 Pro Firmware Research

Independent community research into the **Goldshell SC5 Pro** ASIC miner firmware, including reverse engineering, hardware configuration, thermal management, and firmware upgrade/recovery mechanisms.

## Stock Firmware 2.2.0

| Property | Value |
|---|---|
| Manufacturer | Goldshell |
| Model | **SC5 Pro** |
| Version | **2.2.0** (based on supplied filename; not confirmed by a running miner) |
| Filename | `firmware-Goldshell-SC5Pro-2.2.0.cpb` |
| Format | Goldshell `.cpb` firmware package |
| Algorithm | Blake2b / Siacoin |
| File size | **34,620,416 bytes** |
| SHA-256 | `890dc21e8c7a814eb829998712cf8eb2cd7b8ff6f716d9bf57f7947e84fd81ec` |

**[Download Firmware Release v2.2.0](https://github.com/booozytheclown/goldshell-sc5pro-firmware/releases/tag/stock-2.2.0)**

**[Direct firmware download (.cpb)](https://github.com/booozytheclown/goldshell-sc5pro-firmware/releases/download/stock-2.2.0/firmware-Goldshell-SC5Pro-2.2.0.cpb)**

**Compatibility warning:** This package is labeled for the **SC5 Pro**, not the SC5 (non-Pro), SC Lite, SC Box, or any other miner. Do not cross-flash firmware without independent, hardware-specific verification.

**Firmware update vs. recovery:** This `.cpb` is a firmware package. It has *not* been demonstrated to be a raw microSD/eMMC recovery image. Do not write it directly to an SD card or assume it restores a bricked miner.

### Read-only Package Inspection

- The package header identifies an internal archive named `firmware-MCB_V4_3.tgz` (**not proof** of the miner's control-board revision).
- A gzip-compressed TAR archive starts at offset 512 bytes and includes:
  - `firmware.ius` (43,587,072 bytes, uncompressed size)
  - `firmware.ius.sig` (512 bytes)
- A signature file is present, but the signature's validity and Goldshell authenticity were **not** verified. No firmware was executed or flashed.

### SHA-256 Verification

The SHA-256 hash was independently computed against the supplied 34,620,416-byte `.cpb` file and recorded in `firmware-Goldshell-SC5Pro-2.2.0.cpb.sha256`.

Linux (place both files together):

```bash
sha256sum -c firmware-Goldshell-SC5Pro-2.2.0.cpb.sha256
```

Windows PowerShell:

```powershell
Get-FileHash -LiteralPath ".\firmware-Goldshell-SC5Pro-2.2.0.cpb" -Algorithm SHA256
```

Expected hash:

```text
890dc21e8c7a814eb829998712cf8eb2cd7b8ff6f716d9bf57f7947e84fd81ec
```

A matching hash demonstrates integrity relative to this reference copy; it does **not** establish manufacturer authenticity or safety.

## Research Objectives

- Reverse engineer the original SC5 Pro firmware and document its internal components.
- Investigate firmware validation, signature verification, upgrade, and recovery mechanisms.
- Document miner hardware interfaces, configuration, fan speeds, and thermal management.
- Explore Blake2b compatibility and performance, distinguishing verified results from experiments.
- Publish reproducible findings and encourage community development.

## Contributing

Community contributions are welcome! Use GitHub Issues to report findings, questions, or reproducible test results, and submit Pull Requests for documentation and independently developed tools.

Do not publish passwords, wallet secrets, miner credentials, serial numbers, or personal data. Treat modified and cross-model firmware as potentially unsafe.

## Disclaimer

This is an independent community project and is **not affiliated with or endorsed by Goldshell**.

Original manufacturer firmware remains subject to its intellectual property rights; publishing it for study does **not** make its proprietary contents open source.

Firmware modifications and flashing carry risks including hardware damage and device failure. No guarantee is made as to package safety, authenticity, recovery capability, compatibility, or fitness for production use.
