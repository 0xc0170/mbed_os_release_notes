## Mbed OS 5.6.0 release

The Arm Mbed OS 5.6.0 release helps to further simplify the internet of things (IoT) and embedded product development with the addition of several new features, such as tickless RTOS scheduler support to enable long periods of low-power sleep and IPv6 support to cellular stack to provide enhanced web connectivity. The release also adds several new drivers and platform APIs, support for IAR Embedded Workbench v8.1 and hardware security enhancements. In addition, this release contains many minor fixes and enhancements and brings support for 93 target development boards. In the release note below, we summarize some of the key updates to Mbed OS as a part of the Mbed OS 5.6.0 release.

One additional change you may have noticed is developer.mbed.org is now [os.mbed.com](https://os.mbed.com). We have updated our URL for consistency across the website. The community should experience no significant changes or issues due to this change because all redirects are in place. 

### Core OS

#### Tickless RTOS Scheduler

Power consumption is one of the most important design requirements for IoT devices. Meeting the power budget is becoming very challenging as the systems today include more sensors, faster responses and more connectivity. Mbed OS introduces the Tickless RTOS Scheduler to help achieve the design of low power systems.

**Support Tickless Operation**: In tickless operation, you don’t have to make a tradeoff between high-frequency timing interval, which consumes more power, and low-frequency timing interval, which results in suboptimal time keeping, because the scheduler schedules the next timer tick in response to the next event rather than a fixed timer tick.

**Integration with Mbed OS**: The Tickless RTOS Scheduler is integrated in the native OS and based on the low power ticker. The Tickless RTOS Scheduler is already integrated [in the Ticker API](https://os.mbed.com/docs/v5.6/reference/ticker.html). The specifications are released to help other boards support the implementation of the low power timer and Tickless scheduler. We are working with Mbed silicon partners to enable support for the Tickless Scheduler on all Mbed Enabled boards.

#### Support for Arm Cortex-M23 and Cortex-M33 devices 

Connected devices are growing at a fast pace, and according to [Gartner](http://www.gartner.com/newsroom/id/3598917), there will be more than 20 billion connected devices by 2020. As the number of IoT devices grows, the devices are becoming an increasingly attractive target for cybercriminals. Security is becoming one the most important product requirements for IoT devices. Arm has announced Arm Cortex-M23 and Cortex-M33 processor architecture, which includes TrustZone for Armv8-M and provides hardware-enforced isolation between trusted and untrusted resources while maintaining the efficient exception handling and determinism that have been the hallmark of all Cortex-M processors. 

Mbed OS 5.6.0 release provides initial support for Arm [Cortex-M23](https://developer.arm.com/products/processors/cortex-m/cortex-m23) and [Cortex-M33](https://developer.arm.com/products/processors/cortex-m/cortex-m33) based devices. This release includes support for RTX and tools for GCC only. This release is an instrumental step in supporting upcoming Arm Cortex-M23 and Cortex-M33 MCUs. You will benefit from support for Arm Cortex-M23 and Cortex-M33 as the new development boards including those processors start to come out. 

#### New drivers and platform APIs 

In the Mbed OS 5.6.0 release, we have also added several new drivers and platform APIs. Following are some of the notable additions.

**CriticalSectionLock Class**: CriticalSectionLock class enables the code to run with interrupts disabled. More information is available in [the API](https://os.mbed.com/docs/v5.6/reference/criticalsectionlock.html).

**DeepSleepLock Class**: DeepSleepLock class enables the code to run with deep sleep locked. More information is available in [the API](https://os.mbed.com/docs/v5.6/reference/deepsleeplock.html).

**Mbed_error**: Mbed_error prevents recursion if error is called again. More information is available in [the API](https://os.mbed.com/docs/v5.6/reference/error.html).

**NonCopyable Class**: NonCopyable class allows the creation of classes whose objects cannot be constructed using a copy constructor or assigned to another. It forces the classes copy constructors to be private. More information is available in [the API](https://os.mbed.com/docs/v5.6/reference/noncopyable.html).

Apart from the features described above, Mbed OS 5.6.0 also includes several new features, improvements in current APIs and HAL specification to ensure cross platform support of all APIs. You can find all the changes on GitHub. 

### Connectivity 

#### Cellular stack now supports IPv6 along with previous IPv4

Cellular connectivity is widely used for connecting IoT devices. It is prominent in mobility, such as smart cars, and devices operating in remote areas, such as oil fields. According to [Ericsson](https://www.ericsson.com/res/docs/2016/ericsson-mobility-report-2016.pdf), 10% of all IoT devices by 2021 will be connected by cellular connectivity.  

Mbed OS already includes the cellular point to point stack with IPv4 connectivity, and in Mbed 5.6.0, we are releasing cellular stack supporting IPv6. IPv6 is being widely adopted because it allows almost unlimited (3.4*10^38) addresses, and IPv4 only allows up to 4.3 billion addresses. More information is available in [the cellular documentation](https://os.mbed.com/docs/v5.6/reference/cellular-api.html). 

### Security 

#### Update to Mbed TLS 2.6.0 

Mbed TLS is an open source, portable, easy to use, readable and flexible SSL library. It enables you to include cryptographic and SSL/TLS capabilities in your embedded products. 

The Mbed OS 5.6.0 release supports the latest release of Mbed TLS 2.6.0. The Mbed TLS 2.6.0 fixes an authentication bypass issue in SSL/TLS. More Mbed security information is available in the [security documentation](https://os.mbed.com/docs/v5.6/reference/security-overview.html). 

### Targets and tools 

Thanks to our partners’ hard work, Mbed OS 5.6 adds eight new target platforms and now supports 93 target platforms. We’ll continue to add targets in our biweekly patch releases as partners work with us on support. 

#### Support for IAR Embedded Workbench for Arm v8.1 

Mbed OS 5.6.0 enables initial support to IAR Embedded Workbench for Arm v8.1, which is the latest IAR compiler to support Arm MCUs. Although the default compiler version for IAR remains 7.8.x, you can also build the codebase using IAR 8.1 (builds without dependencies on archives). The current support for IAR Embedded Workbench for Arm v8.1 is limited only to the Mbed CLI tool, and we plan to migrate to the IAR Embedded Workbench for Arm v8.1 as a default IAR toolchain in Mbed OS release 5.7.0. 

#### Support for Arm Compiler 6 

Mbed OS 5.6.0 adds early support for the latest and most efficient version of the Arm compiler, the Arm Compiler 6. This version is based on the LVVM framework, optimized to best use hardware features. You can read about [the Arm Compiler 6](https://developer.Arm.com/products/software-development-tools/compilers/Arm-compiler). The current support for Arm Compiler 6 is limited only to the Mbed CLI tool, and we plan to migrate to Arm Compiler 6 as a default in Mbed OS release 5.7.0. 

### Testing 
Mbed OS is designed to significantly reduce cost and time for embedded software development by providing production quality code and toolset. We are committed to delivering high-quality code working across all supported boards and platforms. To ensure that all the features of the code meet our quality control requirements, we have built an automated testing environment and processes that perform rigorous testing on the code. Following are some of the highlights of our testing framework. 

#### Continuous integration framework: 
The continuous integration framework is designed to make sure that every new feature and change in Mbed OS is tested to ensure:

- For every new feature, we create tests that we then deliver to our partners. For every board to be Mbed Enabled, we need our partners to successfully conduct these tests. 
- Partners test the changes on their board before submitting a Pull Request (PR) on GitHub. 
- Once the PR is submitted, then the gatekeepers manually review the code to make sure it meets all the coding guidelines and code standards. 
- Once approved by gatekeepers, the code goes through the automated test setup where code is added to Mbed OS for testing and examples built across all the platforms, such as IAR, ARM and GCC. 
- During the testing phase, we select the combination of boards and devices that support a variety of peripherals, MCU cores and features to select maximum coverage. 
- To make sure that the Mbed OS code is compatible with all the IDEs, we test that the code exports properly to all the compilers. 
- We merge the PR only if the all the above is successful. 

Following are the summary results for testing conducted for Mbed OS 5.6.0.
- Total test time is 5,770 hours on actual development boards. 
- We have added 94 new test cases since the Mbed OS 5.5.0 release to test new and existing features on Mbed OS. The number of total test cases is 312. 
- We performed 361,440 example builds since the Mbed OS 5.5.0 release. 
- The total number of binaries built is 12,826,080 since the Mbed OS 5.5.0 release.

We plan to share more details about testing processes, such as our out of box testing coverage and system testing, in upcoming release blogs. 

### Known issues

We publish Mbed OS as a collection of modules on GitHub. Issues are raised in the specific repositories and then tracked internally. The purpose of this document is to provide a single view of the outstanding key issues that have not been addressed for this release. It is a filtered and reviewed list based on priority and potential effect. Each item summarizes the problem and includes any known workarounds, along with a link to the GitHub issue (if applicable). We welcome any comments or proposed solutions.

For more information about an issue, contact us on the [forums](http://os.mbed.com/forum).

#### Handshake Messages are not fragmented as per MaxFragmentLength Extension Negotiation
* **Description**: "Once a maximum fragment length other than 2^14 has been successfully negotiated, the client and server MUST immediately begin fragmenting messages (including handshake messages) to ensure that no fragment larger than the negotiated length is sent. " In Mbed TLS, only the application data is fragmented and the handshake messages are not.
* **Workaround**: Disable MaxFragmentLength Extension Negotiation.
* **Reported Issue**: https://github.com/ARMmbed/mbedtls/issues/387
* **Priority**: MAJOR

#### IP addresses in the X.509 certificate subjectAltNames
* **Description**: Parsing IP addresses in the X.509 certificate subjectAltNames is not supported yet. In certificate chains relying on IP addresses in subjectAltNames a `BADCERT_CN_MISMATCH` error is returned.
* **Workaround**: Merge branch https://github.com/ARMmbed/mbedtls/tree/iotssl-602-san-ip into your copy of Mbed TLS before building the application. It is still in EXPERIMENTAL stage; use it at your own responsibility!
* **Reported Issue**: Issue reported by a customer in email.
* **Priority**: MAJOR

#### Mismatch of root CA and issuer of CRL not caught 
* **Description**: The `x509_crt_verifycrl()` function ignores the CRL when the CRL has an issuer different from the subject of root CA certificate.
* **Workaround**: Make sure that the issuer of the CRL and the root CA certificate's subject are the same before passing them to `x509_crt_verifycrl()`.
* **Reported Issue**: Reported by a partner.
* **Priority**: MAJOR

#### Mbed TLS causes stack overflow in Mbed OS targets
* **Description**: The stack memory usage of some Mbed TLS features is higher than 4 KB, which may cause stack overflow errors when running with Mbed OS in constrained embedded environments, which are particularly limited in RAM.
* **Workaround**: The amount of stack required depends on the application and what features of the library it chooses to use. More intensive, demanding tasks may not be possible on more limited, constrained devices, so we recommend designing for the limitations of the target device or choosing a device suitable for your application.
* **Reported Issue**: https://github.com/ARMmbed/mbed-os-example-tls/issues/14
* **Priority**: MAJOR

#### Commissioner does not retransmit message when it receives retransmission
* **Description**: There are two issues with DTLS handshake retransmission. First, the joiner fails to correctly parse received records because it does not correctly handle queued retransmissions received. Second, the commissioner may cause a deadlock as it does not retransmit certain records after it receives retransmission as instructed in RFC6347 Section 4.2.4. 
* **Workaround**: There is no known workaround. 
* **Reported Issue**: https://github.com/openthread/openthread/pull/1207 
* **Priority**: MAJOR

#### Self Test Failure with Some Hardware Accelerators 
* **Description**: Most HW acceleration engines (if not all) require the parameters to be from contiguous memory. All the self tests use test vectors that are defined in the `.bss` section, which means these are not contiguous. This causes the self test to possibly fail, when implementing HW accelerated engines. 
* **Workaround**: There are no known workarounds 
* **Reported Issue**: Reported by the development team. 
* **Priority**: MAJOR

#### uVisor does not support nested interrupts

* **Description**: When running an application with uVisor enabled, nested interrupts are not supported.
* **Workaround**: There is no available workaround at the moment.
* **Reported Issue**: https://github.com/ARMmbed/uvisor/issues/345
* **Priority**: Major

#### On ARMv7-M targets supporting uVisor, the RTOS runs with the same privilege of uVisor

* **Description**: The current architecture of uVisor and of RTX require the RTOS to run with the same privilege of uVisor. As such, the RTOS is considered as trusted.
* **Workaround**: There is no available workaround at the moment.
* **Reported Issue**: https://github.com/ARMmbed/uvisor/issues/235
* **Priority**: Major

#### Mesh networking applications fail to compile with IAR on non-secure platform

* **Description**: If the target has no defined hardware entropy module, then Mbed TLS support is disabled on the build time. This leads to compilation warnings on some Nanostack related modules and compilation failure when using IAR toolchain.
* **Workaround**: There is no available workaround at the moment.
* **Reported Issue**: https://github.com/ARMmbed/mbed-os-example-mesh-minimal/issues/91
* **Priority**: Major

#### UARTSerial asserts if debug is enabled

* **Description**: UARTSerial attempts to claim a mutex from interrupt context. If debug is not enabled, this fails silently, and the driver works as intended. If debug is enabled, the system stops in the assert.
* **Workaround**: Turn off the debug build.
* **Reported Issue**: https://github.com/ARMmbed/mbed-os/issues/4537  
* **Priority**: Major

#### Link in GettingStarted.html generated by `mbed export` is incorrect

* **Description**: The link generated by `mbed export` in the file GettingStarted.html is out of date.
* **Workaround**: Navigate to the correct document by going to the Handbook and selecting "Third party development tools" in the "Development tools and aids" section.
* **Reported Issue**: https://github.com/ARMmbed/mbed-os/issues/5149
* **Priority**: Minor

#### Assembling fails for make_armc5 exporter in Windows upon update of Mbed OS

* **Description**: After updating Mbed OS on Windows and exporting to `make_armc5`, the assembler will complain of `Invalid line start` and `Unknown opcode __FPU_PRESENT`.
* **Workaround**: Remove the `mbed-os` directory, and recreate it from the upstream `mbed-os` Git repo.
* **Reported Issue**: https://github.com/ARMmbed/mbed-os/issues/5145
* **Priority**: Minor

#### Realtek RTL8195AM does not define flash algorithms for uvision

* **Description**: No flashing support in uvision for Realtek RTL8195AM.
* **Workaround**: Use drag-and-drop programming.
* **Reported Issue**: https://github.com/ARMmbed/mbed-os/issues/4651
* **Priority**: Minor

#### Ublox EVK ODIN W2 serial baud rate mismatch 

* **Description**: The default serial port produces incorrect output.
* **Workaround**: None.
* **Reported Issue**: https://github.com/ARMmbed/mbed-os-example-wifi/issues/58
* **Priority**: Major

#### The default address (ff03::1) cannot work for multicast

* **Description**: The default address works with Thread but not 6LoWPAN.
* **Workaround**: None.
* **Reported Issue**: https://github.com/ARMmbed/mbed-os-example-mesh-minimal/issues/130
* **Priority**: Major

### Ports for upcoming targets

[4631](https://github.com/ARMmbed/mbed-os/pull/4631) Add new target NUMAKER_PFM_NANO130

### Fixes and changes

This is the full list of changes available in this release.

[4518](https://github.com/ARMmbed/mbed-os/pull/4518) Add new target in mbedtls importer Makefile for mbedtls tests

[4644](https://github.com/ARMmbed/mbed-os/pull/4644) Ticker: add fire interrupt now function

[4814](https://github.com/ARMmbed/mbed-os/pull/4814) Merge lwip 2.0.2 stable

[4809](https://github.com/ARMmbed/mbed-os/pull/4809) STM32: Align HAL & US tickers

[4517](https://github.com/ARMmbed/mbed-os/pull/4517) Add cpp API for CMSIS OS 2 EventFlags

[4908](https://github.com/ARMmbed/mbed-os/pull/4908) fs: Add FileSystem::reformat

[4920](https://github.com/ARMmbed/mbed-os/pull/4920) Modify LED error sequence to be more recognisable

[4960](https://github.com/ARMmbed/mbed-os/pull/4960) Nanostack update for mbed-os-5.6

[5003](https://github.com/ARMmbed/mbed-os/pull/5003) Move Cortex specific RTX behind TARGET_CORTEX

[4962](https://github.com/ARMmbed/mbed-os/pull/4962) platform: add CriticalSectionLock

[4843](https://github.com/ARMmbed/mbed-os/pull/4843) fatfs: Add lower bound to block sizes

[4911](https://github.com/ARMmbed/mbed-os/pull/4911) Support cellular IPv4v6 dual stack in LWIP

[4907](https://github.com/ARMmbed/mbed-os/pull/4907) Update uVisor to v0.30.0

[4580](https://github.com/ARMmbed/mbed-os/pull/4580) Use EventFlags instead of Semaphores

[4406](https://github.com/ARMmbed/mbed-os/pull/4406) mbed_events.h: Add ability to request a shared event queue

[5037](https://github.com/ARMmbed/mbed-os/pull/5037) Revert "Adjusting Stack size Allocation (IAR, LPC176x)"

[5030](https://github.com/ARMmbed/mbed-os/pull/5030) Export uVision linker flags so that bootloader projects build correctly

[4912](https://github.com/ARMmbed/mbed-os/pull/4912) Add sleep manager API

[4916](https://github.com/ARMmbed/mbed-os/pull/4916) Add mcuxpresso exporter

[5055](https://github.com/ARMmbed/mbed-os/pull/5055) Travis: fix the latest breakage - use group:

[4991](https://github.com/ARMmbed/mbed-os/pull/4991) Add tickless to some mbed-os devices

[5012](https://github.com/ARMmbed/mbed-os/pull/5012) STM32_us_ticker_16b: keep code to cope with past event

[4938](https://github.com/ARMmbed/mbed-os/pull/4938) Update IAR to version 8

[5063](https://github.com/ARMmbed/mbed-os/pull/5063) Fixing lp ticker and sleep manager tests

[4875](https://github.com/ARMmbed/mbed-os/pull/4875) Initial support for Cortex M-23/M-33 devices.

[4987](https://github.com/ARMmbed/mbed-os/pull/4987) Update mbed TLS to version 2.6.0

[5073](https://github.com/ARMmbed/mbed-os/pull/5073) use gcc assembly for arm 6

[4949](https://github.com/ARMmbed/mbed-os/pull/4949) NEW TOOLCHAIN: Add the ARMC6 Compiler

[5093](https://github.com/ARMmbed/mbed-os/pull/5093) Disable response files on export

[5090](https://github.com/ARMmbed/mbed-os/pull/5090) Correct long call macros for ARMC6

[5111](https://github.com/ARMmbed/mbed-os/pull/5111) Emit dependency information with ARMC6

[5069](https://github.com/ARMmbed/mbed-os/pull/5069) Changed error print to assert

[5107](https://github.com/ARMmbed/mbed-os/pull/5107) mbed_rtx_idle: uVisor: Don't attempt to sleep

[5122](https://github.com/ARMmbed/mbed-os/pull/5122) update server name to os.mbed.com

[5103](https://github.com/ARMmbed/mbed-os/pull/5103) Parse libraries with memap-arm

[5116](https://github.com/ARMmbed/mbed-os/pull/5116) Separate string literal from macro

[5132](https://github.com/ARMmbed/mbed-os/pull/5132) Fix MBED_ VERSION

[5091](https://github.com/ARMmbed/mbed-os/pull/5091) Correct booting on Nordic devices with ARMC6

[5094](https://github.com/ARMmbed/mbed-os/pull/5094) ARMC6 support for Cortex-M23

[5044](https://github.com/ARMmbed/mbed-os/pull/5044) Realtek_RTL8195AM fix for debug profile

[5125](https://github.com/ARMmbed/mbed-os/pull/5125) Refactor memap for speed

The upgrade should be generally transparent to developers using the Mbed OS RTOS APIs, but please report in the [forums](https://os.mbed.com/forum/bugs-suggestions/) or contact us at [support@mbed.com](mailto:support@mbed.com) if you have any issues in this area. 

### Using the release 

You can fetch the latest version of the Mbed OS 5.6 release from the `mbed-os` GitHub repository using [this branch](https://github.com/ARMmbed/mbed-os/releases/tag/mbed-os-5.6.0). 
