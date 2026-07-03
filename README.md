# Solar-Panel-Tracker-project
Dual-Axis Solar Panel Tracker — STM32F103, FreeRTOS, PID Control, C programming
Built a fully functional solar tracking system using an STM32F103C8T6 microcontroller running FreeRTOS, designed to automatically orient a solar panel toward the sun across both the horizontal and vertical axes.
How it works:
Four light-dependent resistors (LDRs) are arranged in a 2×2 grid on the panel surface. The system continuously compares light intensity between opposite sensor pairs to detect where the sun is relative to the panel. Two independent PID controllers process this error and drive two DC gear motors to correct the panel's position in real time.
Key technical highlights:
⚙️ Dual-axis PID control — proportional, integral, and derivative terms tuned independently for each axis, with integral windup protection and output clamping
📡 Register-level STM32 programming — GPIO, ADC2, TIM3 PWM, and I2C all configured directly through hardware registers without relying on CubeMX-generated drivers
🔄 FreeRTOS multitasking — two independent tasks running concurrently: one handling the full sensor-PID-motor control loop, another managing the LCD display over I2C without ever blocking motor actuation
💡 ADC oversampling — 30 samples averaged per channel per cycle for clean readings from high-impedance LDR voltage dividers
🖥️ Live diagnostics — 16×2 LCD displays all four LDR readings in real time via I2C with a PCF8574 backpack
