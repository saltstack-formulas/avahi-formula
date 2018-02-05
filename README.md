# avahi

Salt formula to install and manage the configuration for the avahi daemon.

## avahi

Install avahi


## Operating in Container-based environments


When running `avahi-daemmon` within an unprivileged lxd container, it is necessary to avoid setting
rlimits.  To do this, you can add this to your pillar data:


```
avahi_config:
  rlimit-disable-all: True
```

You could also set a conditional on the salt grain `virtual` which would be equal to the value `LXC` as follows:

```
avahi_config:
{% if salt['grains.get']('virtual', '') == 'LXC' %}
  rlimit-disable-all: True
{% endif %}
```

