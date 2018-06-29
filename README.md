#### Ansible systemd_mount

This Ansible role configures systemd mount files.

This role requires the ``openstack-ansible-plugins`` repository to be available
on your local system. The Ansible galaxy resolver will not retrieve this role
for you. To get the plugins role in place clone the plugins repository
**before** running this role.

``` bash
# git clone https://github.com/openstack/openstack-ansible-plugins /etc/ansible/roles/plugins
```

You can also use the ``ansible-galaxy`` command on the ``ansible-role-requirements.yml`` file.

``` bash
# ansible-galaxy install -r ansible-role-requirements.yml
```
Release notes for the project can be found at:
  https://docs.openstack.org/releasenotes/ansible-role-systemd_mount

----

###### Example playbook

> See the "defaults.yml" file for a full list of all available options.

``` yaml
- name: Create a systemd mount file for Mount1 and 2
  hosts: localhost
  become: true
  roles:
    - role: "systemd_mount"
      systemd_mounts:
        - what: '/var/lib/machines.raw'
          where: '/var/lib/machines'
          type: 'btrfs'
          options: 'loop'
          unit:
            ConditionPathExists:
              - '/var/lib/machines.raw'
          state: 'started'
          enabled: true
        - config_overrides: {}
          what: "10.1.10.1:/srv/nfs"
          where: "/var/lib/glance/images"
          type: "nfs"
          options: "_netdev,auto"
          unit:
            After:
              - network.target
```
