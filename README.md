# esp-blink -- Blink Example

Starts a FreeRTOS task to blink an LED. 

## Instructions on how to get you dev environment ready
The .vscode folder includes config files to launch an openOCD debug session.

## Set up debugging environment
You will need to install openOCD. you can follow the [expressif debuging](https://docs.espressif.com/projects/esp-idf/en/latest/esp32/api-guides/jtag-debugging/) instructions to set this up.

### Helpful tips
Need to replace the esp-wroom-32.cfg openOCD file to get rid of errors when trying to launch openOCD server.
```
cp esp-wroom-32.cfg ~/.espressif/tools/openocd-esp32/v0.10.0-esp32-20191114/openocd-esp32/share/openocd/scripts/board/esp-wroom-32.cfg
```
Use the following to verify that Jlink is working and start openocd server
```
openocd -f interface/jlink.cfg -f board/esp-wroom-32.cfg
```

The following will flash your pre-built esp32 app via Jlink.
```
openocd -f interface/jlink.cfg -f board/esp-wroom-32.cfg -c "program_esp build/blink.bin 0x10000 verify reset exit"
```

This will start a gdb session if you have the openOCD server working
```
xtensa-esp32-elf-gdb -x gdbinit build/blink.elf
```
### Other helpful resources when connecting jlink to esp32:

* [esp32 Jtag pins](https://docs.espressif.com/projects/esp-idf/en/latest/api-guides/jtag-debugging/configure-other-jtag.html)
* [mcuoneeclipse](https://mcuoneclipse.com/2019/09/22/eclipse-jtag-debugging-the-esp32-with-a-segger-j-link/) - Jlink pins needed for esp32
* [NodeMCU](https://www.shenzhen2u.com/NodeMCU-32S) - Pinout for board that I am using. yours board may be different
