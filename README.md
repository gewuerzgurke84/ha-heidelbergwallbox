Welcome to my little documentation repository that describes how to integrate Homeassistant with Heidelberg Energy Wallbox.

# Introduction
I bought a Heidelberg Energy Wallbox to charge my electric car. The Wallbox can be controlled using RS485/Modbus interface. With this integration I want to control the Wallbox to optimize the charge/energy level since I have solar modules installed on my roof. (german: "PV Überschussladen")
Furthermore I tried to assemble everything with as few components as required.

# Environment
- [Heidelberg Energy Control](https://www.heidelberg-wallbox.eu/heidelberg-wallbox-energy-control/7/heidelberg-wallbox-energy-control-11kw-5m/7-5m-foerderfaehig-durch-die-kfw)
- Homeassistant 2022.7.5 running inside a Jail
- FreeBSD 13.0-RELEASE
- [DSD Tech RS485/USB Adapter](https://www.amazon.de/DSD-TECH-Konverter-Kompatibel-Windows/dp/B07B416CPK)

# Hardware Setup
- Ensure that everything is powered off (german: ["Die 5 Sicherheitsregeln der Elektrotechnik"](https://www.medical-airport-service.de/arbeitssicherheit/die-5-sicherheitsregeln-der-elektrotechnik))
- Remove the cover from the Wallbox
- Connect the wire (I used RJ45/Cat6) with A/B pins at the right side of the board (IN). You should use one twisted pair
- Configure the Wallbox via Jumpers according to this manual: https://github.com/steff393/wbec (see chapter, "Switch configuration of wallbox
")
- Connect the wire with RS485/USB Adapter (A/B) which is plugged on your homeassistant hardware

# Software Setup
- Ensure you can access the DSD Tech Adapter via /dev/ttyUSB0 (Linux) or /dev/ttyU0 (Freebsd)
- Configure the modbus integration as specified in integration-modbus.yaml
- Add the modbus automation to ensure the wallbox does not show an error (a "heartbeat" command must be sent via modbus)

## Items
## Automation

# References
- Great project, https://github.com/steff393/wbec
- Homeassistant's Modbus documentation, https://www.home-assistant.io/integrations/modbus/
- 