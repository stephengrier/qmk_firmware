# stephengrier's TADA68 layout

This layout mostly replicates the default ANSI layout of the TADA68 but with a
few modifications to suit my tastes.

The modifications from the default keymap are:

* Replaced capslock with a second function key
* Swapped the left ALT and Win keys to be more like the Mac layout
* Added an arrow key cluster on the IJKL keys
* Fn+x toggles backlight breathing mode

With this keymap backlight breathing mode can be enabled/disabled with Fn+x.
This is not supported at all in the default keymap.

## Compiling and flashing

Compile the firmware with:

```bash
qmk compile -kb tada68 -km stephengrier
```

This will create a hex file called `tada68_stephengrier.hex`. If you are using
the stock mass storage bootloader you will need a bin file instead. In this case
you should comment out the `BOOTLOADER` line from the `rules.mk` file before
compiling.

### Flashing

This keymap expects the DFU bootloader. If you are using the stock mass storage
bootloader that comes with the Tada68 then you will need to comment out the
`BOOTLOADER` line from the `rules.mk` file and recompile (see above).

```bash
dfu-programmer atmega32u4 erase
dfu-programmer atmega32u4 flash tada68_stephengrier.hex
dfu-programmer atmega32u4 reset
```
