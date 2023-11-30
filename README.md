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
    key: "CHANGEME"
ota:
  password: "CHANGEME"

wifi:
  ssid: !secret wifi_ssid
  password: !secret wifi_password
  ap:
    password: "VdkpvVWmbuu0"

dashboard_import:
  package_import_url: github://taylorfinnell/petlibro-esphome/plwf105/plwf105.yaml@master
  import_full_config: true
```

### PLAF108 (Airstream Feeder)

TODO


