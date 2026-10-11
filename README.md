OpenCode
========

Ansible role that installs [OpenCode](https://opencode.ai) on Linux, mirroring
the official installer (`https://opencode.ai/v2/install`):

* Installs the binary to `~/.opencode/bin/opencode` (the directory the
  built-in self-updater expects, so `opencode` can update itself).
* Optionally pins a specific version.
* Never modifies shell config files (equivalent of `--no-modify-path`).
* Uses the `linux-x64-baseline` build automatically on CPUs without AVX2.

Make sure `~/.opencode/bin` is on `PATH` yourself if needed.

Role Variables
--------------

| Variable               | Default             | Description                                        |
|------------------------|---------------------|----------------------------------------------------|
| `opencode_version`     | `""` (latest)       | Version to install, e.g. `2.0.21` (leading `v` OK) |
| `opencode_user`        | `root`              | User the binary is installed for/owned by          |
| `opencode_install_dir` | `~/.opencode/bin`   | Install directory (`~` expands to `opencode_user`) |

Example Playbook
----------------

```yaml
- hosts: all
  become: true
  roles:
    - role: carlosroman.opencode
      vars:
        opencode_version: "2.0.21"
```

Dev commands
------------

See `AGENTS.md` (`make lint`, `make test`, distro targets).

License
-------

MIT
