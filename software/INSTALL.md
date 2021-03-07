# eeprom configuration

This folder contains the device tree and a dump of EEPROM used to identify and properly configure the raspberry PI
Here are the commands executed to generate it.

```bash
dtc -@ -I dts -O dtb -o xbee_bme280_overlay.dto xbee_bme280_overlay.dts
eepmake eeprom_settings.txt myhat.eep  xbee_bme280_overlay.dto
```

Now, the EEPROM must be flashed. To do this, use the following command.
Note: the JP1 must be set to autorize flash in writing mode.

```bash
sudo eepflash.sh -w -f=myhat.eep -t=24c256
```

