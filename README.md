# Butane Basics Practice Notes
My step-by-step practical notes, YAML validation rules, and structural syntax blueprints for Flatcar Container Linux Butane configurations.
**Goal:** To understand and write simple Butane YAML files that
configure Flatcar OS before it even boots up.

---

## Strict YAML Rules

These rules keep a Butane file clean and working correctly.

- **No tabs.** Always use the space bar, never the Tab key.
- **Two space rule.** Move forward exactly two spaces for every new
  sub section.
- **Small letters.** Always use lowercase letters for keys and
  commands.
- **Colon space.** Always put a space after a colon symbol.
- **Dash space.** Always put a space after a list dash.
- **Pipe symbol.** Use `|` to write a big block of text across
  multiple lines.

---

## Core Commands and What They Mean

### Basic headers and fetching settings

- `variant:` — Shows which operating system this file is for. Always
  `flatcar` in this case.
- `version:` — States which version of the file format is being used.
- `ignition:` — Used to fetch extra settings from the internet or
  another network location.
- `config:` — Opens up more options inside the settings.
- `merge:` — Adds another online configuration file into this one.
- `replace:` — Deletes the old settings completely and loads a brand
  new file from a URL instead.

### Creating files and folders

- `storage:` — The main place where files and drives get created.
- `files:` — Starts a list of new files to create.
- `path:` — The exact folder location where the file should go.
- `mode:` — Sets file permissions, like read, write, or execute.
- `overwrite:` — Overwrites or deletes an existing file at that path.
- `contents:` — The actual text or data written inside the file.
- `inline:` — Writes short text directly inside the config file
  itself.
- `directories:` — Creates a new empty folder.
- `links:` — Creates a shortcut, called a symlink, pointing to
  another file.

### Setting up users and security

- `passwd:` — The main block used to create and manage user accounts
  on the system.
- `users:` — The list of new accounts to create.
- `name:` — Sets the login username. Flatcar's default admin user is
  called `core`.
- `ssh_authorized_keys:` — Where you paste your SSH public key, so you
  can log in securely without needing a password.

---

## Automation with systemd

When you want a Flatcar server to run something automatically in the
background right after it turns on, like a security script or a log
scanner, you use the `systemd:` block.

- `systemd:` — The main block that manages and controls all
  background services and startup tasks on Linux.
- `units:` — A list inside systemd where each background service is
  defined, one at a time.
- `name:` — The exact name of the service. In Linux, this name must
  always end in `.service`, for example `alina-firewall.service`.
- `enabled:` — Set to `true` or `false`. When set to `true`, the
  service starts automatically every single time the machine boots
  up.

---

## Advanced Commands

These are not needed for everyday practice, but they matter a lot in
real cloud infrastructure. Here is what each one actually does, and
why it exists.

### 1. `disks:`, `partitions:`, and `raid:` — splitting and joining hard disks

When you set up a new server in the cloud, it often comes with more
than one empty hard disk attached to it.

- `disks:` tells the computer exactly which physical disk to work on,
  for example `/dev/sda`.
- `partitions:` splits that disk into smaller sections. For example,
  you could create a separate 10GB partition just for a database.
- `raid:` is used when you have three or four hard disks, and you
  want your data to stay safe even if one disk fails or burns out.
  RAID joins all those disks together into one, and keeps
  automatically copying the data across them, so nothing is lost if
  one disk dies.

### 2. `luks:` and `key_file:` — locking and encrypting a hard disk

This one matters a lot for cybersecurity. Imagine a hacker breaks
into a data center and physically removes your server's hard disk. If
that disk is not encrypted, they can just read everything on it
directly.

`luks:` is the standard Linux system that locks an entire hard disk
using encryption. When the computer boots up, the disk stays locked
until the correct `key_file:`, which works like a password, is
provided. This key does not have to sit on the machine itself. Butane
can even fetch it securely from the internet or from a separate secure
server.

### 3. `trees:` — copying a whole folder at once

Earlier, under `storage:` and `files:`, each file has to be written
out one at a time, with its own path and contents. But imagine your
laptop already has a folder with a hundred security configuration
files sitting in it. Writing each one out by hand would take forever.

`trees:` solves this. It tells Butane to take an entire folder from
your local computer and copy it directly into the Flatcar system,
without needing to define every single file separately. What would
take hours by hand takes seconds with this command.

### 4. `kernel_arguments:` — giving direct settings to the OS engine

The kernel is the core engine of a Linux operating system. The very
first time a computer boots up, before any regular software even
starts running, the hardware loads its settings through the kernel.

`kernel_arguments:` lets you speak directly to the kernel the moment
the system starts, saying things like "keep this hardware feature
turned off" or "set security to a stricter level." These are deep,
operating system level settings that cannot be controlled through
normal software scripts.

---

## Important Definitions

- **Flatcar Container Linux** — A small, highly secure operating
  system built only to run containers. Its core system stays
  completely read only.
- **Ignition** — The machine readable JSON file that Flatcar actually
  reads to configure itself the very first time it boots.
- **Transpiler** — The command line tool that translates an easy
  Butane YAML file into the machine's Ignition JSON file.

---

> **Quick hint:** File modes, like `0644` for regular files or `0755`
> for scripts, can be found in any standard Linux cheat sheet. All
> local file paths are relative to the folder set using the
> `--files-dir` flag in the terminal.
