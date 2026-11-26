# PowerGuard 32

Limit how far your Android phone charges. An ESP32 sits between the charger and the phone and cuts the power once the battery reaches the limit you set in the app. Keeping a battery below 100% most of the time slows down its ageing.

The project has two parts:

- **ESP32 firmware** (this repository): a small Arduino sketch that listens over Bluetooth Low Energy and switches one output pin.
- **Android app** "PowerGuard 32 - Charge Limit": reads the phone's battery level and sends it, together with your limit, to the ESP32.
  [Get it on Google Play](https://play.google.com/store/apps/details?id=com.tuejj.powerguard32)

## How it works

1. The app connects to the ESP32, which advertises itself as `Charge32`.
2. The app sends the charge limit and, on every change, the current battery level.
3. The ESP32 drives GPIO 4 HIGH while the battery is more than one percent below the limit, and LOW otherwise.
4. Whatever you connect to GPIO 4 switches the power going to the phone.

The app has to stay connected, because the ESP32 only knows the battery level the phone last reported. The app shows a status notification while it is running.

## What you need

- An ESP32 development board with Bluetooth LE
- A switching element controlled by GPIO 4 that interrupts the USB power line to the phone, for example a relay module or a MOSFET switch board that accepts a 3.3 V control signal
- A USB cable or adapter you are willing to cut or put in between
- The Arduino IDE with the ESP32 board package

Only switch the 5 V USB line. Do not put this on the mains side of a charger.

## Flashing

1. Install the Arduino IDE and add the ESP32 board package (Boards Manager, "esp32" by Espressif).
2. Open `PowerGuard32-ESP32/PowerGuard32-ESP32.ino`.
3. Select your board and port, then upload.
4. Open the serial monitor at 115200 baud. You should see `Starting BLE...`.

The sketch was written and tested in July 2023 with the ESP32 Arduino core of that time (2.x). Newer cores changed parts of the BLE API, so the sketch may need small adjustments there.

## Bluetooth protocol

| | |
|---|---|
| Device name | `Charge32` |
| Service UUID | `bcbe96b5-795d-4d06-a4e6-9dd718910290` |
| Characteristic UUID | `63cec759-d14e-4c97-bcdd-06b59a04346f` (read, write, notify) |

Messages are short ASCII strings written to the characteristic:

| Message | Meaning | Example |
|---|---|---|
| `L<number>` | Set the charge limit in percent | `L80` |
| `B<number>` | Report the current battery level in percent | `B63` |

There is no pairing and no authentication. Anyone within Bluetooth range can write to the characteristic, so treat this as a hobby project for use at home.

## Privacy

The app collects no data and has no internet access. See [PRIVACY.md](PRIVACY.md).

## Disclaimer

This is a hobby project, provided as is and without any warranty. You build and use the hardware at your own risk.

## Contact

contact@tuejj.com
