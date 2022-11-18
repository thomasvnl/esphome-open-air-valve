# ESPHome Open Air Valve

Visit https://esphome.io/ for instructions on how to deploy this firmware.

More documentation might come available in future updates. Make sure to copy `example.secrets.yaml` to `secrets.yaml` and fill it with your own wifi credentials.


If you want to add a SHT-31 moisture & Temperature sensor to the Open AIR Valve. Add the following code at the bottom of 'open-air-valve.yaml' 

```
sensor:
  - platform: sht3xd
    temperature:
      name: "Temperature Open AIR Valve x"
    humidity:
      name: "Humidity Open AIR Valve x"
    address: 0x44
    update_interval: 60s
```

Visit [the Open AIR repository](https://github.com/Flamingo-tech/Open-AIR) for more details about the project this firmware belongs to.
