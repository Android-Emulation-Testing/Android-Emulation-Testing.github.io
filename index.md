![license](https://img.shields.io/badge/Platform-Android-green "Android")
![license](https://img.shields.io/badge/Version-Beta-yellow "Version")
![license](https://img.shields.io/badge/Licence-Apache%202.0-blue.svg "Apache")

## Table of Contents
- [About this Study](#about-this-study)
- [Code and Data Release](#code-and-data-release)
  - [Code Release](#code-release)
    - [Failure Scene Capture](#failure-scene-capture)
    - [Enhancements](#enhancements)
    - [Failure Discrepancy Report](#failure-discrepancy-report)
  - [Data Release](#data-release)
    - [Data Format](#data-format)

## About this Study

This paper conducts a systematic and rigorous study on
emulation-based mobile app testing as to the fidelity of test
results, as motivated by its huge advantages and side effects
compared to testing apps on physical devices. Leveraging a
custom-built virtualized testing infrastructure with its physical
counterpart at scale, we identify the key aspects contributing
to test result discrepancies to be specific system
add-ons and corrupted regional ecosystems, rather than commonly
believed factors such as heterogeneous hardware and
general customizations. These findings lead to practical solutions
that boost the testing fidelity by effectively managing
conflicts among stakeholders at both the emulator and app
levels. We hope that our infrastructure, experiences, and enhancements
will foster a more viable mobile ecosystem by
making app testing more accurate, affordable, and scalable.

## Code and Data Release

The code and data involved in our study are provided in [this github repository](https://github.com/Android-Emulation-Testing/Code-and-Data-Release).
They are organized as follows.

```
Code-and-Data-Release
|---- Failure Scene Capture
|---- Enhancements
      |---- Graphics Resource Format Extension
      |---- Background Management Strategy Adaptation
      |---- Dynamic Binary Patching
|---- Measurement Data
```

### Code Release

#### Failure Scene Capture

To effectively capture failure scenes, we propose a considerate method that combines content-aware memory image pruning with failsafe data collection.
We have provided the source code of the failure scene capture mechanisms in the [`Failure Scene Capture` folder](https://github.com/Android-Emulation-Testing/Code-and-Data-Release/tree/main/Failure%20Scene%20Capture).

#### Enhancements

In order to effectively enhance the testing fidelity on virtualized devices, we have devised threefold enhancements that eliminate most of the failure discrepancies in reality:

 * Graphics Resource Format Extension
 * Background Management Strategy Adaptation
 * Dynamic Binary Patching

For each enhancement, we have released our source code as well as a detailed `README.md` document.
For more information, please consult the [`Enhancements` folder](https://github.com/Android-Emulation-Testing/Code-and-Data-Release/tree/main/Enhancements).

#### Failure Discrepancy Report

We have reported the root causes and solutions of the failure discrepancies to all the corresponding stakeholders, including phone vendors (e.g., Huawei, Honor, and Meizu) and hardware manufacturers (e.g., MediaTek).
The complete list of our reported failures is provided below.

| Index | Stakeholder | Description | Current State |
| ----- | ----------- | ----------- | ------------- |
| 1     | Huawei | Integer overflow during implicit conversions | Confirmed & Fixed |
| 2     | Meizu | Improper null-terminations of C/C++ strings in vendor modules | Confirmed & Fixed |
| 3     | Honor | Integer overflow during implicit conversions | Confirmed & Fixed |
| 4     | Huawei, Xiaomi | Deadlock in system server when accessing local media files | Confirmed & Fixed |
| 5     | Smartisan | Incorrect handling of page faults in the FUSE filesystem | Confirmed & Fixed |
| 6     | MediaTek | Errors in MediaTek’s GPU drivers | Confirmed |
| 7     | Samsung | Array index out of bounds in vendor modules | Confirmed |
| 8     | Google | Graphics resource format inconsistency | [Reported](https://issuetracker.google.com/issues/262255458) |

### Data Release

To benefit the community, we have provided in part the measurement data (with proper anonymization) in the [`Measurement Data` folder](https://github.com/Android-Emulation-Testing/Code-and-Data-Release/tree/main/Measurement%20Data). 
We will release the full dataset as soon as we obtain official approval of the relevant authorities.

#### Data Format

The data file is organized in `.csv` format. 
Each row corresponds to a failure event.
The attributes of each failure event are organized as follows:

|  Attribute   | Description  |
|  ----  | ----  |
| error  | The triggered exception/signal of the failure. |
| scene  | A brief summary of the anonymized failure scene. |
| os_version  | The Android version of the device producing the failure. |
| device_brand  | The brand of the device producing the failure. |
| device_model  | The model of the device producing the failure. |
| device_type  | The type of the device. Specifically, `physical` denotes a physical device and `virtualized` denotes a virtualized device. |
| failure_layer  | The layer in which the failure occurred. Specifically, `java` and `native` denote that the failure occurred in the Java or the native layer, respectively. |
