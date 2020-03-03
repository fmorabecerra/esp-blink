# esp-blink -- Blink Example

Starts a FreeRTOS task to blink an LED

## Instructions on how to get you dev environment ready

### Need to replace esp-wroom-32.cfg file to get rid of errors
```cp esp-wroom-32.cfg.working_with_jlink ~/.espressif/tools/openocd-esp32/v0.10.0-esp32-20191114/openocd-esp32/share/openocd/scripts/board/esp-wroom-32.cfg```

### Verify that Jlink is working. And start openocd server
openocd -f interface/jlink.cfg -f board/esp-wroom-32.cfg

### This will flash built program and reset board via Jlink.
openocd -f interface/jlink.cfg -f board/esp-wroom-32.cfg -c "program_esp build/blink.bin 0x10000 verify reset exit"

### This will start a gdb session
xtensa-esp32-elf-gdb -x gdbinit build/blink.elf

## links on how to connect jlink to esp32:
https://docs.espressif.com/projects/esp-idf/en/latest/api-guides/jtag-debugging/configure-other-jtag.html
https://www.shenzhen2u.com/NodeMCU-32S
https://mcuoneclipse.com/2019/09/22/eclipse-jtag-debugging-the-esp32-with-a-segger-j-link/
