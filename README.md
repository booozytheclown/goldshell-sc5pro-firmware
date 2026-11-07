# Goldshell SC5 Pro Firmware Research

Independent community research into the **Goldshell SC5 Pro** ASIC miner's stock firmware, including reverse engineering, hardware configuration, fan and thermal controls, firmware upgrade mechanisms, and recovery research.

## Stock Firmware 2.2.0

| Property | Value |
|---|---|
| Manufacturer | Goldshell |
| Model | **SC5 Pro** |
| Firmware version | **2.2.0** (as identified by supplied filename; package not yet independently examined) |
| Filename | `firmware-Goldshell-SC5Pro-2.2.0.cpb` |
| Format | Goldshell `.cpb` firmware update package |
| Algorithm | Blake2b / Siacoin |
| Purpose | Archival reference and community firmware research |
| SHA-256 | **Pending local-file verification** |
| File size | **Pending local-file measurement** |

Find firmware downloads under [Releases](../../releases) once a release has been published.

**Compatibility warning:** This file is identified as firmware for the **SC5 Pro**. It must not be treated as compatible with the SC5 (non-Pro), SC Lite, SC Box, HS Box, or any other Goldshell model without independent hardware-specific validation. Cross-flashing can permanently disable a miner.

**Update vs. recovery:** The `.cpb` format is used for normal Goldshell firmware updates through the miner interface. It has **not** been verified as a standalone microSD / eMMC recovery image. Do not rename or write this file directly to an SD card on the assumption that it is a raw recovery image.

### SHA-256 Verification

After the original firmware file is available, record its SHA-256 digest and byte size here. Do not substitute a hash from a different firmware version or model.

Windows PowerShell:

```powershell
Get-Item -LiteralPath ".\firmware-Goldshell-SC5Pro-2.2.0.cpb" | Select-Object Name, Length
Get-FileHash -LiteralPath ".\firmware-Goldshell-SC5Pro-2.2.0.cpb" -Algorithm SHA256
```

Linux:

```bash
sha256sum firmware-Goldshell-SC5Pro-2.2.0.cpb
```

Once a matching `.sha256` file has been published, verify it with:

```bash
sha256sum -c firmware-Goldshell-SC5Pro-2.2.0.cpb.sha256
```

A matching SHA-256 establishes integrity relative to the published checksum; it does not independently establish manufacturer authenticity, malware-free operation, or suitability for flashing.

## Research Objectives

- Reverse engineer the original SC5 Pro firmware and document its embedded software components.
- Investigate update-package structure, validation, signatures, boot process, and possible recovery paths.
- Document miner hardware interfaces, configuration, fan speeds, and thermal controls.
- Explore Blake2b compatibility and performance, clearly distinguishing tested findings from hypotheses.
- Publish reproducible research and encourage community collaboration.

## Contributing

Community contributions are welcome. Use GitHub Issues for discoveries, questions, and reproducible test results. Submit Pull Requests for documentation or independently developed tools.

Do not publish passwords, wallet credentials, miner secrets, identifying serial numbers, or private configuration data. Treat all firmware modifications and flashing procedures as potentially destructive until validated.

## Disclaimer

This independent community project is **not affiliated with or endorsed by Goldshell**. Manufacturer firmware and documentation remain subject to their respective intellectual property rights; making a reference package available does not grant an open-source license to the proprietary contents.

No claim is made that the firmware is independently authenticated, safe, or verified to recover a failed device. Firmware modification, downgrade, cross-flashing, and recovery experiments can cause hardware damage or failure. Proceed only with an understood recovery plan and appropriate safeguards.
