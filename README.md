
# Ansible Role:  `trivy` 

Ansible role to install [trivy](https://github.com/aquasecurity/trivy).

[![GitHub Workflow Status](https://img.shields.io/github/actions/workflow/status/bodsch/ansible-trivy/main.yml?branch=main)][ci]
[![GitHub issues](https://img.shields.io/github/issues/bodsch/ansible-trivy)][issues]
[![GitHub release (latest by date)](https://img.shields.io/github/v/release/bodsch/ansible-trivy)][releases]
[![Ansible Quality Score](https://img.shields.io/ansible/quality/50067?label=role%20quality)][quality]

[ci]: https://github.com/bodsch/ansible-trivy/actions
[issues]: https://github.com/bodsch/ansible-trivy/issues?q=is%3Aopen+is%3Aissue
[releases]: https://github.com/bodsch/ansible-trivy/releases
[quality]: https://galaxy.ansible.com/bodsch/trivy

If `latest` is set for `trivy_version`, the role tries to install the latest release version.  
**Please use this with caution, as incompatibilities between releases may occur!**

The binaries are installed below `/usr/local/bin/trivy/${trivy_version}` and later linked to `/usr/bin`. 
This should make it possible to downgrade relatively safely.

The downloaded archive is stored on the Ansible controller, unpacked and then the binaries are copied to the target system.
The cache directory can be defined via the environment variable `CUSTOM_LOCAL_TMP_DIRECTORY`. 
By default it is `${HOME}/.cache/ansible/trivy`.
If this type of installation is not desired, the download can take place directly on the target system. 
However, this must be explicitly activated by setting `trivy_direct_download` to `true`.

## Requirements & Dependencies

Ansible Collections

- [bodsch.core](https://github.com/bodsch/ansible-collection-core)
- [bodsch.scm](https://github.com/bodsch/ansible-collection-scm)

```bash
ansible-galaxy collection install bodsch.core
ansible-galaxy collection install bodsch.scm
```
or
```bash
ansible-galaxy collection install --requirements-file collections.yml
```

## Operating systems

Tested on

* Arch Linux
* Debian based
    - Debian 10 / 11 / 12
    - Ubuntu 20.10 / 22.04


## Contribution

Please read [Contribution](CONTRIBUTING.md)

## Development,  Branches (Git Tags)

The `master` Branch is my *Working Horse* includes the "latest, hot shit" and can be complete broken!

If you want to use something stable, please use a [Tagged Version](https://github.com/bodsch/ansible-trivy/tags)!

## Configuration

```yaml
trivy_version: 0.45.1

trivy_direct_download: false

trivy_release: {}
```

---

## Author and License

- Bodo Schulz

## License

[Apache](LICENSE)

**FREE SOFTWARE, HELL YEAH!**
