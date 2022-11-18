# ESPHome Open Air Valve

Visit https://esphome.io/ for instructions on how to deploy this firmware.

More documentation might come available in future updates. Make sure to copy `example.secrets.yaml` to `secrets.yaml` and fill it with your own wifi credentials.


### Sensor Support: SHT-31

More info about this sensor and ESPhome : https://esphome.io/components/sensor/sht3xd.html

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

### Sensor Support: Senseair S8

More info about this sensor and ESPhome : https://esphome.io/components/sensor/senseair.html?highlight=co2+senseair

If you want to add a Senseair S8 Co2 sensor to the Open AIR Valve. Add the following code at the bottom of 'open-air-valve.yaml' 

```
sensor:
  - platform: senseair
    co2:
      name: "Co2 Open AIR Valve x"
    update_interval: 60s
```

### Combination of Senseair S8 & SHT-31 in one Sensor

If you have a combination sensor add the following to the bottom of ''open-air-valve.yaml' 

```
sensor:
  - platform: sht3xd
    temperature:
      name: "Temperature Open AIR Valve x"
    humidity:
      name: "Humidity Open AIR Valve x"
    address: 0x44
    update_interval: 60s
  - platform: senseair
    co2:
      name: "Co2 Open AIR Valve x"
    update_interval: 60s
```
