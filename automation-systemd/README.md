# Automation with systemd

## What this shows

This sets up a background service that starts automatically the
moment the machine boots up, using systemd. The `name` must end in
`.service`, and `enabled: true` makes sure it runs on every boot,
without anyone needing to start it manually. Explaination you can check in main readme.md file

Files here:
- `background-service.bu` > the source YAML file
- `background-service.json` > the converted Ignition file, made using
  the real `butane` transpiler
- `background-service-test.png` > the proof of practice, here you can check my personal efforts how i successfully tranpile
