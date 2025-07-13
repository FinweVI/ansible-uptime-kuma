# Ansible Role: uptime-kuma

Provision and manage [Uptime Kuma](https://github.com/louislam/uptime-kuma) - Self-Hosted monitoring system

## Requirements

- Ansible >= 2.18

## Role Variables

All variables which can be overridden are stored in [defaults/main.yml](defaults/main.yml) file as well as in table below.

| Name           | Default Value | Description                        |
| -------------- | ------------- | -----------------------------------|
| `uptime_kuma_version` | 1.23.6 | Uptime Kuma version to install |
| `uptime_kuma_user` | kuma | User to run the daemon with |
| `uptime_kuma_home` | /opt/kuma | Home of the user (for SRC and DATA dirs) |
| `uptime_kuma_src` | /opt/kuma/uptime-kuma-1.23.6 | Source Directory for uptime Kuma |
| `uptime_kuma_config_dir` | /etc/uptime-kuma | Directory for Uptime Kuma configurations through ENVs |
| `uptime_kuma_config_file` | /etc/uptime-kuma/kuma.conf | Path of the configuration file |
| `uptime_kuma_env_vars` | {} | Dictionnary of ENVs Vars to pass to the daemon |

See the [defaults/main.yml](defaults/main.yml) file for examples.


## Notes

It's Debian-based Only.
It must be possible to make it CentOS (or any other linux-based OS) compatible.
Issues & PR are welcome for any improvement ;-)
