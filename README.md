# UV-K5 CHIRP Driver — KN2Q Eleven Scan Banks

This repository contains a modified CHIRP driver for Quansheng radios running the matching KN2Q build of the F4HWN firmware.

The primary change in this fork is support for **eleven scan banks**. A memory channel can be assigned independently to any combination of Scan Banks 1–11, making it easier to organize channels by purpose without duplicating them. For example, the same channel can belong to local, travel, amateur-radio, public-safety monitoring, or event-specific banks.

## Compatibility

- Quansheng UV-K5 family radios supported by the corresponding F4HWN firmware
- UV-K1, UV-K5 V3, and Fusion variants supported by the upstream driver
- The matching KN2Q firmware build with eleven-scan-bank support
- CHIRP next/daily builds with developer mode and external-module loading

> [!IMPORTANT]
> This driver changes how scan-bank membership is stored in the radio. Use it only with a matching firmware build that supports eleven scan banks. Using an incompatible driver or firmware may produce incorrect settings or channel data.

## Features

- Eleven independently selectable scan banks
- Multiple scan-bank memberships per memory channel
- Scan-bank configuration through CHIRP's **Extra** fields and radio settings
- Support for the settings and features inherited from the F4HWN CHIRP driver
- English interface text

## Installation

Download `uvk5_egzumer_f4hwn.py` from this repository or from the latest release.

### Enable developer mode in CHIRP

This normally needs to be done only once:

1. Open CHIRP.
2. Open the **Help** menu and enable **Developer Mode**.
3. Accept the warning.
4. Close and reopen CHIRP when prompted.
5. Open the **View** menu and enable **Show Extra Fields**.

### Load the driver

The external driver must be loaded each time CHIRP is restarted:

1. In CHIRP, select **File → Load Module**.
2. Accept the warning about loading an external module.
3. Browse to `uvk5_egzumer_f4hwn.py` and open it.
4. Confirm that CHIRP reports the module as loaded.

## Downloading From the Radio

1. Turn on the radio normally.
2. Insert the programming cable fully into the radio, then connect it to the computer.
3. In CHIRP, select **Radio → Download From Radio**.
4. Select the correct serial port.
5. Select the Quansheng/F4HWN entry supplied by the loaded driver.
6. Click **OK** and wait for the download to complete.
7. Save the downloaded image before making changes. This gives you a backup of the radio's current configuration.

## Using the Eleven Scan Banks

In the **Memories** tab, use the channel's **Extra** fields to select its scan-bank memberships. Each channel can belong to one bank, several banks, or no banks.

The radio-wide scan-bank settings are available under **Settings**. The exact labels shown in CHIRP may vary slightly with the CHIRP and firmware versions.

After editing the configuration, select **Radio → Upload To Radio**. Do not disconnect the cable or turn off the radio until the upload finishes.

## Recommended First Use

Before uploading anything:

1. Download the radio with this driver.
2. Save an untouched backup image.
3. Make a small test change.
4. Upload it and confirm that the radio operates correctly.

Keep the backup image in case you need to restore the original configuration.

## Notes and Limitations

- This is an external development driver and is not included with standard CHIRP installations.
- A CHIRP update may require the module to be loaded again or may temporarily affect compatibility.
- The eleven-bank format requires the matching KN2Q firmware and driver versions.
- Always download from the radio before uploading a configuration created with a different driver version.

## Credits

This project is based on the CHIRP driver created for the F4HWN firmware, which in turn grew from the Quansheng UV-K5 community and Egzumer firmware ecosystem.

Many thanks to F4HWN, the original driver authors and contributors, the CHIRP developers, and the wider UV-K5 community. This fork focuses on extending the existing scan-list implementation from three banks to eleven while retaining the upstream driver's other capabilities.

## Disclaimer

This software is provided without warranty. You are responsible for maintaining a backup and for ensuring that your radio is programmed and operated in accordance with applicable laws, license conditions, and local frequency-use restrictions.
