---
layout: page
title: "RFXtrx Sensor"
description: "Instructions how to integrate RFXtrx sensors into Home Assistant."
date: 2015-08-06 17:15
sidebar: true
comments: false
sharing: true
footer: true
ha_category: Sensor
---

The `rfxtrx` platform support sensors that communicate in the frequency range of 433.92 MHz.

First you have to set up your [rfxtrx hub.](/components/rfxtrx/)
The easiest way to find your sensors is to add this to your `configuration.yaml`:

```yaml
sensor: 
 platform: rfxtrx
 automatic_add: True
```

Then when the sensor emits a signal it will be automatically added:

<p class='img'>
<img src='/images/components/rfxtrx/sensor.png' />
</p>

Here the name is 0a52080000301004d240259 and you can verify that it works from the frontend. 
Then you should update your configuration to:

```yaml
sensor:
 platform: rfxtrx
 devices:
    0a52080000301004d240259: 
        name: device_name
```

If you want to display several data types from one sensor:

```yaml
sensor: 
 platform: rfxtrx
 devices:
    0a520802060100ff0e0269: 
        name: Bath
        data_type: 
         - Humidity
         - Temperature
```



Example configuration:

```yaml
# Example configuration.yaml entry
sensor: 
 platform: rfxtrx
 automatic_add: True
 devices:
   0a52080705020095220269:
     name: Lving
   0a520802060100ff0e0269:
        name: Bath
        data_type: 
         - Humidity
         - Temperature
```

Configuration variables:

- **devices**  (*Optional*): A list of devices with their name to use in the frontend.
- **automatic_add** (*Optional*): To enable the automatic addition of new lights.
- **data_type**  (*Optional*): Which data type the sensor should show

