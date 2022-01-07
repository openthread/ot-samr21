# OpenThread on SAMR21 Example

This repo contains example platform drivers for the [Microchip ATSAMR21G18A][samr21] based on [SAM R21 Xplained Pro Evaluation Kit][samr21_xplained_pro].

[samr21]: http://www.microchip.com/wwwproducts/en/ATSAMR21G18A
[samr21_xplained_pro]: https://www.microchip.com/DevelopmentTools/ProductDetails/ATSAMR21-XPRO

The example platform drivers are intended to present the minimal code necessary to support OpenThread. See the "Run the example with SAMR21 boards" section below for an example using basic OpenThread capabilities.

## Toolchain

Download and install the [GNU toolchain for ARM Cortex-M][gnu-toolchain].

[gnu-toolchain]: https://developer.arm.com/tools-and-software/open-source-software/developer-tools/gnu-toolchain/gnu-rm

In a Bash terminal, follow these instructions to install the GNU toolchain and other dependencies.

```bash
$ cd <path-to-ot-samr21>
$ ./script/bootstrap
```

## Building

1. Download [Advanced Software Framework (ASF)][asf].

[asf]: https://www.microchip.com/mplab/avr-support/advanced-software-framework

2. Unzip it to <path-to-ot-samr21>/third_party/microchip folder

```bash
$ unzip asf-standalone-archive-3.45.0.85.zip
$ cp xdk-asf-3.45.0 -rf <path-to-ot-samr21>/third_party/microchip/asf
```

3. Build OpenThread Firmware (CLI example) on SAMR21 platform.

```bash
$ cd <path-to-ot-samr21>
$ ./script/build
```

## Flash Binaries

After a successful build, the `elf` files are found in `<path-to-ot-samr21>/build/bin/`.

Compiled binaries may be flashed onto the SAM R21 Xplained Pro using embedded debugger EDBG.

```
Open a terminal

$ openocd -f board/atmel_samr21_xplained_pro.cfg

Leave the terminal open to monitor the status of the opencd server and open a new terminal. In this terminal

$ cd <path-to-ot-samr21>/build/bin
$ arm-none-eabi-gdb ot-cli-ftd
$ (gdb) target remote 127.0.0.1:3333
$ (gdb) load
$ (gdb) monitor reset
$ (gdb) c
```

## Interact

1. Open terminal to `/dev/ttyUSB1` (serial port settings: 115200 8-N-1).
2. Type `help` for list of commands.
3. See [OpenThread CLI Reference README.md][cli] to learn more.

[cli]: https://github.com/openthread/openthread/blob/main/src/cli/README.md

# Contributing

We would love for you to contribute to OpenThread and help make it even better than it is today! See our [Contributing Guidelines](https://github.com/openthread/openthread/blob/main/CONTRIBUTING.md) for more information.

Contributors are required to abide by our [Code of Conduct](https://github.com/openthread/openthread/blob/main/CODE_OF_CONDUCT.md) and [Coding Conventions and Style Guide](https://github.com/openthread/openthread/blob/main/STYLE_GUIDE.md).

# License

OpenThread is released under the [BSD 3-Clause license](https://github.com/openthread/ot-samr21/blob/main/LICENSE). See the [`LICENSE`](https://github.com/openthread/ot-samr21/blob/main/LICENSE) file for more information.

Please only use the OpenThread name and marks when accurately referencing this software distribution. Do not use the marks in a way that suggests you are endorsed by or otherwise affiliated with Nest, Google, or The Thread Group.

# Need help?

There are numerous avenues for OpenThread support:

- Bugs and feature requests — [submit to the Issue Tracker](https://github.com/openthread/openthread/issues)
- Stack Overflow — [post questions using the `openthread` tag](http://stackoverflow.com/questions/tagged/openthread)
- Google Groups — [discussion and announcements at openthread-users](https://groups.google.com/forum/#!forum/openthread-users)

The openthread-users Google Group is the recommended place for users to discuss OpenThread and interact directly with the OpenThread team.
