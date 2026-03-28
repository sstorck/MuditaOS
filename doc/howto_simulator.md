# How to use Mudita simulator

The Mudita simulator is a tool created to speed up developer work. Despite its limitations, it's a good introduction to the Mudita GUI and selected apps and functionalities of MuditaOS.

## Pure phone simulator

Some of the differences between the simulator and the physical device are:

- you can't make phone calls or send text messages (unless you have a connected development board)
- it doesn't work fully as on the phone i.e. there are no visible E-Ink refreshes

You can start the simulator locally by executing the `PurePhone.elf` file located inside your build directory.

You can also run the simulator on disk image with the same layout as we got on the phone by using `run_simulator_on_filesystem_image.sh`.

To unlock the simulator press `s` on the keyboard to simulate the centre function key and then press `c` which simulates a `#` key. Then enter the default pin of `3333`.

To move around the simulator please use the ["Keyboard binding on Linux Pure simulator" document](host_keyboard_bindings.md#keyboard-binding-on-linux-pure-simulator).

## Harmony clock simulator

> [!NOTE]
> After 15s with no interaction, the simulator will shut down and the debugger will detatch.

You can start the simulator locally by executing the `BellHybrid.elf` file located inside your build directory. Alternatively, check the [setup IDE documentation](setup_ide.md) for IDE-specific debugging.

To keep the simulator awake, press `s` on the keyboard to light click.

To move around the simulator, please use the ["Keyboard binding on Linux Harmony simulator" section](host_keyboard_bindings.md#keyboard-binding-on-linux-harmony-simulator).
