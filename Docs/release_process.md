## How We Release Arm Mbed OS

The three types of Arm Mbed OS releases are major releases, feature releases and patch releases. Major releases happen infrequently and indicate a change in the structure of the OS. In major releases, the first number after "Mbed OS" changes. For example, moving to Arm Mbed OS 5.0 was a major release. 

Feature releases occur about once a quarter. As their name suggests, feature releases introduce new features to the code base. Unlike major releases, feature releases are backward compatible. The second digit in the release number indicates the feature release. For example, Mbed OS 5.1.0 indicates major version 5, feature version 1. 

Patch releases occur about once every two weeks. They include bug fixes and additional target support. They are also backward compatible. The last digit in the release number indicates the patch release. In Mbed OS 5.2.3, `3` shows the patch release is the third release in Mbed 5.2.

### The release process

Every release goes through a rigorous review and testing process. We stage changes to the `release-candidate` branch in the `mbed-os` repository. Two weeks before each release, we implement a code freeze. No new code can go into the release branch after that time. Any new patches must go into a later release. During code freeze, we apply [our testing tools](testing.md) to the release branch. These tests include nightly runs through our continuous integration (CI) processes, as well as out-of-box QA. We also put our examples through this testing process.

After all tests return no errors, we release the latest updates. You can find the most recent release in the `mbed-os` repository with the `latest` tag. A release note accompanies each release. The release notes for major and feature releases are longer and give an overview of the new features. The release notes for the patch releases include only a list of changes and known issues, if applicable. You can find our release notes here and on [our blog](https://developer.mbed.org/blog/). 
