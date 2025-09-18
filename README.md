# GPS (U-blox NEO-M8N GPS/GNSS Receiver)

## GPS GPIO Connection
| GPS GPIO | Function | RPi GPIO Connection |
|----------|----------|---------------------|
| **VCC (3.3V \ 5V)** | Power | Pin 1 (3.3V) \ Pin 2 \ 4 (5V) |
| *GND* | Ground | Pin 6 \ 9 (GND) |
| *TXD* | Transmit | Pin 10 (GPIO15, RXD) |
| *RXD* | Receive | Pin 8 (GPIO14, TXD) |

## Installation
```besh
sudo raspi-config
```
