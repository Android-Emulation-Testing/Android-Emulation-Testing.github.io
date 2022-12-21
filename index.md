![license](https://img.shields.io/badge/Platform-Android-green "Android")
![license](https://img.shields.io/badge/Version-Beta-yellow "Version")
![license](https://img.shields.io/badge/Licence-Apache%202.0-blue.svg "Apache")

## Table of Contents
- [About this Study](#about-this-study)
- [Code and Data Release](#code-and-data-release)
  - [Code Release](#code-release)
    - [Failure Scene Capture](#failure-scene-capture)
    - [Enhancements](#enhancements)
  - [Data Release](#data-release)
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

The code and data involved in our study are provided in [this github repository](https://github.com/Android-Emulation-Testing/code-and-data).

### Code Release

#### Failure Scene Capture

We have provided the source code of captureing failure scene mentioned in our paper in the [`capture` folder](https://github.com/Android-Emulation-Testing/code-and-data/tree/main/capture).

#### Enhancements

We have provided the source code of the enhancements mentioned in our paper in the [`enhancements` folder](https://github.com/Android-Emulation-Testing/code-and-data/tree/main/enhancements).

### Data Release

We have provided in part the measurement data (with proper anonymization) in the [`data` folder](https://github.com/Android-Emulation-Testing/code-and-data/tree/main/data). 
We will release the full dataset as soon as we obtain official approval of the relevant authorities.

#### Data Format

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
