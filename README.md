# LED-BLINK

# 💡 Experiment 01 – Interfacing a Digital Output (LED) with ARM Development Board

### 🎯 **Aim**
To interface a digital output (LED) to an ARM development board and write a blink code.

---

### ⚙️ **Components Required**
- STM32CubeIDE  
- NUCLEO ARM Development Board  

---

### 🧠 **Theory**

**ARM (Advanced RISC Machine)** is a 32-bit processor architecture developed by ARM Holdings. It is widely used in embedded systems and SoC (System-on-Chip) products. Many semiconductor companies like Samsung, Atmel, and Texas Instruments license ARM architecture to design their own SoCs.
### 🧩 **What is an ARM7 Processor?**
The **ARM7 processor** is commonly used in embedded system applications. It provides a balance between the classic ARM architecture and the newer Cortex series, offering an excellent platform for both hardware and software development.
### 🔍 **LPC2148 Microcontroller**
The **LPC2148**, developed by NXP Semiconductors (Philips), is a 16/32-bit ARM7-based microcontroller featuring a wide range of peripherals.
#### **Key Features**
- 16/32-bit ARM7TDMI-S core in LQFP64 package  
- On-chip **Flash memory**: 32 KB – 512 KB  
- On-chip **SRAM**: 8 KB – 40 KB  
- **ISP/IAP** via on-chip bootloader  
- **Embedded ICE-RT** and **Real Monitor** for real-time debugging  
- **USB 2.0** full-speed device controller with 2 KB endpoint RAM  
- **10-bit ADC** (6 or 14 channels, 2.44 μs conversion time)  
- **10-bit DAC** for analog output  
- **Timers:** Two 32-bit timers, watchdog, and PWM unit  
- **RTC** with 32 kHz clock input  
- **UARTs (2x), I²C (2x)** up to 400 kbit/s  
- **5V-tolerant GPIOs**, 21 external interrupt pins  
- **Max CPU Clock:** 60 MHz using on-chip PLL (lock time 100 µs)  
- **Crystal Frequency:** 1 MHz – 25 MHz  
- **Power modes:** Idle and Power-down with peripheral clock scaling  

---

### 🧭 **Procedure**

1. Open **STM32CubeIDE**.
   <img width="1918" height="1199" alt="Screenshot 2025-10-29 213152" src="https://github.com/user-attachments/assets/27c93289-cc17-4ab8-8a3f-63caca348a9c" />


2. Click **File → New STM32 Project**.
  <img width="1918" height="1197" alt="Screenshot 2025-10-29 211447" src="https://github.com/user-attachments/assets/14963674-fc74-4989-a83e-24ab643909b8" />
<img width="1900" height="1187" alt="Screenshot 2025-10-29 211635" src="https://github.com/user-attachments/assets/437814eb-5885-4c35-a7a0-d7cc002e4b77" />


3. Select the **target microcontroller** or board and click **Next**.
  <img width="1919" height="1199" alt="Screenshot 2025-10-29 211849" src="https://github.com/user-attachments/assets/b1ca1781-c674-4fd6-8ad1-600eb29cfbfd" />




4. Name the project.
  <img width="1919" height="1199" alt="Screenshot 2025-10-29 211950" src="https://github.com/user-attachments/assets/fb338aaf-ece4-4067-a6ee-b0c390bd9e56" />


5. The corresponding `.ioc` file will be generated automatically.
  <img width="1919" height="1198" alt="Screenshot 2025-10-29 212224" src="https://github.com/user-attachments/assets/67e95930-6c1e-4269-8d6a-b53880b32970" />

6. Configure the pins as **GPIO (Input/Output)**, **USART**, etc. as needed.
   <img width="1918" height="1199" alt="Screenshot 2025-10-29 212300" src="https://github.com/user-attachments/assets/c9ab17be-d5da-4c5f-a82e-dc2ed4dd0d71" />

7. Save the configuration (`Ctrl + S`) – the base C program will be generated automatically.
  <img width="1080" height="608" alt="image" src="https://github.com/user-attachments/assets/ea9b5448-1f4d-4fde-a478-8248685b271c" />

8. Edit the generated main program as required.
  <img width="1918" height="1199" alt="Screenshot 2025-10-29 212407" src="https://github.com/user-attachments/assets/0971213b-3a3e-426e-a6c5-71b4d47f1952" />

<img width="1727" height="868" alt="image" src="https://github.com/user-attachments/assets/3208a597-7e7e-46f3-9821-ed6dec4fd2a1" />


9. Click **Project → Build All**.
    <img width="1917" height="1198" alt="Screenshot 2025-10-29 212627" src="https://github.com/user-attachments/assets/ab2ddebc-422f-4718-ac3a-39b5540aa7cf" />


10. Link the **HEX file** using the post-build process.
  <img width="1917" height="1199" alt="Screenshot 2025-10-29 212723" src="https://github.com/user-attachments/assets/ec498c59-c8fe-4529-9488-a2f5ed65ab2d" />


11. Click **Debug** and connect the **STM Nucleo Board**.
    <img width="1918" height="1199" alt="Screenshot 2025-10-29 213116" src="https://github.com/user-attachments/assets/dbad5a92-4685-4e33-8e8f-d59c738b910c" />

12. Click **Run** to execute the program.
    
---

### 💻 **Program**


```c
#include "main.h"

void SystemClock_Config(void);
static void MX_GPIO_Init(void);

int main(void)
{
    HAL_Init();
    SystemClock_Config();
    MX_GPIO_Init();

    while (1)
    {
        HAL_GPIO_WritePin(GPIOA, GPIO_PIN_5, GPIO_PIN_RESET);
        HAL_Delay(1000);
        HAL_GPIO_WritePin(GPIOA, GPIO_PIN_5, GPIO_PIN_SET);
        HAL_Delay(1000);
    }
}
```
---
### OUTPUT

CASE 1: LED ON 
![WhatsApp Image 2025-10-27 at 22 06 09_027e2f84](https://github.com/user-attachments/assets/74e87174-6c32-414e-99c3-b1aec7b66751)


CASE 2: LED OFF
![WhatsApp Image 2025-10-27 at 22 05 59_6a1ec76d](https://github.com/user-attachments/assets/a2e2e1d9-edf7-420d-9ebe-e358a39ebc01)


---
### RESULT

Interfacing a digital output with ARM microcontroller is executed and the results are verified.
