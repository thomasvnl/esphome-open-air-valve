# ESPHome Open Air Valve

Visit https://esphome.io/ for instructions on how to deploy this firmware.

More documentation might come available in future updates. Make sure to copy `example.secrets.yaml` to `secrets.yaml` and fill it with your own wifi credentials.


### Sensor Support: SHT-31

More info about this sensor and ESPhome : https://esphome.io/components/sensor/sht3xd.html

If you want to add a SHT-31 moisture & Temperature sensor to the Open AIR Valve. Add the following code at the bottom of `open-air-valve.yaml` 

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

If you want to add a Senseair S8 Co2 sensor to the Open AIR Valve. Add the following code at the bottom of `open-air-valve.yaml` 

```
sensor:
  - platform: senseair
    co2:
      name: "Co2 Open AIR Valve x"
    update_interval: 60s
```

### Combination of Senseair S8 & SHT-31 in one Sensor

If you have a combination sensor add the following to the bottom of `open-air-valve.yaml` 

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

### SHT-20 Sensor

If you have a SHT-20 Sensor add the following to the bottom of Add the following righ below "board: esp32dev" 

```
sensor:
  - platform: custom
    lambda: |-
      auto sht20 = new SHT20();
      App.register_component(sht20);
      return {sht20->temperature_sensor, sht20->humidity_sensor, sht20->vpd_sensor, sht20->dew_point_sensor};
    sensors:
      - name: "Temperature Open AIR Valve x"
        id: sensor_temperature
        unit_of_measurement: °C
        accuracy_decimals: 2
      - name: "Humidity Open AIR Valve x"
        id: sensor_humidity
        unit_of_measurement: "%"
        accuracy_decimals: 2
      - name: "Open AIR Valve x Vapour-pressure deficit"
        id: sensor_vpd
        unit_of_measurement: "kPa"
        accuracy_decimals: 2
      - name: "Open AIR Valve x Dew point"
        id: sensor_dew_point
        unit_of_measurement: °C
        accuracy_decimals: 2

```
Add the following righ below "board: esp32dev" 
```
  libraries:
    - Wire
    - u-fire/uFire SHT20@^1.1.1
  includes: sht20.h
```

Place the SHT20.H file in the same directory as the `open-air-valve.yaml`.

Change all the 'x' in the document for a number or a letter so you know which valve is which. (if sensors have identical names they wont show up in HA)

