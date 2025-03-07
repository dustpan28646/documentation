---
id: install-with-bazel
title: Installing Prysm from source with Bazel
sidebar_label: Building from source
---

Prysm can be installed on GNU/Linux, MacOS, and Arm64 using our build tool, [Bazel](https://bazel.build). This page includes instructions for performing this method.

:::tip Pro-Tip
**NOTICE:** The Prysm installation script is the easiest and most efficient way of installing the latest binaries. Instructions for using it can be found [here](/docs/install/linux).
:::

**Have questions?** Stop by the [#documentation](https://discord.gg/QQZMCgU) channel on Discord and let us know.

## System requirements

### Minimum specifications

These specifications must be met in order to successfully run the Prysm client.

* Operating System: 64-bit GNU/Linux, MacOS
* Processor: Intel Core i5–760 or AMD FX-8100 or better
* Memory: 8GB RAM
* Storage: 20GB available space SSD
* Internet: Broadband connection

### Recommended specifications

These hardware specifications are recommended, but not required to run the Prysm client.

* Processor: Intel Core i7–4770 or AMD FX-8310 or better
* Memory: 16GB RAM
* Storage: 100GB available space SSD

## Dependencies

* A modern UNIX operating system
* The latest release of [Bazel](https://docs.bazel.build/versions/master/install.html) installed
* The `cmake` package installed
* The `git` package installed
* `libssl-dev` installed
* `libgmp-dev` installed
* `libtinfo5` installed

## Why Bazel?

Instead of using the `Go` tool to build Prysm, our team relies on the [Bazel](https://bazel.build) build system used by major companies to manage monorepositories. Bazel provides reproducible builds and a sandboxed environment that ensures everyone building Prysm has the same experience and can build our entire project from a single command. For more detailed rationale on why Bazel, how it works in Prysm, and all important information about how exactly building from source works, read our rationale [here](/docs/reading/bazel)

## Installing Prysm

1. Open a terminal window. Ensure you are running the most recent version of Bazel by issuing the command:

```text
bazel version
```

2. Clone Prysm's [main repository](https://github.com/prysmaticlabs/prysm), make sure you switch to the latest version (the latest version number can be found from the [releases page](https://github.com/prysmaticlabs/prysm/releases)), and enter the directory:

```text
git clone https://github.com/prysmaticlabs/prysm
git checkout <version>
cd prysm
```

3. Build both the beacon chain node and the validator client:

```text
bazel build //beacon-chain:beacon-chain --config=release
bazel build //validator:validator --config=release
```

Bazel will automatically pull and install any dependencies as well, including Go and necessary compilers. Now that your installation is done, you can then read [joining eth2](/docs/mainnet/joining-eth2).
