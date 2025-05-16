# Dockstream Smart Fountain (PLWF105)

The simplest way to configure and use this firmware is to define plwf105.yaml as the package import

```
packages:
  petlibro-esphome: github://taylorfinnell/petlibro-esphome/plwf105/plwf105.yaml@main
```

If you want to customize some values, you can use a extended package syntax and pass in variables

```
packages:
  petlibro-esphome:
    url: https://github.com/taylorfinnell/petlibro-esphome
    files:
      - path: plwf105/plwf105.yaml
        vars:
          hide_ml:  "true"
          timezone: "America/Los_Angeles"
```

If you want to customize the package, you can import the individual components as you wish.

For an example of a minimal fountain firmware. In this case, you would need to define the wifi and other basic components in addition to the fountain firmware

```
packages:
  petlibro-esphome:
    url: https://github.com/taylorfinnell/petlibro-esphome
    files:
      - path: plwf105/platform.yaml
      - path: plwf105/gpio.yaml
      - path: plwf105/lights.yaml
      - path: plwf105/pump.yaml
      - path: plwf105/water.yaml
```

The list of all files is included in the plwf105.yaml file. Files are laid out as 'features'. Later files may require earlier files. For example, calibrate_water.yaml requires the smart button and filter features for it to work correctly.
