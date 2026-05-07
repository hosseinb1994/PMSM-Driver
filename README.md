# PMSM-Driver
48V three-phase PMSM/BLDC motor driver based on TI DRV8323S gate driver with SPI config. Power stage uses 6× CSD18536KCS MOSFETs (up to 25A) with low-side current sensing on all phases. Onboard 48V→12V (LM5161) and 12V→3.3V (AMS1117) regulators. Interfaces with MCU via 3× PWM, SPI, ENABLE, and FAULT. Suitable for FOC and trapezoidal control.
