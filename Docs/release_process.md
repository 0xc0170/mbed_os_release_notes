## How We Release Arm Mbed OS

The three types of Arm Mbed OS releases are major, feature and patch.

Any release can break binary compatibility.

### Major release

Major releases happen infrequently and indicate a possible change in the structure of the OS. In major releases, the first number after "Mbed OS" changes. For example, moving to Arm Mbed OS 5.0 was a major release. 

They can include:

- incompatible functionality changes (including redesign, removal or new additions)
- removing deprecated functionality

### Feature release

Feature releases occur once a quarter. As their name suggests, feature releases introduce new features to the code base. Unlike major releases, feature releases are backward compatible (source compatible). The second digit in the release number indicates the feature release. For example, Mbed OS 5.1.0 indicates major version 5, feature version 1. 

They can include:

- new Mbed OS features
- new functionality (adding functions, methods, classes)
- larger refactors
- it can deprecate functionality (there should be a new alternative functionality provided)
- configuration changes

#### Patch release

Patch releases occur every two weeks. They are also backward compatible (source compatible). The last digit in the release number indicates the patch release. In Mbed OS 5.2.3, `3` shows the patch release is the third release in Mbed 5.2.

They can include:

- bug fixes
- improvements to existing functionality (targets driver updates, implementation specific improvements that do no change code flow or behavior)
- new target support
- new tests

### The release process

Every release goes through a rigorous review and testing process. We stage changes to the `release-candidate` branch in the `mbed-os` repository. 

Two weeks before each feature release, we implement a code freeze on the master branch while we produce the new release branch. Once the new branch is created, master is once again available. The release branch then goes into the release testing phase, in which we apply <a href="/docs/v5.7/tools/testing.html" target="_blank">our testing tools</a>. These tests include nightly runs through our continuous integration (CI) processes, as well as out-of-box QA. We also put our examples through this testing process. We apply no new code, except for critical bug fixes found during this period, to the release branch.

For patch releases, code freeze occurs the Thursday before the release. Patch releases also go through exporter tests and nightly CI tests.

After all tests return no errors, we release the latest updates. You can find the most recent release in the `mbed-os` repository with the `latest` tag. A release note accompanies each release. The release notes for major and feature releases are longer and give an overview of the new features. The release notes for the patch releases include only a list of changes and known issues, if applicable. You can find our release notes on <a href="https://os.mbed.com/releases/" target="_blank">the releases page</a> and on <a href="https://os.mbed.com/blog/" target="_blank">the blog</a>.
