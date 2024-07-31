# Battery Management System (BMS) with Buck-Boost Converter

## Brief

This Battery Management System (BMS) with Buck-Boost Converter is designed for lithium battery applications, providing a flexible voltage range of 3-5V. 
It is particularly useful in projects requiring stable 3.3V or 5V outputs. The system includes a charging circuit, protection circuit, and a DC-DC buck-boost converter, 
ensuring consistent voltage, enhanced battery safety, and adaptability for various devices.

## Features

The key components of the module include:

- **Charging Circuit:** Utilizing the [MCP73831](https://ww1.microchip.com/downloads/en/DeviceDoc/MCP73831-Family-Data-Sheet-DS20001984H.pdf),
  this circuit facilitates the selection of charge current via a resistor and incorporates an indicator diode.

- **Protection Circuit:** Protection is ensured by [DW01A](https://hmsemi.com/downfile/DW01A.PDF) and [FS8205A](https://datasheet.lcsc.com/lcsc/2010271837_FUXINSEMI-FS8205A_C908265.pdf).
  The FS8205A connects the battery's negative to the common ground, with DW01A controlling battery operation. The transistor disconnects the battery in cases of discharge, overcharge, short circuit, etc.

- **DC-DC Buck-Boost Converter:** Employing [TPS63020DSJR](https://www.ti.com/lit/ds/symlink/tps63020.pdf?ts=1700141277158&ref_url=https%253A%252F%252Fwww.ti.com%252Fproduct%252FTPS63020),
  this component enables voltage conversion. The goal is to maintain a constant voltage level regardless of the battery charge, acting as a step-up converter when voltage is low and a step-down converter when it's high.

In summary, this module facilitates battery charging, provides protection, and allows for adjustable output voltage.

> Refer to the complete schematic in `BMS_Buck-Boost.pdf`.

## Module Appearance

![Top Layer](https://github.com/tor1kk/BMS_Buck-Boost/blob/master/img/top_layer.jpg)
![Bottom Layer](https://github.com/tor1kk/BMS_Buck-Boost/blob/master/img/bottom_layer.jpg)

## Pinouts

- `-B` and `+B` are used to connect the battery.
- `+B`, `+V`, and `GND` are for connecting to the load, with `+B` used for measuring battery voltage.

## Notes

- While using the module during charging and securing the load, certain limitations exist when the level on the `VBUS` line is high. At this point, transistor Q2 (refer to the schematic [here](https://github.com/tor1kk/BMS_Buck-Boost/blob/master/BMS_Buck-Boost.pdf)) doesn't pass the voltage. This is done to optimize battery charge. If you want to use `VBUS` for the DC-DC converter during charging, employ diode `D4` and an additional diode to prevent current from `+VCC_IN` to `+BATT`.
