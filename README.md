# keychron-awesome

Keychron keyboards custom build instructions

## Keychron Q1 v2 (Knob version) enable response backlight

Response (or dynamic) backlight modes are switched off in stock firmware.

You'll need `qmk` CLI and `git`.

## System Setup

### MacOS

Install toolchain

```
brew install git qmk/qmk/qmk
```

Clone Keychron QMK repo in `~/qmk_firmware`

```
cd ~
git clone https://github.com/Keychron/qmk_firmware.git
```

Switch to `playground` branch

```
cd qmk_firmware
git branch playground
cd ..
```

Init QMK

```
qmk setup
```

It will give you the warning about not official repository being used, it's OK since we'll use Keychron fork.

## Modify firmware sourcecode

Navigate to corresponding keyboard model folder

```
cd qmk_firmware/keyboards/keychron/q1/q1_ansi_stm32l432_ec11
```

It's Q1 V2 (stm32l432) ANSI Knob (ec11) version. TODO: add description for more variants.

Edit firmware config using your favourite editor

```
$EDITOR ../config.h
```

You may uncomment any effects you would like to have. Responsive effects have `_SOLID_` in their names.

Note that `RGB_MATRIX_FRAMEBUFFER_EFFECTS` should also be enabled.

## Compile

That's it, it is time to compile the source

```
qmk compile -km via
```

Resulting firmware lays in `~/qmk_firmware` with the name like `keychron_q1_q1_ansi_stm32l432_ec11_via.hex`

## Flash

As recommended using QMK Toolbox. See official Keychron instruction for details https://www.keychron.com/blogs/archived/how-to-reset-your-keychron-q1-to-factory-settings

## Thanks

* Youhen from Reddit https://www.reddit.com/r/Keychron/comments/va2agx/keychron_q1_v2_guide_how_do_i_changeadd_rgb/
