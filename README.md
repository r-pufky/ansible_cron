# Cron
Manage cron units.

Manage cron units with a single call.

## Requirements
[supported platforms](https://github.com/r-pufky/ansible_cron/blob/main/meta/main.yml)

[collections/roles](https://github.com/r-pufky/ansible_cron/blob/main/meta/requirements.yml)

## Role Variables
[defaults](https://github.com/r-pufky/ansible_cron/blob/main/defaults/main)

## Dependencies
Part of the [r_pufky.srv](https://github.com/r-pufky/ansible_collection_srv)
collection.

## Example Playbook
Create and delete cron jobs. This will create a cronjob on every system that
runs the role. Use group vars to apply defaults to all managed systems.

group_vars/all/vars/cron.yml
```
cron_jobs:
  cron_present:
    special_time: 'daily'
    user: 'root'
    job: 'echo "cron job named cron_present"'
    state: 'present'
```

Apply the base role
``` yaml
- name: 'Manage cron jobs'
  ansible.builtin.include_role:
    name: 'r_pufky.srv.cron'
```

Install or remove cronjobs as part of another role
``` yaml
- name: 'Manage cron jobs'
  ansible.builtin.include_role:
    name: 'r_pufky.srv.cron'
  vars:
    cron_jobs:
      some_role_cronjob:
        special_time: 'daily'
        user: 'root'
        job: 'echo "cron job created for a role"'
        state: 'present'
      old_cronjob:
        state: 'absent'
```

## Development
Configure [environment](https://github.com/r-pufky/ansible_collection_srv/blob/main/docs/dev/environment/README.md)

Run all unit tests:
``` bash
molecule test --all
```

### Issues
Create a bug and provide as much information as possible.

Associate pull requests with a submitted bug.

## License
[AGPL-3.0 License](https://www.tldrlegal.com/license/gnu-affero-general-public-license-v3-agpl-3-0)
 [(direct link)](https://github.com/r-pufky/ansible_cron/blob/main/LICENSE)

## Author Information
PGP Fingerprint: [466EEC2B67516C7117C85CE3A0BC35D16698BAB9](https://keys.openpgp.org/vks/v1/by-fingerprint/466EEC2B67516C7117C85CE3A0BC35D16698BAB9)
| [github gist](https://gist.github.com/r-pufky/a8df36977c55b5bb20829267c4c49d22)
