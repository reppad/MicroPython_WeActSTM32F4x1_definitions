# MicroPython board definitions for WeAct MiniF4-STM32F4x1 boards

Board definitions for boards
* WeAct STM32F401CEU6
* WeAct STM32F411CEU6

These Definitions are **made for MicroPython 1.14** ([commit 9dedcf1](https://github.com/micropython/micropython/tree/9dedcf122d19c6b7452adb48ff5567509adfb073))

All definitions can be configured to fit boards variants by editing **mpconfigboard.h**
* HSE crystal : 25 or 8 MHz
    * WEACT_STUDIO_HSE_IS_8MHZ
* Flash : internal or 4/8/16 MB SPI flash
    * MICROPY_HW_ENABLE_INTERNAL_FLASH_STORAGE
    * MICROPY_HW_SPIFLASH_SIZE_BITS


## Build

### Documentation

MycroPython documentation
> https://github.com/micropython/micropython/wiki/Building-Micropython-Binaries

WeAct documentation
> https://github.com/reppad/MiniF4-STM32F4x1/tree/master/SDK/STM32F411CEU6/MicroPython

### How to build

* Install commons build tools (*build-essential, git...*) and ARM gcc toolchain
> https://learn.adafruit.com/building-circuitpython/linux#install-build-tools-on-ubuntu-2986713-2


* Get micropython sources and build mpy-cross
```
git clone https://github.com/micropython/micropython.git
cd micropython
git submodule update --init
cd mpy-cross
make -j4
cd ../ports/stm32/boards
```

* Get folders *WeAct_F401CE* and *WeAct_F401CE* from this repo and past it in current directory (*micropython/ports/stm32/boards*)

* Configure the board variant in *mpconfigboard.h*

* Go back to *micropython/ports/stm32* directory

* Build the desired board
```
make BOARD=WeAct_F411CE -j
# if the toolchain is not in your PATH
make BOARD=WeAct_F411CE CROSS_COMPILE=/path/to/gcc-arm-none-eabi-10-2020-q4-major/bin/arm-none-eabi- -j
```
