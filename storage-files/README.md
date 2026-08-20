# Storage and Files

## What this shows

This shows how Butane creates an actual file on the machine before it
even boots. The `path` sets where the file goes, `mode` sets its
permissions, and `contents` writes text directly into it using the
inline block.

Files here:
- `storage-file.bu` > the source YAML file
- `storage-file.json` > the converted Ignition file, made using the
  real `butane` transpiler
- `storage-test.png` > the proof of practice, here you can check my personal efforts how i successfully tranpile
