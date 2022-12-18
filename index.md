![license](https://img.shields.io/badge/Platform-Android-green "Android")
![license](https://img.shields.io/badge/Version-Beta-yellow "Version")
![license](https://img.shields.io/badge/Licence-Apache%202.0-blue.svg "Apache")

## Table of Contents
- [About this Study](#about-this-study)
- [Code and Data Release](#code-and-data-release)
  - [Code Release](#code-release)
    - [Measurement Code](#measurement-code)
    - [Enhancements](#enhancements)
  - [Data Release](#data-release)
    - [Measurement Data](#measurement-data)
    - [Data Format](#data-format)

## About this Study

This paper conducts a systematic and rigorous study on
emulation-based mobile app testing, as motivated by its huge
advantages compared to testing apps on physical devices.
Leveraging a custom-built virtualized testing infrastructure
with its physical counterpart, we identify the key aspects contributing
to test result discrepancies to be specific system
add-ons and corrupted regional ecosystems, rather than commonly
believed factors such as heterogeneous hardware and
general customizations. These findings lead to practical solutions
that boost the testing fidelity by effectively managing
conflicts among stakeholders at both the emulator and app
levels. We hope that our infrastructure, insights, and enhancements
will foster a more viable mobile ecosystem by making
app testing more accurate, affordable, and scalable.

## Code and Data Release

We are currently preparing the code and data of this study for public release, and it will take one to two days if things go smoothly.

The code and data involved in our study will be released in [this github repository](https://github.com/Android-Emulation-Testing/code-and-data).

### Code Release

#### Measurement Code

#### Enhancements

We have provided the enhancements in Section 6 of our paper in the [`enhancements`](https://github.com/Android-Emulation-Testing/code-and-data/tree/main/enhancements) folder.

### Data Release

#### Measurement Data

We have provided the a portion of the measurement data (with proper anonymization) of failure events in the [`data`](https://github.com/Android-Emulation-Testing/code-and-data/tree/main/data) folder. As to the full dataset, we are still in discussion with the authority to what extend can it be released.

#### Data Format

The attributes of each failure event are organized as follows:
|  Attribute   | Description  |
|  ----  | ----  |
| error  | The triggered Exception/Signal of the failure. |
| scene  | A brief summary of the failure scene with anonymization. |
| os_version  | The Android version. |
| device_brand  | The device brand. |
| device_model  | The device model. |
| device_type  | The type of the device. Specifically, `physical` denotes a physical device and `virtrualized` denotes a virtrualized device. |
| failure_layer  | The layer in which the failure occurred. Specifically, `java` and `native` denote that the failure occurred in the Java or the native layer, respectively. 