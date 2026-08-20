# Users and Security

## What this shows

This creates a user account on the machine and adds an SSH key to it,
so the machine can be logged into securely without needing a
password. Flatcar's default admin user is called `core`.

Files here:
- `core-user.bu` > the source YAML file
- `core-user.json` > the converted Ignition file, made using the
  real `butane` transpiler
- `core-user-test.png` > the proof of practice, here you can check my personal efforts how i successfully tranpile
