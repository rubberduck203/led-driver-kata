# LED Driver Kata

You've been asked to develop an LED Driver for ACME Co.'s new device.
The hardware isn't ready yet, but the specs are looking pretty good.

The device will have 8 memory mapped, single color, LEDs.
The pins are active HIGH.

The low bit maps to LED1; high bit to LED8.

|     |   |   |   |   |   |   |   |   |
| --- | - | - | - | - | - | - | - | - |
| Bit | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |
| LED | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 |

Since the target hardware isn't available yet, the tests must be runnable from the host OS.
We do know that we'll be using the [Atmel ATxmega128a1][atxmega128a1] mcu though, so the solution must also compile with the [avr-gcc compiler][avr-gcc].

## Development Environment

- Host Compiler: [gcc][gcc]
- Target Compiler: [avr-gcc][avr-gcc]
- Test Framework: [CppUTest][cpputest]
- Build: [make][make]

For convenience, a docker image is provided with these dependencies pre-installed.
The following command will start the build tools container and mount the current working directory.

```bash
# from the project root directory
docker run --rm -it -v ${PWD}:/mount rubberduck/led-driver-kata
```

Feel free to add any tools you feel you need, but please make sure they are added to the Dockerfile.

[atxmega128a1]: http://www.microchip.com/wwwproducts/en/ATxmega128A1
[avr-gcc]: http://www.nongnu.org/avr-libc/user-manual/install_tools.html
[gcc]: https://gcc.gnu.org/
[cpputest]: https://cpputest.github.io/
[make]: https://www.gnu.org/software/make/

## Stories

### Turn all the LEDs On

Given the LEDs are off
When requested
Then all of the LEDs are turned on

### Turn all the LEDs Off

Given the LEDs are on
When requested
Then all of the LEDs are turned off

### Turn a Single LED On

Given an LED is off
When requested
Then that LED is turned on
And all other LEDs are in their original state

### Turn a Single LED Off

Given an LED is on
When requested
Then that LED is turned off
And all other LEDs are in their original state

### Initialize the LEDs

When the driver is initialized
Then all of the LEDs should be off

### The pins are active LOW not HIGH!

There was a bug in the spec.
It turns out that the pins are active LOW, not HIGH.
All our lights are on when they should be off and vice versa.
Go fix the bug.

---

[![CC BY-SA 4.0](https://i.creativecommons.org/l/by-sa/4.0/88x31.png)][cc-by-sa]

This work is licensed under a [Creative Commons Attribution-ShareAlike 4.0 International License][cc-by-sa]

[cc-by-sa]: http://creativecommons.org/licenses/by-sa/4.0/