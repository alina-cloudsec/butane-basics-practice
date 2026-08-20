# Disks and RAID

## What this shows

This shows how Butane can set up hard disks on a new server. It picks
a physical disk, splits it into a partition, and joins multiple disks
together using RAID, so data stays safe even if one disk fails. explaination you can check in my main README.md file

Files here:
- `disks-raid.bu` > the source YAML file
- `disks-raid.json` > the converted Ignition file, made using the
  real `butane` transpiler
- `disks-raid-test.png` > the proof of practice, here you can check my personal efforts how i successfully tranpile
