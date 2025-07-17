<!-- DOCSIBLE START -->

# 📃 Role overview

## ansible-uptime-kuma



Description: Uptime Kuma


| Field                | Value           |
|--------------------- |-----------------|
| Readme update        | 18/07/2025 |








### Defaults

**These are static variables with lower priority**

#### File: defaults/main.yml

| Var          | Type         | Value       |
|--------------|--------------|-------------|
| [uptime_kuma_version](defaults/main.yml#L2)   | str | `1.23.6` |    
| [uptime_kuma_user](defaults/main.yml#L4)   | str | `kuma` |    
| [uptime_kuma_home](defaults/main.yml#L5)   | str | `/opt/{{ uptime_kuma_user }}` |    
| [uptime_kuma_src](defaults/main.yml#L7)   | str | `{{ uptime_kuma_home }}/uptime-kuma-{{ uptime_kuma_version }}` |    
| [uptime_kuma_data_dir](defaults/main.yml#L8)   | str | `{{ uptime_kuma_home }}/data` |    
| [uptime_kuma_backup_enabled](defaults/main.yml#L10)   | bool | `True` |    
| [uptime_kuma_backup_dir](defaults/main.yml#L11)   | str | `/var/backups/kuma` |    
| [uptime_kuma_backup_retention_days](defaults/main.yml#L12)   | int | `7` |    
| [uptime_kuma_backup_script](defaults/main.yml#L13)   | str | `kuma.backup.sh.j2` |    
| [uptime_kuma_env_vars](defaults/main.yml#L16)   | dict | `{}` |    
| [uptime_kuma_env_vars.**UPTIME_KUMA_HOST**](defaults/main.yml#L17)   | str | `127.0.0.1` |    
| [uptime_kuma_env_vars.**UPTIME_KUMA_PORT**](defaults/main.yml#L18)   | int | `3001` |    
| [uptime_kuma_env_vars.**DATA_DIR**](defaults/main.yml#L19)   | str | `{{ uptime_kuma_data_dir }}` |    





### Tasks


#### File: tasks/backup.yml

| Name | Module | Has Conditions |
| ---- | ------ | -------------- |
| Create backup dir | ansible.builtin.file | False |
| Deploy uptime-kuma backup script | ansible.builtin.template | False |
| Deploy uptime-kuma backup systemd unit | ansible.builtin.template | False |
| Deploy uptime-kuma backup timer unit | ansible.builtin.template | False |
| Enable a timer unit for uptime-kuma's backup | ansible.builtin.systemd_service | False |

#### File: tasks/install.yml

| Name | Module | Has Conditions |
| ---- | ------ | -------------- |
| Download uptime-kuma source archive to local folder | ansible.builtin.get_url | False |
| Unpack uptime-kuma src archive | ansible.builtin.unarchive | False |
| Download uptime-kuma dist archive to local folder | ansible.builtin.get_url | False |
| Unpack uptime-kuma dist archive | ansible.builtin.unarchive | False |
| Install NPM dependencies | community.general.npm | False |

#### File: tasks/main.yml

| Name | Module | Has Conditions |
| ---- | ------ | -------------- |
| Import prerequisites | ansible.builtin.import_tasks | False |
| Import install | ansible.builtin.import_tasks | False |
| Import service | ansible.builtin.import_tasks | False |
| Import backup | ansible.builtin.import_tasks | True |

#### File: tasks/prerequisites.yml

| Name | Module | Has Conditions |
| ---- | ------ | -------------- |
| Install node-related packages | ansible.builtin.apt | False |
| Create user {{ uptime_kuma_user }} | ansible.builtin.user | False |
| Create datadir | ansible.builtin.file | False |

#### File: tasks/service.yml

| Name | Module | Has Conditions |
| ---- | ------ | -------------- |
| Create systemd service unit | ansible.builtin.template | False |
| Enable and start uptime-kuma systemd unit | ansible.builtin.systemd | False |







## Author Information
FinweVI

#### License

MIT

#### Minimum Ansible Version

2.18

#### Platforms

- **Debian**: ['bookworm']
- ****: 


#### Dependencies

No dependencies specified.
<!-- DOCSIBLE END -->
