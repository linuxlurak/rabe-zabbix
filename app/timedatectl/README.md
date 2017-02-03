# timedatectl

High level monitoring for time and date keeping based on the backend agnostic timedatectl command.

* [Template App timedatectl active](Template_App_timedatectl_active.xml)
* [timedatectl.conf](./userparameters/timedatectl.conf)
* [SELinux policy module rabetimedatectl](selinux/rabetimedatectl.te)

This template is part of [RaBe's Zabbix template and helpers
collection](https://github.com/radiorabe/rabe-zabbix).

## Template

### Items

* NTP enabled (rabe.timedatectl.ntp.enabled)
* NTP synchronized (rabe.timedatectl.ntp.synchronized)

### Triggers

* Warning: NTP not enabled
* Warning: NTP not synchronized for more than {$TIMEDATECTL_MAX_NO_SYNC_TIME}
* Information: NTP not synchronized

### Macros

* `{$TIMEDATECTL_MAX_NO_SYNC_TIME}`
  
   Time to wait before triggering a not synchronized WARNING trigger (60m by default)

## UserParameters

| Key | Description |
| --- | ----------- |
| `rabe.timedatectl.ntp.enabled` | "NTP enabled" yes/no value from `timedatectl status` output |
| `rabe.timedatectl.ntp.synchronized` | "NTP synchonized" yes/no value from `timedatectl status` output |

## SELinux Policy

The [rabetimedatectl](selinux/rabetimedatectl.te) policy module allows the agent to connect to dbus and lets
it request info from the timedated service. It also allows answers from the timedated service to the agent.

## License
This template is free software: you can redistribute it and/or modify it under
the terms of the GNU Affero General Public License as published by the Free
Software Foundation, version 3 of the License.

## Copyright
Copyright (c) 2017 [Radio Bern RaBe](http://www.rabe.ch)
