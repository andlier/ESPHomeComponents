ESPHome Components
======

This repo contains components for Microfire sensors that can be used in ESPHome and Home Assistant. 

### Use
There are several examples:
 - [example_mod_ec.yaml](example_mod_ec.yaml): Mod-EC used by itself
 - [example_mod_ec_dallas.yaml](example_mod_ec_dallas.yaml): Mod-EC that uses a Dallas DS18B20 as a water temperature source
 - [example_mod_ph.yaml](example_mod_ph.yaml): Mod-pH used by itself
 - [example_mod_ph_dallas.yaml](example_mod_ph_dallas.yaml): Mod-pH that uses a Dallas DS18B20 as a water temperature source
  - [example_mod_orp.yaml](example_mod_orp.yaml): Mod-ORP used by itself
 - [example_ec_ph_dallas.yaml](example_ec_ph_dallas.yaml): Mod-EC, Mod-pH and DS18B20 used together
 - [example_ec_ph_orp_dallas.yaml](example_ec_ph_orp_dallas.yaml): Mod-EC, Mod-pH, Mod-ORP and DS18B20 used together

 ### Temperature Compensation
 For conductivity and pH measurements, the temperature of the liquid is important. For accurate meausurements, a temperature sensor is needed. 

 #### Mod-EC
 The component has several optional configuration variables. See [example_mod_ec_dallas.yaml](example_mod_ec_dallas.yaml) for how it is used.
 - `temperature_sensor` - the ID of a temperature sensor, if not provided, 25°C is used. 
 - `temperature_coefficient` - *Defaults to 0.019* - The temperature coefficient to use for compensation. This is usually 0.019 for freshwater/hydroponis/pools, and 0.021 for saltwater. Other liquids have different coefficients. 
 - `temperature_constant` - *Defaults to 25.0* - The temperature to adjust the measurement to. For example, the default of 25°C will adjust the measured value as if the water was 25°C. 

 #### Mod-pH
 The component has several optional configuration variables. See [example_mod_ph_dallas.yaml](example_mod_ph_dallas.yaml)for how it is used.
 - `temperature_sensor` - the ID of a temperature sensor, if not provided, 25°C is used. 

* * *

### Calibration
Each sensor example comes with calibration controls. They are implemented with lamdas within Home Assistant. 

An example of the lambda:
```yaml
  - platform: template
    id: ec_calibrate_low
    name: EC Calibrate Low 0.1
    icon: mdi:format-vertical-align-bottom
    on_press:
        lambda: |-
          id(ec).calibrateLow(0.1);
```
To change the particular low-point calibration, edit the 2 `0.1` points to match your solution. Do the same thing for mid- and high-points as needed. 

 #### Mod-EC
 The Mod-EC sensor can use up to three calibration points: low, mid, and high. A single point can also be used. Read the [datasheet](https://docs.google.com/document/d/1tfF-OZBhD1JVnNeXnkn0zgdczgs0994KFTN9oT3JPR4/export?format=pdf&ref=microfire-llc) for detailed information. 

 #### Mod-pH
 The Mod-pH sensor can use up to three calibration points: low, mid, and high. A single point can also be used. Read the [datasheet](https://docs.google.com/document/d/1DSG9bdEHDt9mdQInVfCWy4qiohi6sVeEy7QbvBfUmU0/export?format=pdf&ref=microfire-llc) for detailed information. 

 #### Mod-ORP
 The Mod-ORP sensor uses a single point. Read the [datasheet](https://docs.google.com/document/d/1nhQdt0k4pQb8jUJF8Eyrj9TyxYFNImvvaVTNkO53OXs/export?format=pdf&ref=microfire-llc) for detailed information. 

### Hardware
All components can be purchased at [microfire.co](https://microfire.co/). 

* * *

### Ask a question 🤙

*   [Discord](https://discord.gg/rAnZPdW)
*   [questions@microfire.co](mailto:questions@microfire.co)

* * *

### Website
[microfire.co](https://microfire.co)
