### Mbed OS Known Issues
#### About this document

This is the list of known issues for the [5.6.0 release of Mbed OS and related tools](https://os.mbed.com/docs/v5.6/releases/mbed-os-56-releases.html/).

We publish Mbed OS as a collection of modules on GitHub. Issues are raised in the specific repositories and then tracked internally. The purpose of this document is to provide a single view of the outstanding key issues that have not been addressed for this release. It is a filtered and reviewed list based on priority and potential effect. Each item summarizes the problem and includes any known workarounds, along with a link to the GitHub issue if applicable. We welcome any comments or proposed solutions.

For more information about an issue, contact us on the [forums](http://os.mbed.org/forums).

#### Additional information
For further information regarding this release, please refer to the release notes referenced above.

#### Known issues

**Handshake Messages are not fragmented as per MaxFragmentLength Extension Negotiation**

- Description: "Once a maximum fragment length other than 2^14 has been successfully negotiated, the client and server MUST immediately begin fragmenting messages (including handshake messages) to ensure that no fragment larger than the negotiated length is sent. " In Mbed TLS only the application data is fragmented and the handshake messages are not.
- Workaround: Disable MaxFragmentLength Extension Negotiation.
- Reported Issue: https://github.com/ARMmbed/mbedtls/issues/387
- Priority: MAJOR

**IP addresses in the X.509 certificate subjectAltNames**

- Description: Parsing IP addresses in the X.509 certificate subjectAltNames is not supported yet. In certificate chains relying on IP addresses in subjectAltNames a BADCERT_CN_MISMATCH error is returned.
- Workaround: Merge branch https://github.com/ARMmbed/mbedtls/tree/iotssl-602-san-ip into your copy of Mbed TLS before building the application. It is still in EXPERIMENTAL stage; use it at your own responsibility!
- Reported Issue: Issue reported by a customer in email.
- Priority: MAJOR

**Mismatch of root CA and issuer of CRL not caught**

- Description: The `x509_crt_verifycrl()` function ignores the CRL, when the CRL has an issuer different from the subject of root CA certificate.
- Workaround: Make sure that the issuer of the CRL and the root CA certificate's subject are the same before passing them to `x509_crt_verifycrl()`.
- Reported Issue: Reported by a partner.
- Priority: MAJOR

**Mbed TLS causes stack overflow in Mbed OS targets**

- Description: The stack memory usage of some Mbed TLS features is higher than 4 KB, which may cause stack overflow errors when running with Mbed OS in constrained embedded environments, which are particularly limited in RAM.
- Workaround: The amount of stack required depends on the application, and what features of the library it chooses to use. More intensive, demanding tasks may not be possible on more limited, constrained devices, so we recommend designing for the limitations of the target device, or choosing a device suitable for your application.
- Reported Issue: https://github.com/ARMmbed/mbed-os-example-tls/issues/14
- Priority: MAJOR

**Commissioner does not retransmit message when it receives retransmission**

- Description: There are two issues with DTLS handshake retransmission. First, the joiner fails to correctly parse received records because it does not correctly handle queued retransmissions received. Second, the commissioner may cause a deadlock as it does not retransmit certain records after it receives retransmission as instructed in RFC6347 Section 4.2.4.
- Workaround: There is no known workaround.
- Reported Issue: https://github.com/openthread/openthread/pull/1207
- Priority: MAJOR

**Self Test Failure with Some Hardware Accelerators**

- Description: Most HW acceleration engines (if not all) require the parameters to be from contiguous memory. All the self tests use test vectors that are defined in the .bss section, which means these are not contiguous. This causes the self test to possibly fail, when implementing HW accelerted engines.
- Workaround: There are no known workarounds
- Reported Issue: Reported by the development team.
- Priority: MAJOR

**uVisor does not support nested interrupts**

- Description: When running an application with uVisor enabled, nested interrupts are not supported.
- Workaround: There is no available workaround at the moment.
- Reported Issue: https://github.com/ARMmbed/uvisor/issues/345
- Priority: Major

**On ARMv7-M targets supporting uVisor, the RTOS runs with the same privilege of uVisor**

- Description: The current architecture of uVisor and of RTX require the RTOS to run with the same privilege of uVisor. As such, the RTOS is considered as trusted.
- Workaround: There is no available workaround at the moment.
- Reported Issue: https://github.com/ARMmbed/uvisor/issues/235
- Priority: Major

**Mesh networking applications fail to compile with IAR on non-secure platform**

- Description: If the target has no defined hardware entropy module then Mbed TLS support is disabled on the build time. This leads to compilation warnings on some Nanostack related modules and compilation failure when using IAR toolchain.
- Workaround: There is no available workaround at the moment.
- Reported Issue: https://github.com/ARMmbed/mbed-os-example-mesh-minimal/issues/91
- Priority: Major

**UARTSerial asserts if debug is enabled**

- Description: UARTSerial attempts to claim a mutex from interrupt context. If debug is not enabled, this fails silently, and driver works as intended. If debug is enabled, the system stops in the assert.
- Workaround: Turn off the debug build.
Reported Issue: https://github.com/ARMmbed/mbed-os/issues/4537
Priority: Major

**Link in GettingStarted.html generated by mbed export is incorrect**

- Description: The link generated by `mbed export` in the file GettingStarted.html is out of date.
- Workaround: Navigate to the correct document by going to the Handbook and selecting "Third party development tools" in the "Development tools and aids" section.
- Reported Issue: https://github.com/ARMmbed/mbed-os/issues/5149
- Priority: Minor

**Assembling fails for make_armc5 exporter in Windows uppon update of Mbed OS**

- Description: After updating Mbed OS on Windows and exporting to `make_armc5`, the assembler will complain of `Invalid line start` and `Unknown opcode __FPU_PRESENT`.
- Workaround: Remove the `mbed-os` directory, and recreate it from the upstream `mbed-os` Git repo
- Reported Issue: https://github.com/ARMmbed/mbed-os/issues/5145
- Priority: Minor

**Realtek RTL8195AM does not define flash algorithms for uvision**

- Description: No flashing support in uvision for Realtek RTL8195AM
- Workaround: Use drag-n-drop programming
- Reported Issue: https://github.com/ARMmbed/mbed-os/issues/4651
- Priority: Minor

**Ublox EVK ODIN W2 serial baud rate mismatch**

- Description: The default serial port produces incorrect output
- Workaround: None
- Reported Issue: https://github.com/ARMmbed/mbed-os-example-wifi/issues/58
- Priority: Major

**The default address (ff03::1) cannot work for multicast**

- Description: The default address works with Thread but not 6LoWPAN
- Workaround: None
- Reported Issue: https://github.com/ARMmbed/mbed-os-example-mesh-minimal/issues/130
- Priority: Major

### Ports for Upcoming Targets

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
