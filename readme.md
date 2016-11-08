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
```

### Install ntp service with custom stats option:

```
---

- hosts: all
  roles:
      - role: ntp
        ntp_stats_config:
            - 'statsdir  /var/lib/ntp/stats/'
            - 'driftfile /var/lib/ntp/ntp.drift'
            - 'filegen loopstats file loopstats type day enable'
            - 'filegen peerstats file peerstats type day enable'
            - 'filegen clockstats file clockstats type day enable'
            - 'sysstats file sysstats type day enable'

...
```



 NTP Stats configuration info
------------------------

### Important:
Create the /ntpstats directory at /var/log/ntpstats" owned by "ntp".

### Popular options are:
peerstats - Record peer statistics with one line appended to the peerstats file set each NTP packet or reference clock update
loopstats - Record clock discipline loop statistics . One line is appended to the loopstats file set each system clock update
clockstats - Record reference clock statistics with one line appended to the clockstats file set each update received from a reference clock driver
sysstats   - Record system statistics with one line appended to the sysstats file each hour

 License
---------

BSD

 Author
--------

 - Piotr Dobrysiak

