# Core Headers

## What this shows

This file has the very basic headers every Butane file needs. The
`variant` field tells the transpiler this file is for Flatcar. The
`version` field states which spec version the file follows. The
`ignition` block shows how a config can pull in settings from another
file over the network, using `merge`.

Files here:
- `base-config.bu` > the source YAML file
- `base-config.json` > the converted Ignition file, made using the
  real `butane` transpiler
- `headers-test.png` > the proof of practice, where you can check my personal efforts how i successfully tranpile
