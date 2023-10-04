
# Ansible Role:  `trivy` 

Ansible role to install and configure docker [trivy](https://github.com/distribution/distribution).

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
    - Debian 10 / 11
    - Ubuntu 20.10


## Contribution

Please read [Contribution](CONTRIBUTING.md)

## Development,  Branches (Git Tags)

The `master` Branch is my *Working Horse* includes the "latest, hot shit" and can be complete broken!

If you want to use something stable, please use a [Tagged Version](https://github.com/bodsch/ansible-trivy/tags)!

## Configuration

```yaml
trivy_version: 2.8.1

trivy_release_download_url: https://github.com/distribution/distribution/releases

trivy_system_user: trivy
trivy_system_group: trivy
trivy_config_dir: /etc/docker/trivy

trivy_direct_download: false

trivy_service: {}
trivy_log: {}
trivy_storage: {}
trivy_auth: {}
trivy_middleware: {}
trivy_reporting: {}
trivy_http: {}
trivy_notifications: {}
trivy_redis: {}
trivy_health: {}
trivy_proxy: {}
trivy_compatibility: {}
trivy_validation: {}
```

### `trivy_log`

[upstream doku](https://github.com/distribution/distribution/blob/main/docs/configuration.md#log)

```yaml
trivy_log:
  accesslog:
    disabled: true
  level: info
  formatter: text
  fields: {}
```

### `trivy_storage`

[upstream doku](https://github.com/distribution/distribution/blob/main/docs/configuration.md#storage)
```yaml
trivy_storage:
  filesystem:
    rootdirectory: /var/lib/trivy
    maxthreads: 100
  delete:
    enabled: false
  cache:
    blobdescriptorsize: 10000

```

### `trivy_auth`

[upstream doku](https://github.com/distribution/distribution/blob/main/docs/configuration.md#auth)
```yaml
trivy_auth: {}
```

### `trivy_middleware`

[upstream doku](https://github.com/distribution/distribution/blob/main/docs/configuration.md#middleware)
```yaml
trivy_middleware: {}
```

### `trivy_reporting`

[upstream doku](https://github.com/distribution/distribution/blob/main/docs/configuration.md#reporting)
```yaml
trivy_reporting: {}
```

### `trivy_http`

[upstream doku](https://github.com/distribution/distribution/blob/main/docs/configuration.md#http)
```yaml

trivy_http:
  addr: localhost:5000
  secret: "{{ ansible_host | b64encode }}"
  relativeurls: true
  debug:
    addr: localhost:5001
    prometheus:
      enabled: true
      path: /metrics
```

### `trivy_notifications`

[upstream doku](https://github.com/distribution/distribution/blob/main/docs/configuration.md#notifications)
```yaml
trivy_notifications: {}
```

### `trivy_redis`

[upstream doku](https://github.com/distribution/distribution/blob/main/docs/configuration.md#redis)
```yaml
trivy_redis: {}
```

### `trivy_health`

[upstream doku](https://github.com/distribution/distribution/blob/main/docs/configuration.md#health)
```yaml
trivy_health: {}
```

### `trivy_proxy`

[upstream doku](https://github.com/distribution/distribution/blob/main/docs/configuration.md#proxy)

```yaml
trivy_proxy: {}
```

### `trivy_compatibility`

[upstream doku](https://github.com/distribution/distribution/blob/main/docs/configuration.md#compatibility)
```yaml
trivy_compatibility: {}
```

### `trivy_validation`

[upstream doku](https://github.com/distribution/distribution/blob/main/docs/configuration.md#validation)
```yaml
trivy_validation: {}
```


---

## Author and License

- Bodo Schulz

## License

[Apache](LICENSE)

**FREE SOFTWARE, HELL YEAH!**
