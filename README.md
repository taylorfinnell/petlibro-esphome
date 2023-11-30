# petlibro-esphome

A collection of esphome  firmwares for Petlibro devices.


## Example configs

### PLWF105 (Dockstream Fountain)

```
packages:
  remote_package:
    url: https://github.com/taylorfinnell/petlibro-esphome
    files: ['plwf105/plwf105.yaml']
    refresh: 1s

substitutions:
  name: mia-water-bowl
  friendly_name: Mia Water Bowl

logger:

api:
  encryption:
    key: rgRQfQg/fzDuQnihMjGIABBk+JV1ARRi2d1E55UvNd0=
ota:
  password: "956eb0b4d05f51380a1829eae220cdc0"

wifi:
  ssid: !secret wifi_ssid
  password: !secret wifi_password
  manual_ip:
    static_ip: 192.168.30.222
    gateway: 192.168.30.1
    subnet: 255.255.255.0
  ap:
    ssid: "Mia-Water-Bowl Fallback Hotspot"
    password: "VdkpvVWmbuu0"

captive_portal:

dashboard_import:
  package_import_url: github://taylorfinnell/petlibro-esphome/plwf105/plwf105.yaml@master
  import_full_config: true
```

### PLAF108 (Airstream Feeder)

TODO


