# Trees and Kernel Arguments

## What this shows

`trees` copies an entire folder from a local computer straight into
the Flatcar system, instead of writing out each file one at a time.
`kernel_arguments` talks directly to the Linux kernel the moment the
machine starts, to set deep, low level settings before anything else
even loads. expalination you can read in my main README,md file

Files here:
- `trees-kernel.bu` — the source YAML file
- `trees-kernel.json` — the converted Ignition file, made using the
  real `butane` transpiler
- `trees-kernel-test.png` — the proof of practice, here you can check my personal efforts how i successfully tranpile
