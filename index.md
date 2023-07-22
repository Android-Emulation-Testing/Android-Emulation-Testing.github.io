![license](https://img.shields.io/badge/Platform-Android-green "Android")
![license](https://img.shields.io/badge/Version-Beta-yellow "Version")
[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0)

## Table of Contents
- [About this Study](#about-this-study)
- [Artifact Release](#artifact-release)
    - [Data Format](#data-format)
- [Failure Discrepancy Report](#failure-discrepancy-report)

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

## Artifact Release

We have released the anonymized failure data associated with our paper in [this github repository](https://github.com/Android-Emulation-Testing/emu-fidelity-ae).

The anonymized failure data are collected from our physical and device farms over a three-month period.
The failure data involves 5,918 physical devices as well as 5,918 virtualized devices running on ARM commodity servers.

### Data Format

The data file is organized in `.csv` format. 
Each row represents a single failure scene, and detailed information (i.e. call stacks, device information) about the scenes is provided, in the format described in the table below.

| Column | Description | Example |
| ------ | ----------- | ------- |
| error | The triggered exception/signal of the failure | java.lang.NullPointerException |
| reason | The descriptive message printed after the error | must not be null |
| stack_frame | The call stack of the failure | [{'file': 'app.java', 'method': 'badMethod()', 'line_number': '10'}] |
| thread_name | The name of the thread at fault | thread-1 |
| failure_time | The unix timestamp at which the failure occurs, in seconds | 1640966505.0 |
| app_id | The id of the failing app. They correspond to Table 1 of our paper. | 1 |
| app_version | The version of the app, denoted by the date they are tested in our device farm. | 2022-01-01 |
| device_brand | The brand of the failing device. For virtualized devices this is the brand of its physical device pair. | samsung |
| device_model | The device model of the failing device. The model for our virtualized devices is 'virt'. | samsung-model-1 |
| android_version | The android version of the device. | 10.0 |

## Failure Discrepancy Report

We have reported the root causes and solutions of the failure discrepancies mentioned in our paper to all the corresponding stakeholders, including phone vendors (e.g., Huawei, Honor, and Meizu) and hardware manufacturers (e.g., MediaTek).
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
| 8     | Google | Graphics resource format inconsistency | [Confirmed & Fixed](https://issuetracker.google.com/issues/262255458) |
