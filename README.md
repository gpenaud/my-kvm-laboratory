# KVM Laboratory spawner

### IMPORTANT
This is a pre-alpha software which has beel only tested on debian stretch and is probably very adherent to my own local host. This can heavily impact your network configuration, so don't come to cry if you meet critical problems after having used it.

Network files touched:
 - /etc/network/interfaces
 - /etc/network/interfaces.d/*
 - /etc/resolv.conf

All ansible playbooks will be executed on **localhost**

### OBJECTIVES

To spawn with dnsmasq and libvirt a whole local VM stack, fully configured with pre-defined IPs and name resolution, on isolated flat bridged network

### DOCUMENTATION

Please define your VMs and network desired topology in host_vars/localhost, then:

```
ansible-playbook -i inventory.yml site.yml
```

**libvirt role variables:**
- cluster_definition_directory: location of your xml libvirt definition files
- cluster_network: XML definition of the network used by your VMs
- cluster_vms: XML definitions of your VMs

**dns-proxy role variables:**
- dns_proxy_bridges: interfaces configures as interfaces and dnsmasq light dns-dhcp servers

by default, a "proxy" instance of dnsmasq proxifies dns query to bridge queries to the dnsmasq concerned instances
