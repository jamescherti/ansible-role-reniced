# ansible-role-reniced

The [ansible-role-reniced](https://github.com/jamescherti/ansible-role-reniced) Ansible role configures `reniced` on Debian and Ubuntu based operating systems.

## Customizations

When `reniced_conf` is defined, it is used as the configuration content.

Include the role using:
```yaml
- name: Import role reniced
  when: ansible_os_family == "Debian"
  ansible.builtin.import_role:
    name: reniced
```

Variables:
```yaml
reniced_conf: |
  # high prio network services
  0 ^apache
  0 ^nfsd
  0 ^ntpd
  0 ^openvpn
  0 ^portmap
  0 ^ppp
  0 ^rpc.
  0 ^sshd

  # medium prio network services
  5 ^inn$
  5 ^mysqld

  # low prio network services
  15i ^amavisd-new
  15i ^clamd
  15 ^controlchan
  15 ^exim4
  15 ^freshclam
  15 ^innwatch
  12 ^mailman
  15 ^rc.news
  15i ^spamd

  # long running user processes (screen)
  3 ^irssi

  # test OOM settings
  o1 bash
```

## Author and license

Copyright (C) 2024-2025 [James Cherti](https://www.jamescherti.com).

Distributed under terms of the MIT license.

## Links

- [ansible-role-reniced @GitHub](https://github.com/jamescherti/ansible-role-reniced)
