# STM32L072RB
Extreme low power, plenty of peripherals, USB bootloader ready to rip, hell yeah.

## Specs I Care About
Flash:  128kB
EEPROM: 6kB
RAM:    10kB
SPI:    6
I2S:    1
I2C:    3
USART:  4
LPUART: 1
USB:    1 (package will connect to usb C ofc)
GPIO:   51
12bADC: 1 (16channel)
12bDAC: 2
freq:   32 MHz
DCV:    1.8V to 3.6V
PCKG:   LQFP64

## Notes from the getting started guide
https://www.st.com/resource/en/application_note/an4467-getting-started-with-stm32l0xx-hardware-development-stmicroelectronics.pdf

* VDD voltage between 1.8V and 3.6V
* VDD_USB is separate voltage supply for USB XCVR, if not used supply 3.0 to 3.6V
* Need 3V minimum for VDD_USB to have adequate USB line level
* V_core is provided by internal LDO, programmable from 1.2V to 1.8V
* Selectable core voltage ranges which limit clock speed
    * Range 1 = 1.8V | 32Mhz
    * Range 2 = 1.5V | 16Mhz
    * Range 3 = 1.2V | 4.2Mhz
* 10uF ceramic per package + 100nF ceramic for each Vdd pin
* V_dda 1uF ceramic + 100nF ceramic
* Connect Vref1 to V_dda
* Pulldown capacitor recommended on nRST to reduce parasitic reset
* Sysclk can be driven by 4 different sources
    * HSI16 high speed internal oscillator clock
    * HSE high speed external oscillator clock
    * PLL clocl
    * MSI multispeed internal oscillator clock
        * Low cost, no external components
        * 7 Frequencies available from 65.5kHz to 4.2MHz
        * enabled, disabled by RCC_CR register, default on
* Oscillator clocks are divided by 4
* Device has secondary clock sources 37kHz low speed internal RC and 32.768kHz low speed external crystal
* Each clock source can be enabled or disabled independently when not in use
* USB Bootloader is in system memory, BOOT0 = 1 and nBOOT1 = 1
* Connect the SWD port