# butane-basics-practice
My step-by-step practical notes, YAML validation rules, and structural syntax blueprints for Flatcar Container Linux Butane configurations.
* **Goal:** To understand and write simple Butane YAML files to configure Flatcar OS before it boots.

---

## Strict YAML Rules (To keep your mind fresh and clean)

* **No Tabs:** Never use the Tab key. Always use the Spacebar.
* **2 Spaces Rule:** Move forward by exactly 2 spaces for every new sub-section.
* **Small Letters:** Always use lowercase letters for all keys and commands.
* **Colon Space (`: `):** Always put a space after the colon symbol.
* **Dash Space (`- `):** Always put a space after a list dash.
* **Pipe Symbol (`|`):** Use this symbol to write a big block of text on new lines.

---

## Core Commands and Simple Meanings

### Basic Headers & Internet Fetching
* `variant:` -> To show this file belongs to this OS (always `flatcar`).
* `version:` -> To declare the file specification version.
* `ignition:` -> To fetch settings from the internet or other networks.
* `config:` -> To avail more options in settings.
* `merge:` -> To add another online configuration file into this file.
* `replace:` -> To delete old settings and load a completely new file from a URL.

### Creating Files & Directories
* `storage:` -> Where files and drives will create.
* `files:` -> To create a new file list.
* `path:` -> To give the exact absolute folder destination of your file.
* `mode:` -> For file permissions to read, write, or execute.
* `overwrite:` -> To overwrite or delete an existing file at that path.
* `contents:` -> To write text or data inside your file.
* `inline:` -> To write short text directly inside the configuration file.
* `directories:` -> To create a new blank folder.
* `links:` -> To create a desktop shortcut (symlink) to another file.

### Setting Up Users & Security
* `passwd:` -> Main block to create and manage system user accounts.
* `users:` -> The list of new accounts you want to create.
* `name:` -> To set the login username (Flatcar's default admin user is `core`).
* `ssh_authorized_keys:` -> To paste your computer's SSH public key for secure login without a password.

---

## Automation & Background Services (`systemd:`) - Detailed Explanation

When you want your Flatcar node to run security scripts, capacity guards, or log scanners automatically in the background right after the system turns on, you use the `systemd:` block. Here is how its components work in detail:

* `systemd:` -> The main parent configuration block designed to manage and control all system services, background daemons, and automated boot tasks on Linux.
* `units:` -> A nested list container inside systemd where you declare each individual background service or startup application you want to build or modify.
* `name:` -> Specifies the exact identifier name for your service. A crucial rule in Linux is that this name must always end with a valid suffix, specifically `.service` (e.g., `alina-firewall.service`).
* `enabled:` -> A boolean switch (`true` or `false`). When set to `true`, it tells the operating system to automatically activate and start this background program every single time the machine boots up.

---

## What About the Extra Advanced Commands?

You do not need to use these everyday commands for basic practice, but they are good to know for big cloud infrastructure setups:

* **RAID & Disks (`disks:`, `partitions:`, `raid:`):** Used only when you connect multiple physical hard drives together to save data safely.
* **LUKS Encryption (`luks:`, `key_file:`):** Used to put a high-security lock and password on your hard disk so hackers cannot read it.
* **Directory Trees (`trees:`):** Used to copy a whole folder structure from your local computer into the server at once.
* **Kernel Customization (`kernel_arguments:`):** Used to change the deep engine settings of the Linux Operating System at boot time.

---

## Important Definitions

* **Flatcar Container Linux:** A tiny, highly secure operating system made only to run containers. Its main system is completely read-only.
* **Ignition:** The machine-readable JSON file that Flatcar reads to configure itself on its very first boot.
* **Transpiler:** The command-line tool that translates our easy Butane YAML file into the machine's Ignition JSON file.

---

> [!NOTE]
> **Quick Hint:** You can find file modes (like `0644` for regular files or `0755` for scripts) in standard Linux cheat sheets. All local file paths are relative to the folder you specify with the `--files-dir` flag in your terminal.
