# PMSM Driver

A 48V three-phase PMSM/BLDC motor driver board based on the **Texas Instruments DRV8323S** smart gate driver with SPI configuration. Designed for high-performance motor control applications such as robotics, drones, e-mobility, and industrial actuators using FOC or trapezoidal commutation.

---

## Features

- **Input voltage:** 48V DC (up to 25A continuous)
- **Gate driver:** TI DRV8323S in 3-PWM mode with integrated current sense amplifiers
- **Power stage:** 6× CSD18536KCS N-channel MOSFETs (three half-bridges)
- **Current sensing:** Low-side shunt resistors (WSLP2512L5000FEA, 0.5 mΩ) on all three phases, routed to MCU ADC channels
- **Protection:** Reverse polarity / freewheeling Schottky diode (SS24S), fault reporting to MCU
- **MCU interface:** 3× PWM, SPI (SCLK/SDI/SDO/nSCS), ENABLE, FAULT, and amplifier calibration GPIOs

---

## Power Supply Architecture

| Stage | Component | Purpose |
|-------|-----------|---------|
| 48V → 12V | LM5161 (buck converter) | Gate driver supply |
| 12V → 3.3V | AMS1117-3.3 (LDO) | Logic / MCU supply |

The 48V input is provided through a connector rated for 48V / 25A max.

---

## MCU Interface

| Signal | Direction | Description |
|--------|-----------|-------------|
| PWM1, PWM2, PWM3 | MCU → Driver | High-side PWM inputs (3-PWM mode) |
| SCLK, SDI, SDO, nSCS | SPI | DRV8323S configuration |
| ENABLE | MCU → Driver | High: wake up / Low: sleep |
| FAULT | Driver → MCU | Fault indication |
| AMP_CALIBRATION | MCU → Driver | Current sense amplifier calibration |
| CUR_SENSE_PH_A/B/C | Driver → MCU ADC | Phase current feedback |

---

## Bill of Materials (Key Components)

| Reference | Part Number | Description |
|-----------|-------------|-------------|
| U1 | DRV8323S | Three-phase smart gate driver |
| U2 | LM5161PWPT | 48V → 12V buck converter |
| U3 | AMS1117-3.3 | 12V → 3.3V LDO |
| Q1–Q6 | CSD18536KCS | N-channel power MOSFETs |
| R16–R18 | WSLP2512L5000FEA | 0.5 mΩ current sense shunts |
| D1 | SS24S-E3/61T | Schottky diode |
| L1 | DR125-101-R | Buck converter inductor |

---

## Applications

- Brushless DC (BLDC) and PMSM motor control
- Field-Oriented Control (FOC)
- Trapezoidal commutation
- Robotics, drones, e-bikes, and industrial actuators

---

## Design Tool

This project was designed using [CircuitMaker](https://circuitmaker.com/) by Altium.

---

## Author

**H. Baghaei**

---

## License

Released under the MIT License. See `LICENSE` for details.
