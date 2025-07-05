STM32 Bare-Metal: Timer Interrupt (TIM2 + GPIO Toggle)

This project demonstrates how to configure TIM2 on the STM32F401RE to generate periodic interrupts and toggle an output pin (PA5) using pure bare-metal (register-level) programming with CMSIS. No HAL or third-party libraries are used.

🚀 What This Project Covers
- Using TIM2 to generate a 1-second periodic interrupt
- Configuring NVIC to enable TIM2 IRQ
- Writing an interrupt service routine (ISR) for TIM2
- Toggling an LED connected to PA5 on each timer overflow
- Completely non-blocking: no delay loops or SysTick used

📘 Learning Outcomes
- Combine hardware timers and interrupts in embedded systems
- Understand how timer update events trigger interrupts
- Learn NVIC interrupt configuration using CMSIS
- Master low-level peripheral control with direct register access

🛠️ Hardware & Tools
- STM32 Nucleo-F401RE
- Keil uVision (or any ARM-compatible IDE)
- CMSIS + STM32F4 startup files
- On-board LED (PA5)

📂 Project Structure
- `main.c` – Core application logic and timer + GPIO setup
- `startup_stm32f401xe.s` – Make sure TIM2_IRQHandler is not weakly defined
- `stm32f4xx.h` – CMSIS header for STM32F4 series

🔧 How It Works
1. TIM2 is configured to overflow every 1 second:
   - Clock: 16 MHz
   - Prescaler: 16000-1 → 1 kHz timer clock
   - ARR: 1000-1 → 1 Hz overflow
2. TIM2 update interrupt is enabled
3. `TIM2_IRQHandler()` toggles PA5 and clears the UIF flag
4. Main loop remains idle

🧪 Expected Output
- The onboard LED (PA5) toggles ON and OFF every 1 second.
- The microcontroller stays responsive — main loop is not blocked.

📌 Notes
- This is purely register-level programming; no HAL used.
- Be sure to correctly link startup and linker script if using a new project.
- NVIC configuration and ISR name must match vector table.



