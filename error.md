# Common GPS Errors (u-blox NEO-M8N on Raspberry Pi)

## 1. `Permission denied`
- **Cause:** User doesn’t have access to `/dev/ttyS0` or `/dev/ttyAMA0`.
- **Fix:**  
  - Use `sudo`  
  - Add user to `dialout` group  
  - Or create udev rule with `MODE="0666"`

---

## 2. `already opened by another process`
- **Cause:** Another process (e.g., `cat`, `gpsmon`, or `serial-getty`) is using the port.
- **Fix:**  
  - Check background jobs: `jobs -l` and `kill %1`  
  - Disable getty:  
    ```bash
    sudo systemctl stop serial-getty@ttyS0.service
    sudo systemctl disable serial-getty@ttyS0.service
    ```

---

## 3. No data / blank output
- **Cause:** Wrong wiring, wrong UART, or wrong baud rate.  
- **Fix:**  
  - Cross-check TX ↔ RX  
  - Ensure correct port (`ttyS0` vs `ttyAMA0`)  
  - Try baud rates `9600`, `38400`, `115200`

---

## 4. NMEA shows `$GNRMC,,V,...` (no coordinates)
- **Cause:** GPS has not locked onto satellites yet.  
- **Fix:** Place module outdoors with clear sky. Wait for blinking LED.

---

## 5. `stty: /dev/ttyS0: Permission denied`
- **Cause:** Same as error #1.  
- **Fix:** Use `sudo` or adjust permissions.

---

## 6. GPS module LED never lights
- **Cause:** Module not powered or faulty.  
- **Fix:** Connect VCC → 5V (with onboard regulator) and GND → Pi GND.

---

## 7. Output shows garbage characters
- **Cause:** Baud rate mismatch.  
- **Fix:** Use correct baud (`9600` default for most M8N).

---

## 8. `gpsmon:ERROR: SER: device open of /dev/ttyS0 failed`
- **Cause:** Missing permissions or busy device.  
- **Fix:** Combine solutions from #1 and #2.
