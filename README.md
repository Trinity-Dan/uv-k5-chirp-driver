# UV-K5 CHIRP Driver — KN2Q Eleven Scan Banks

This repository contains the matching CHIRP driver for **KN2Q firmware v1.0.0** on supported Quansheng UV-K1 and UV-K5 V3 radios.

The KN2Q firmware and driver extend the inherited three-list system to **eleven independent scan banks**. A memory channel can belong to any combination of Scan Banks 1–11, making it possible to organize channels by location, service, activity, or operating role without creating duplicate memories.

## Compatibility

- KN2Q firmware v1.0.0
- Quansheng UV-K1 using the PY32F071 MCU
- Quansheng UV-K5 V3 using the PY32F071 MCU
- Fusion builds made from the matching KN2Q firmware source
- CHIRP next/daily builds with developer mode and external-module loading

> [!IMPORTANT]
> This driver uses the KN2Q eleven-bank memory format. Use it only with matching KN2Q firmware. An incompatible stock or F4HWN driver may omit or misinterpret the extended scan-bank data.

## Features

- Eleven independently selectable scan banks
- Multiple scan-bank memberships per memory channel
- Per-channel Bank 1–11 controls in CHIRP's **Extra** fields
- Radio-wide selection of Bank 0, Banks 1–11, combined `1-11`, and `ALL` modes
- Compatibility with the on-radio `ScAdd1`–`ScAdd3` and `ScAd4`–`ScAd11` controls
- Support for the settings inherited from the F4HWN 4.3 driver

## Installation

Download `uvk5_kn2q.py` from this repository or from the corresponding release.

### Enable developer mode in CHIRP

This normally needs to be done only once:

1. Open CHIRP.
2. Open the **Help** menu and enable **Developer Mode**.
3. Accept the warning.
4. Close and reopen CHIRP when prompted.
5. Open the **View** menu and enable **Show Extra Fields**.

### Load the driver

The external driver must be loaded each time CHIRP is restarted:

1. Select **File → Load Module**.
2. Accept the external-module warning.
3. Browse to `uvk5_kn2q.py` and open it.
4. Confirm that CHIRP reports the module as loaded.

## Downloading From the Radio

1. Turn on the radio normally.
2. Insert the programming cable fully, then connect it to the computer.
3. Select **Radio → Download From Radio** in CHIRP.
4. Select the correct serial port.
5. Select the Quansheng/F4HWN entry supplied by the loaded module.
6. Click **OK** and wait for the download to finish.
7. Save an untouched copy of the downloaded image before making changes.

## Using the Eleven Scan Banks

In the **Memories** tab, enable **Show Extra Fields** and use each channel's Bank 1–11 fields to select its memberships. A channel can belong to one bank, several banks, or no banks.

The active scan mode is available under **Settings**:

- `0` scans channels assigned to no bank.
- `1`–`11` scan the selected bank.
- `1-11` scans the union of all eleven banks.
- `ALL` scans all programmed channels.

Membership can also be changed on the radio. Use `ScAdd1` through `ScAdd3` for the legacy banks and `ScAd4` through `ScAd11` for the extended banks.

After editing, select **Radio → Upload To Radio**. Do not disconnect the cable or turn off the radio until the upload finishes.

## Recommended First Use

1. Flash the matching KN2Q firmware.
2. Perform **Reset All** on the radio.
3. Load `uvk5_kn2q.py` in CHIRP.
4. Download a fresh image from the reset radio.
5. Save that untouched image as a backup.
6. Add or edit a small number of channels and upload them.
7. Confirm normal button, receive, transmit, and scan-bank operation before completing the configuration.

## Troubleshooting

If a button press unexpectedly causes transmit behavior or other controls act incorrectly after changing firmware or driver versions:

1. Perform **Reset All** on the radio.
2. Download a fresh image with the matching KN2Q driver.
3. Add the desired channels to that fresh image.
4. Upload it to the radio.

Do not reuse an image produced by an incompatible driver when diagnosing this behavior.

## Notes and Limitations

- This is an external development driver and is not included with standard CHIRP installations.
- A CHIRP update may require the module to be loaded again or may temporarily affect compatibility.
- Always download from the radio before uploading a configuration created with a different driver version.
- Keep an untouched backup of a known-good radio image.

## Related Firmware

Use the matching [KN2Q firmware for the UV-K1 and UV-K5 V3](https://github.com/Trinity-Dan/uv-k1-k5v3-firmware-kn2q).

## Credits

This project is based on the CHIRP driver for F4HWN firmware, which grew from the Quansheng UV-K5 and Egzumer firmware ecosystem.

Many thanks to F4HWN, the original driver authors and contributors, the CHIRP developers, and the wider UV-K5 community. This fork focuses on extending the multi-bank system from three banks to eleven while keeping the inherited capabilities and authorship recognized.

## Disclaimer

This software is provided without warranty. You are responsible for maintaining backups and ensuring that your radio is programmed and operated in accordance with applicable laws, license conditions, band plans, and local frequency-use restrictions.
