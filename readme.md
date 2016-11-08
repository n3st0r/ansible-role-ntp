 role-ntp
=========

My own ansible role for install and configure ntp/ntpd service role.

 Examples
----------

### Install ntp and start ntp service.

```
---

- hosts: all
  roles:
      - role: ntp

...
```

### Install ntp service with custom servers:

```
---

- hosts: all
  roles:
      - role: ntp
        ntp_config_server:
            - 0.my.ntp.server
            - 1.my.ntp.server

...
```

### Install ntp service with custom servers and own restricted networks:

```
---

- hosts: all
  roles:
      - role: ntp
        ntp_config_server:
            - 0.my.ntp.server
            - 1.my.ntp.server
        ntp_config_restrict:
            - -4 default kod notrap nomodify nopeer noquery
            - 192.168.0.0/24 trust

...

 License
---------

BSD

 Author
--------

 - Piotr Dobrysiak

