# LUKS Encryption

## What this shows

This locks an entire hard disk using encryption. Even if someone
physically removes the disk, they cannot read the data without the
correct key. This matters a lot for cybersecurity, since it protects
data even if the hardware itself is stolen. explaination you can see in my main README.md file

Files here:
- `luks-encryption.bu` > the source YAML file
- `luks-encryption.json` > the converted Ignition file, made using the
  real `butane` transpiler
- `luks-encryption-tets.png` > the proof of practice, where you can check my personal efforts how i successfully tranpile
