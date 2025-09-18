# GPS (U-blox NEO-M8N GPS/GNSS Receiver)
- A high performance Global Positioning System \ Global Navigation Satellite System receiver module for precise positioning & navigation.
- Supports multiple satellite systems: GPS (USA), GLONASS (Russia), Galileo (Europe), BeiDou (China)
- Works on the L1 frequency band (1575.42 MHz).

## GPS GPIO Connection
| GPS GPIO | Function | RPi GPIO Connection |
|----------|----------|---------------------|
| **VCC (3.3V \ 5V)** | Power | Pin 1 (3.3V) \ Pin 2 \ 4 (5V) |
| *GND* | Ground | Pin 6 \ 9 (GND) |
| *TXD* | Transmit | Pin 10 (GPIO15, RXD) |
| *RXD* | Receive | Pin 8 (GPIO14, TXD) |

## Features
- High sensitivity → works in weak signal env.
- Fast Time-To-First-Fix (TTFF) → acquires satellites quickly (cold start: ~26s, hot start: ~1s).
- Update rate : up to 10 Hz (10 position updates per second).
- Accuracy: Horizontal position: ~2.5 m (without correction), Timing accuracy: ~30 ns with PPS output.
- PPS (Pulse Per Second) pin → useful for time synchronization.
  
## Installation
```besh
sudo raspi-config
```
- Interface Options -> Enable (I2C & SPI)
```besh
sudo reboot
```
```besh
sudo apt install gpsd gpsd-clients python-gps
```
```besh
sudo cat /dev/serial0
```
```besh
sudo gpsmon /dev/serial0
```
- [Error & Verification]()
