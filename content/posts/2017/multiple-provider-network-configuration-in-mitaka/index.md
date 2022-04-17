---
title: "Multiple Provider Network Configuration in Mitaka"
date: 2017-02-23
draft: false
authors: ["jiasir"]
categories: ["2017"]
series: ["OpenStack"]
tags: ["OpenStack"]
description: "Neutron provider VLANs are Neutron networks that map directly to an 802.1Q VLAN in the cloud provider’s physical network infrastructure."
---

Neutron provider VLANs are Neutron networks that map directly to an 802.1Q VLAN in the cloud provider's physical network infrastructure.

This is the example configuration of neutron network node:

On the `neutron.conf` file:
```
[DEFAULT]
core_plugin = ml2
service_plugins = router
```

On the `ml2_conf.ini` file:
```
[ml2]
type_drivers = flat,vlan,vxlan
tenant_network_types = vxlan
mechanism_drivers = linuxbridge,l2population
extension_drivers = port_security
[ml2_type_flat]
flat_networks = provider
[ml2_type_vlan]
network_vlan_ranges = provider
[securitygroup]
firewall_driver = iptables
```

We also need to configure the physical switches as trunk not access mode:
```
interface GigabitEthernet1/0/12
    description Trunk to Compute Node
    spanning-tree portfast trunk
    switchport trunk encapsulation dot1q
    switchport mode trunk
    switchport trunk native vlan 1
    switchport trunk allowed vlan 1,110,111
```

The physical network infrastructure must be configured to convey the provider VLAN traffic as tagged VLANs to the cloud compute nodes and neutron network nodes.
