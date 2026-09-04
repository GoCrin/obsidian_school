[nodered](https://nodered.org/)
[home assistant](https://www.home-assistant.io/)

# Installation von Home assistant

Es gibt viele Möglichkeiten Home assistant zu [installieren](https://www.home-assistant.io/installation/) hier wird es aber via docker installiert.

```bash
sudo docker run -it --network host homeassistant/home-assistant
```

# Verbindung zu ESP via MQTT

4xhits2526

admin user -> settings adcanced mode
settings -> intergrations
zertifikat validierung auf auto

(mqtt options) discovery prefix:  4xhits2526/\<unique\>
use a client cert: false

tasmota: mqtt topic: 4xhits2526/\<unique\>

button:

---

Andere wichtige Links:
[tasmota](https://github.com/arendst/Tasmota)
[tasmota supported devices](https://templates.blakadder.com/)