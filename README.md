# EXPERIMENT-02-Interfacing-Multiple-Switches-for-LED-Control-Using-MicroPython

## NAME: SARANYA S

## DEPARTMENT: B.E CSE-IOT

## ROLL NO: 212223110044

## DATE OF EXPERIMENT:

## AIM

To interface multiple switches with the Raspberry Pi Pico and control LEDs using MicroPython.

## APPARATUS REQUIRED

Raspberry Pi Pico

2 Push Button Switches

2 LEDs (Light Emitting Diodes)

330Ω Resistors

Breadboard

Jumper Wires

USB Cable

## THEORY



FIGURE-01: RASPBERRY PI PICO PINOUT DIAGRAM

Raspberry Pi Pico is a microcontroller board based on the RP2040 chip. It supports MicroPython, making it suitable for IoT and embedded applications. The Raspberry Pi Pico is a compact microcontroller board featuring a 40-pin layout, including power, ground, GPIO, and communication interface pins. It operates with a dual-core ARM Cortex-M0+ processor and supports MicroPython and C/C++ programming.

The power pins include VBUS (5V from USB), VSYS (1.8V to 5.5V input), 3V3(OUT) (regulated 3.3V output), and multiple ground (GND) connections. The board offers 26 multi-purpose GPIO pins (GP0 to GP28), which can be used for digital input, output, PWM, and communication interfaces such as I2C, SPI, and UART. It also features three analog-to-digital converter (ADC) pins (GP26, GP27, GP28), used for reading analog sensor values, along with an ADC_VREF pin to set the reference voltage.

For communication, I2C (SDA, SCL), SPI (MOSI, MISO, SCK), and UART (TX, RX) interfaces are mapped across different GPIO pins, allowing seamless connectivity with sensors and peripherals. All GPIO pins support PWM (Pulse Width Modulation), making it useful for motor control, LED brightness adjustment, and sound applications. The BOOTSEL button enables USB mass storage mode for firmware flashing, while the DEBUG pins (SWD interface) provide debugging capabilities. With its low power consumption, flexible GPIO options, and rich interface support, the Raspberry Pi Pico is widely used for IoT, embedded systems, robotics, and automation projects.

WORKING PRINCIPLE

The switches are connected as inputs to GPIO pins of the Pico.

The LEDs are connected as outputs.

A MicroPython script reads the switch states and controls the LEDs accordingly.

### CIRCUIT DIAGRAM
 ![image](https://github.com/user-attachments/assets/1c7234b9-5041-4156-94b8-0b846adb6b8e)
    Figure-01 circuit diagram of digital input interface 


Connect switch 1 to GP2 and switch 2 to GP3.

Connect LED 1 to GP14 via a 330Ω resistor.

Connect LED 2 to GP17 via a 330Ω resistor.

Connect the other terminals of the switches to GND.

## PROGRAM (MicroPython):
# Interfacing Multiple switches with LED:
```
from machine import Pin
import time

led = Pin(0, Pin.OUT)

switch = Pin(1, Pin.IN, Pin.PULL_DOWN)

while True:
    if switch.value() == 1:   
        led.value(1)
        print("Switch ON → LED ON")
    else:                    
        led.value(0)
        print("Switch OFF → LED OFF")
    
    time.sleep(0.1)
```

# OUTPUT:
<img width="1919" height="916" alt="Screenshot 2025-09-07 215931" src="https://github.com/user-attachments/assets/6b41393b-b204-4f3d-b441-2bcb7a68d74d" />
<img width="1919" height="983" alt="Screenshot 2025-09-07 215904" src="https://github.com/user-attachments/assets/4cb2053f-321b-466e-bbc6-ee1262eb36f1" />



# Interfacing Multiple switches with Multiple LED's:
```
from machine import Pin
from time import sleep
print("Welcome Pi Pico")
switch1 = Pin(2, Pin.IN, Pin.PULL_UP)
switch2 = Pin(3, Pin.IN, Pin.PULL_UP)
led1 = Pin(15, Pin.OUT)
led2 = Pin(16, Pin.OUT)

while True:
    sw1_state = switch1.value()  
    sw2_state = switch2.value()
    
    print("Switch 1 state:", sw1_state)
    print("Switch 2 state:", sw2_state)
    
    
    led1.value(0)
    led2.value(0)
    
    if sw1_state == 1 and sw2_state == 1:
        led1.value(0)
        led2.value(0)
    elif sw1_state == 1:
        led1.value(0)
        sleep(0.5)
        led1.value(1)
    elif sw2_state == 1:
        led2.value(0)
        sleep(0.5)
        led2.value(1)
    
    sleep(0.1)
```

## OUTPUT:
<img width="1919" height="920" alt="Screenshot 2025-09-07 221520" src="https://github.com/user-attachments/assets/eec1603e-cf3e-4d6c-b1c9-b4d9514d34dd" />
<img width="1919" height="895" alt="Screenshot 2025-09-07 221452" src="https://github.com/user-attachments/assets/68d59077-7be0-45ab-83fa-d1f1b5604707" />
<img width="1919" height="896" alt="Screenshot 2025-09-07 221402" src="https://github.com/user-attachments/assets/3ca80adf-b7e3-4413-a804-b62a4fa97bff" />
<img width="1919" height="897" alt="Screenshot 2025-09-07 221330" src="https://github.com/user-attachments/assets/1e104974-13d3-4eb3-9e36-fcc6c3215481" />



## RESULTS

The multiple switches connected to the Raspberry Pi Pico successfully controlled the LEDs based on their states, confirming the proper interfacing of digital inputs and outputs.

