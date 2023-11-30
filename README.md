# petlibro-esphome

A collection of esphome  firmwares for Petlibro devices.


## Example configs

### PLWF105 (Dockstream Fountain)

```
packages:
  remote_package:
    url: https://github.com/taylorfinnell/petlibro-esphome
    ref: master
    files: ['plwf105/plwf105.yaml']
    refresh: 1s

substitutions:
  name: mia-water-bowl
  friendly_name: Mia Water Bowl
  
api:
  encryption:
    key: "CHANGEME"
ota:
  password: "CHANGEME"

wifi:
  ssid: !secret wifi_ssid
  password: !secret wifi_password
  manual_ip:
    static_ip: 192.168.30.15
    gateway: 192.168.30.1
    subnet: 255.255.255.0
  ap:
    password: "CHANGEME"
```

### PLAF108 (Airstream Feeder)

TODO


