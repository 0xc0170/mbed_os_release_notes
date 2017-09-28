## Mbed OS 5.6.0 release

### About this release

The Arm Mbed OS 5.6.0 release helps to further simplify the internet of things (IoT) and embedded product development with the addition of several new features, such as tickless RTOS scheduler support to enable long periods of low-power sleep and IPv6 support to cellular stack to provide enhanced web connectivity. The release also adds several new drivers and platform APIs, support for IAR Embedded Workbench v8.1 and hardware security enhancements. In addition, this release contains many minor fixes and enhancements and brings support for 93 target development boards. In the release note below, we summarize some of the key updates to Mbed OS as a part of the Mbed OS 5.6.0 release.

One additional change you may have noticed is developer.mbed.org is now [os.mbed.com](https://os.mbed.com). We have updated our URL for consistency across the website. The community should experience no significant changes or issues due to this change because all redirects are in place. 

### Core OS

#### Tickless RTOS Scheduler

Power consumption is one of the most important design requirements for IoT devices. Meeting the power budget is becoming very challenging as the systems today include more sensors, faster responses and more connectivity. Mbed OS introduces the Tickless RTOS Scheduler to help achieve the design of low power systems.

**Support Tickless Operation**: In tickless operation, you don’t have to make a tradeoff between high-frequency timing interval, which consumes more power, and low-frequency timing interval, which results in suboptimal time keeping, because the scheduler schedules the next timer tick in response to the next event rather than a fixed timer tick.

**Integration with Mbed OS**: The Tickless RTOS Scheduler is integrated in the native OS and based on the low power ticker. The Tickless RTOS Scheduler is already integrated [in the Ticker API](https://os.mbed.com/docs/v5.6/reference/ticker.html). The specifications are released to help other boards support the implementation of the low power timer and Tickless scheduler. We are working with Mbed silicon partners to enable support for the Tickless Scheduler on all Mbed Enabled boards.

#### Support for Arm Cortex-M23 and Cortex-M33 Devices 

Connected devices are growing at a fast pace, and according to [Gartner](http://www.gartner.com/newsroom/id/3598917), there will be more than 20 billion connected devices by 2020. As the number of IoT devices grows, the devices are becoming an increasingly attractive target for cybercriminals. Security is becoming one the most important product requirements for IoT devices. Arm has announced Arm Cortex-M23 and Cortex-M33 processor architecture, which includes TrustZone for Armv8-M and provides hardware-enforced isolation between trusted and untrusted resources while maintaining the efficient exception handling and determinism that have been the hallmark of all Cortex-M processors. 

Mbed OS 5.6.0 release provides initial support for Arm [Cortex-M23](https://developer.arm.com/products/processors/cortex-m/cortex-m23) and [Cortex-M33](https://developer.arm.com/products/processors/cortex-m/cortex-m33) based devices. This release includes support for RTX and tools for GCC only. This release is an instrumental step in supporting upcoming Arm Cortex-M23 and Cortex-M33 MCUs. You will benefit from support for Arm Cortex-M23 and Cortex-M33 as the new development boards including those processors start to come out. 

#### New Drivers and Platform APIs 

In the Mbed OS 5.6.0 release, we have also added several new drivers and platform APIs. Following are some of the notable additions.

**CriticalSectionLock Class**: CriticalSectionLock class enables the code to run with interrupts disabled. More information is available in [the API](https://os.mbed.com/docs/v5.6/reference/criticalsectionlock.html).

**DeepSleepLock Class**: DeepSleepLock class enables the code to run with deep sleep locked. More information is available in [the API](https://os.mbed.com/docs/v5.6/reference/deepsleeplock.html).

**Mbed_error**: Mbed_error prevents recursion if error is called again. More information is available in [the API](https://os.mbed.com/docs/reference/error.html).

**NonCopyable Class**: NonCopyable class allows the creation of classes whose objects cannot be constructed using a copy constructor or assigned to another. It forces the classes copy constructors to be private. More information is available in [the API](https://os.mbed.com/docs/v5.6/reference/noncopyable.html).

Apart from the features described above, Mbed OS 5.6.0 also includes several new features, improvements in current APIs and HAL specification to ensure cross platform support of all APIs. You can find all the changes on GitHub. 

### Connectivity 

#### Cellular stack now supports IPv6 along with previous IPv4

Cellular connectivity is widely used for connecting IoT devices. It is prominent in mobility, such as smart cars, and devices operating in remote areas, such as oil fields. According to [Ericsson](https://www.ericsson.com/res/docs/2016/ericsson-mobility-report-2016.pdf), 10% of all IoT devices by 2021 will be connected by cellular connectivity.  

Mbed OS already includes the cellular point to point stack with IPv4 connectivity, and in Mbed 5.6.0, we are releasing cellular stack supporting IPv6. IPv6 is being widely adopted because it allows almost unlimited (3.4×1038) addresses, and IPv4 only allows up to 4.3 billion addresses. More information is available in [the cellular documentation](https://os.mbed.com/docs/v5.6/reference/cellular-api.html). 

### Security 

#### Update to Mbed TLS 2.6.0 

Mbed TLS is an open source, portable, easy to use, readable and flexible SSL library. It enables you to include cryptographic and SSL/TLS capabilities in your embedded products. 

The Mbed OS 5.6.0 release supports the latest release of Mbed TLS 2.6.0. The Mbed TLS 2.6.0 fixes an authentication bypass issue in SSL/TLS. More Mbed security information is available in the [security documentation](https://os.mbed.com/docs/v5.6/reference/security-overview.html). 

### Targets and Tools 

Thanks to our partners’ hard work, Mbed OS 5.6 adds eight new target platforms and now supports 93 target platforms. We’ll continue to add targets in our biweekly patch releases as partners work with us on support. 

#### Support for IAR Embedded Workbench for Arm v8.1 

Mbed OS 5.6.0 enables initial support to IAR Embedded Workbench for Arm v8.1, which is the latest IAR compiler to support Arm MCUs. Although the default compiler version for IAR remains 7.8.x, you can also build the codebase using IAR 8.1 (builds without dependencies on archives). The current support for IAR Embedded Workbench for Arm v8.1 is limited only to the Mbed CLI tool, and we plan to migrate to the IAR Embedded Workbench for Arm v8.1 as a default IAR toolchain in Mbed OS release 5.7.0. 

#### Support for Arm Compiler 6 

Mbed OS 5.6.0 adds early support for the latest and most efficient version of the Arm compiler, the Arm Compiler 6. This version is based on the LVVM framework, optimized to best use hardware features. You can read about [the Arm Compiler 6](https://developer.Arm.com/products/software-development-tools/compilers/Arm-compiler). The current support for Arm Compiler 6 is limited only to the Mbed CLI tool, and we plan to migrate to Arm Compiler 6 as a default in Mbed OS release 5.7.0. 

### Fixes and changes

The release includes many general enhancements and fixes and upstreams those that have been maintained within the Mbed OS codebase itself. Please visit https://os.mbed.com/releases/ for the full list of changes and known issues. 

The upgrade should be generally transparent to developers using the Mbed OS RTOS APIs, but please report in the [forums](https://os.mbed.com/forum/bugs-suggestions/) or contact us at [support@mbed.com](mailto:support@mbed.com) if you have any issues in this area. 

### Testing 
Mbed OS is designed to significantly reduce cost and time for embedded software development by providing production quality code and toolset. We are committed to delivering high-quality code working across all supported boards and platforms. To ensure that all the features of the code meet our quality control requirements, we have built an automated testing environment and processes that perform rigorous testing on the code. Following are some of the highlights of our testing framework. 

#### Continuous Integration Framework: 
The continuous integration framework is designed to make sure that every new feature and change in Mbed OS is tested to ensure:

- For every new feature, we create tests that we then deliver to our partners. For every board to be Mbed Enabled, we need our partners to successfully conduct these tests. 
- Partners test the changes on their board before submitting a Pull Request (PR) on GitHub. 
- Once the PR is submitted, then the gatekeepers manually review the code to make sure it meets all the coding guidelines and code standards. 
- Once approved by gatekeepers, the code goes through the automated test setup where code is added to Mbed OS for testing and examples built across all the platforms, such as IAR, ARM and GCC. 
- During the testing phase, we select the combination of boards and devices that support a variety of peripherals, MCU cores and features to select maximum coverage. 
- To make sure that the Mbed OS code is compatible with all the IDEs, we test that the code exports properly to all the compilers. 
- We merge the PR only if the all the above is successful. 

This is the summary of test results conducted for Mbed OS 5.6.0:

- Total test time is 5,770 hours on actual development boards. 
- We have added 94 new test cases since the Mbed OS 5.5.0 release to test new and existing features on Mbed OS. The number of total test cases is 312. 
- We performed 361,440 example builds since the Mbed OS 5.5.0 release. 
- The total number of binaries built is 12,826,080 since the Mbed OS 5.5.0 release.

We plan to share more details about testing processes, such as our out of box testing coverage and system testing, in upcoming release blogs. 

### Using the release 

You can fetch the latest version of the Mbed OS 5.6 release from the mbed-os GitHub repository using [this branch](https://github.com/ARMmbed/mbed-os/releases/tag/mbed-os-5.6.0). 
