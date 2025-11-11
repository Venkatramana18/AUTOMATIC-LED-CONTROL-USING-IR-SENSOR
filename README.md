# AUTOMATIC-LED-CONTROL-USING-IR-SENSOR
##  AIM
To design and implement a system using the **STM32 microcontroller** where an LED automatically turns ON or OFF based on the input from an **IR sensor**.

---

##  Components Required
- STM32 Nucleo or Discovery Board (e.g., **Nucleo-G071RB**)
- IR Sensor Module
- LED (5mm Green or any color)
- Jumper wires
- Breadboard

---

##  Theory
An **IR sensor** detects the presence of an object by emitting and receiving infrared light.

### IR Sensor Behavior
- When an **object is detected**, the IR sensor output goes **LOW (0V)**.
- When **no object is detected**, the output stays **HIGH (3.3V)**.

### Microcontroller Response
- If **IR output = LOW** → **LED ON**
- If **IR output = HIGH** → **LED OFF**
### **Procedure**

1. Open **STM32CubeIDE**.
   <img width="924" height="636" alt="Screenshot 2025-11-11 210049" src="https://github.com/user-attachments/assets/0775f68f-a7fe-45a6-b9e9-9d355ab2106e" />

2. Click **File → New STM32 Project**.
  <img width="988" height="619" alt="Screenshot 2025-11-11 210057" src="https://github.com/user-attachments/assets/ea48e0c4-3630-413a-a24c-296685f74b05" />

3. Select the **target microcontroller** or board and click **Next**.
   <img width="736" height="548" alt="Screenshot 2025-11-11 210107" src="https://github.com/user-attachments/assets/03edd505-ea9e-40ae-a6bb-23f3f1c1b4cc" />



4. Name the project.
   <img width="865" height="853" alt="Screenshot 2025-11-11 210135" src="https://github.com/user-attachments/assets/05aa134b-e37b-4072-b7ca-41fee3752b65" />


5. The corresponding `.ioc` file will be generated automatically.
  <img width="581" height="469" alt="Screenshot 2025-11-11 210151" src="https://github.com/user-attachments/assets/160e7ba6-eef5-4e05-a670-834d87804dd0" />

6. Configure the pins as **GPIO (Input/Output)**, **USART**, etc. as needed.
   <img width="580" height="499" alt="Screenshot 2025-11-11 210157" src="https://github.com/user-attachments/assets/acdf9e54-42f4-4c24-bc1e-9ce4c038aadd" />


7. Save the configuration (`Ctrl + S`) – the base C program will be generated automatically.
   <img width="678" height="431" alt="Screenshot 2025-11-11 210210" src="https://github.com/user-attachments/assets/d67b70e3-6b25-42a5-bd85-0ebc130447f9" />

 
8. Edit the generated main program as required.
  <img width="970" height="589" alt="Screenshot 2025-11-11 210217" src="https://github.com/user-attachments/assets/3f7713b1-14db-4863-98af-24b89652f7c0" />


9. Click **Project → Build All**.
    <img width="989" height="572" alt="Screenshot 2025-11-11 210225" src="https://github.com/user-attachments/assets/99676ece-a59d-4399-aa1f-48c8f9ebcb79" />

10. Link the **HEX file** using the post-build process.
    <img width="960" height="417" alt="Screenshot 2025-11-11 210232" src="https://github.com/user-attachments/assets/94870e18-f261-427a-9685-13927b7954dc" />

11. Click **Debug** and connect the **STM Nucleo Board**.
 <img width="775" height="578" alt="Screenshot 2025-11-11 210239" src="https://github.com/user-attachments/assets/6ec94460-c184-41cf-b72f-38777e650e5e" />


13. Click **Run** to execute the program.
    
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
        GPIO_PinState ir = HAL_GPIO_ReadPin(GPIOA, GPIO_PIN_10); // IR OUT at PA10 (D2)

	      if (ir == GPIO_PIN_RESET)  // IR sensor HIGH = object detected
	      {
	          HAL_GPIO_WritePin(GPIOB, GPIO_PIN_3, GPIO_PIN_SET); // Turn ON LED
	      }
	      else
	      {
	          HAL_GPIO_WritePin(GPIOB, GPIO_PIN_3, GPIO_PIN_RESET); // Turn OFF LED
	      }

	      HAL_Delay(100);
    }
}
```
---
### OUTPUT
CASE 1: LED ON 
<img width="900" height="451" alt="Screenshot 2025-11-10 204807" src="https://github.com/user-attachments/assets/6525abdc-d77e-48fe-8406-17411fe752b1" />


CASE 2: LED OFF
<img width="998" height="732" alt="Screenshot 2025-11-11 210330" src="https://github.com/user-attachments/assets/6f922767-347c-41f5-93e5-c23bb5d64134" />

---
### RESULT

The experiment on IR Sensor-Based Automatic LED Control using STM32 was successfully carried out. The STM32 microcontroller accurately read the IR sensor output and controlled the LED based on object detection. When an object was detected, the LED glowed (ON) and when no object was present, the LED remained OFF. Thus, the objective of the experiment was achieved.




