## Mbed OS Known Issues
### About this document

This is the list of known issues for the [5.6.0 release of Mbed OS and related tools](https://os.mbed.com/docs/v5.6/releases/mbed-os-56-releases.html/).

We publish mbed OS as a collection of modules on GitHub. Issues are raised in the specific repositories, and we then track the issues internally. The purpose of this document is to provide a single view of the outstanding key issues that have not been addressed for this release. It is a filtered and reviewed list based on priority and potential effect. Each item summarizes the problem and includes any known workarounds, along with a link to the GitHub issue if applicable. We welcome any comments or proposed solutions.

For more information about an issue, contact us on the [forums](http://os.mbed.org/forums).

### Additional information
For further information regarding this release, please refer to the release notes referenced above.

### Known issues

**Handshake Messages are not fragmented as per MaxFragmentLength Extension Negotiation**

- Description: "Once a maximum fragment length other than 2^14 has been successfully negotiated, the client and server MUST immediately begin fragmenting messages (including handshake messages) to ensure that no fragment larger than the negotiated length is sent. " In Mbed TLS only the application data is fragmented and the handshake messages are not.
- Workaround: Disable MaxFragmentLength Extension Negotiation.
- Reported Issue: https://github.com/ARMmbed/mbedtls/issues/387
- Priority: MAJOR

**IP addresses in the X.509 certificate subjectAltNames**

- Description: Parsing IP addresses in the X.509 certificate subjectAltNames is not supported yet. In certificate chains relying on IP addresses in subjectAltNames a BADCERT_CN_MISMATCH error is returned.
- Workaround: merge branch https://github.com/ARMmbed/mbedtls/tree/iotssl-602-san-ip into your copy of Mbed TLS before building the application. It is still in EXPERIMENTAL stage, use it on your own responsibility!
- Reported Issue: Issue reported by a customer in email.
- Priority: MAJOR

**Mismatch of root CA and issuer of CRL not caught**

- Description: The x509_crt_verifycrl() function ignores the CRL, when the CRL has an issuer different from the subject of root CA certificate.
- Workaround: Make sure that the issuer of the CRL and the root CA certificate's subject are the same before passing them to x509_crt_verifycrl().
- Reported Issue: Reported by a partner.
- Priority: MAJOR

**Mbed TLS causes stack overflow in Mbed OS targets**

- Description: The stack memory usage of some Mbed TLS features is higher than 4 KB, which may cause stack overflow errors when running in constrained embedded environments with mbed OS which are particularly limited in RAM.
- Workaround: The amount of stack required is very dependent on the application, and what features of the library it chooses to use. Obviously more intensive, demanding tasks may not be possible on more limited, constrained devices, so we recommend designing for the limitations of the target device, or choosing a device suitable for your application.
- Reported Issue: https://github.com/ARMmbed/mbed-os-example-tls/issues/14
- Priority: MAJOR

**Commissioner does not retransmit message when it receives retransmission**

- Description: There are two issues with DTLS handshake retransmission. Firstly, the joiner fails to correctly parse received records because it does not correctly handle queued retransmissions received. Secondly, the commissioner may cause a deadlock as it does not retransmit certain records after it receives retransmission as instructed in RFC6347 Section 4.2.4.
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

**Mesh networking applications fails to compile with IAR on non-secure platform**

- Description: If the target have not defined hardware entropy module then Mbed TLS support is disabled on the build time. This leads to compilation warnings on some Nanostack related modules and compilation failure when using IAR toolchain.
- Workaround: There is no available workaround at the moment.
- Reported Issue: https://github.com/ARMmbed/mbed-os-example-mesh-minimal/issues/91
- Priority: Major

**UARTSerial asserts if debug is enabled**

- Description: UARTSerial attempts to claim a mutex from interrupt context. If debug is not enabled, this fails silently, and driver works as intended. If debug is enabled, the system stops in the assert.
- Workaround: Turn off the debug build.
Reported Issue: https://github.com/ARMmbed/mbed-os/issues/4537
Priority: Major

**Link in GettingStarted.html generated by mbed export is incorrect**

- Description: The link generated by mbed export in the file GettingStarted.html is not out of date.
- Workaround: Navigate to the correct document by going to the Handbook and selecting "Third party development tools" in the "Development tools and aids" section.
- Reported Issue: https://github.com/ARMmbed/mbed-os/issues/5149
- Priority: Minor

**Assembling fails for make_armc5 exporter in Windows uppon update of Mbed OS**

- Description: After updating Mbed OS on windows and exporting to make_armc5, the assembler will complain of "Invalid line start" and "Unknown opcode __FPU_PRESENT".
- Workaround: Remove the mbed-os directory, and recreate it from the upstream mbed-os git repo
- Reported Issue: https://github.com/ARMmbed/mbed-os/issues/5145
- Priority: Minor

**Realtek RTL8195AM does not define flash algorithms for uvision**

- Description: No flashing support in uvision for Realtek RTL8195AM
- Workaround: Use drag-n-drop programming
- Reported Issue: https://github.com/ARMmbed/mbed-os/issues/4651
- Priority: Minor

**Daplink bootloader mode might brick NXP device in windows 10**

- Description: Bootloader might flash a target with non-valid data
- Workaround: None
- Reported Issue: https://github.com/mbedmicro/DAPLink/issues/201
- Priority: Major

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
