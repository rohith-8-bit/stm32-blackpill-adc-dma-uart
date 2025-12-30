**Overview**

This project demonstrates the implementation of a timer-driven ADC acquisition system on the STM32 Blackpill. A hardware timer is configured to run at 100 Hz, and every timer overflow triggers an ADC conversion. The ADC result is transferred to memory using DMA, and once the DMA transfer is complete, the sampled value is transmitted over UART and displayed on a serial terminal.

**Hardware and Tools Used**

Board: STM32 Blackpill (STM32F401 / STM32F411)\
ADC Input: PA0 (ADC Channel 0)\
Timer: TIM2\
UART: USART2 (Virtual COM Port)\
IDE: STM32CubeIDE\
Terminal: PuTTY\
Baud Rate: 115200

**System Flow**

TIM2 is configured to generate an update event at 100 Hz.\
The timer update event(TRGO) is used as the external trigger for ADC conversion.\
Each ADC conversion result is transferred to memory using DMA.\
When the DMA transfer completes, an interrupt is generated.\
Inside the DMA completion callback, the ADC value is sent via UART.\
The ADC values can be observed in real time on a serial terminal.
