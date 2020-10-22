<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [ansible-frr](#ansible-frr)
  - [Build Status](#build-status)
    - [GitHub Actions](#github-actions)
    - [Travis CI](#travis-ci)
  - [Requirements](#requirements)
  - [Role Variables](#role-variables)
  - [Dependencies](#dependencies)
  - [Example Playbook](#example-playbook)
  - [Route Maps and Prefix Lists](#route-maps-and-prefix-lists)
    - [Route Maps](#route-maps)
      - [Configuring Route Maps](#configuring-route-maps)
    - [General Options](#general-options)
      - [IP/IPv6 Forwarding](#ipipv6-forwarding)
    - [Prefix Lists](#prefix-lists)
      - [Configuring Prefix Lists](#configuring-prefix-lists)
    - [Access Lists](#access-lists)
      - [Configuring Access Lists](#configuring-access-lists)
  - [Supported Routing Protocols](#supported-routing-protocols)
    - [BGP](#bgp)
      - [Enable BGP](#enable-bgp)
      - [Configuring BGP](#configuring-bgp)
      - [Example BGP](#example-bgp)
    - [OSPF](#ospf)
      - [Enable OSPF](#enable-ospf)
      - [Configuring OSPF](#configuring-ospf)
    - [STATIC](#static)
      - [Configuring STATIC routes](#configuring-static-routes)
  - [Interface Configuration](#interface-configuration)
    - [Interfaces](#interfaces)
  - [Upgrade/Downgrade](#upgradedowngrade)
  - [Quagga configuration](#quagga-configuration)
  - [License](#license)
  - [Author Information](#author-information)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# ansible-frr

Ansible role to install/configure FRR

> NOTE: FRRouting (FRR) is an IP routing protocol suite for Linux and Unix
> platforms which includes protocol daemons for BGP, IS-IS, LDP, OSPF, PIM, and RIP.

## Build Status

### GitHub Actions

![Molecule Test](https://github.com/mrlesmithjr/ansible-frr/workflows/Molecule%20Test/badge.svg)

### Travis CI

[![Build Status](https://travis-ci.org/mrlesmithjr/ansible-frr.svg?branch=master)](https://travis-ci.org/mrlesmithjr/ansible-frr)

## Requirements

For any required Ansible roles, review:
[requirements.yml](requirements.yml)

## Role Variables

[defaults/main.yml](defaults/main.yml)

## Dependencies

## Example Playbook

[playbook.yml](playbook.yml)

## Route Maps and Prefix Lists

### Route Maps

#### Configuring Route Maps

Below is an example of Route Maps Configuration:

```yaml
frr_route_map:
  RTBH:
    permit 10:
      interface: blackhole
      prefix_list: Bad_IPs
      origin: igp
      community: "12345:100"
  RTBH_IN:
    deny 10: []
```

### General Options

#### IP/IPv6 Forwarding

Below is an example of enabling ip and ipv6 forwading:

```yaml
frr_ip_forwarding: true
frr_ipv6_forwarding: true
```

### Prefix Lists

#### Configuring Prefix Lists

Below is an example of Prefix List Configuration:

```yaml
frr_prefix_list:
  Bad_IPs:
    05 permit:
      prefix: 192.168.88.0/24
      match: ge 32
    10 permit:
      prefix: 172.16.0.0/16
      match: le 32
frr_prefix_list_v6:
  Bad_IPs:
    05 permit:
      prefix: 1234:5678::/32
      match: ge 128
```

### Access Lists

#### Configuring Access Lists

Below is an example

```yaml
frr_access_list:
  - "10 permit 10.10.10.21/32"
  - "10 permit 192.168.0.0/17"
  - "101 permit ip 10.0.0.0 0.0.0.255 any"
```

## Supported Routing Protocols

| Protocol          | Implemented | Notes               |
| ----------------- | ----------- | ------------------- |
| [BGP](#bgp)       | X           | Only initial config |
| [OSPF](#ospf)     | X           | Only initial config |
| [STATIC](#static) | X           | Only initial config |

### BGP

#### Enable BGP

To enable BGP routing, make sure that `bgpd: true` is configured under:

```yaml
frr_daemons:
  bgpd: false
  isisd: false
  ldpd: false
  nhrpd: false
  ospf6d: false
  ospfd: false
  pimd: false
  ripd: false
  ripngd: false
  zebra: true
```

#### Configuring BGP

In order to configure BGP, define the following based on your requirements:

```yaml
frr_bgp:
  asns:
    65000:
      log_neighbor_changes: true
      timers: '3 9'
      other:
        - "bgp bestpath as-path multipath-relax"
      neighbors:
        group1:
          asn: 66000
          is_peer_group: true
          multihop: 255
        192.168.250.11:
          asn: 65000
          default_originate: false
          description: node1
          next_hop_self: true
          timers_connect: 5
          v6only: true
          other:
            - "capability dynamic"
        192.168.250.12:
          asn: 65000
          default_originate: false
          description: node2
          next_hop_self: true
          v4_route_reflector_client: true
          password: secret
        192.168.250.12:
          peer_group: group1
          description: far_away
      networks:
        - "{{ frr_router_id }}/32"
        - "{{ hostvars[inventory_hostname]['ansible_enp0s8']['ipv4']['address'] }}/24"
      redistribute:
        - bgp
        - connected
        - kernel
        - ospf
        - static
      redistribute_v6:
        - bgp
        - connected
        - kernel
```

#### Example BGP

Below is an example of a BGP configuration:

```yaml
frr_bgp:
  asns:
    65000:
      log_neighbor_changes: true
      af_v4:
        - "maximum-paths 2"
      af_v6:
        - "maximum-paths 2"
      neighbors:
        192.168.250.11:
          asn: 65000
          default_originate: false
          description: node1
          next_hop_self: true
          af_v4:
            - "soft-reconfiguration inbound"
        192.168.250.12:
          asn: 65000
          default_originate: false
          description: node2
          next_hop_self: true
        "::1":
          asn: 65000
          default_originate: false
          description: node1
          next_hop_self: true
          af_v6:
            - "activate"
            - "soft-reconfiguration inbound"
      networks:
        - "{{ frr_router_id }}/32"
        - "{{ hostvars[inventory_hostname]['ansible_enp0s8']['ipv4']['address'] }}/24"
        - "{{ hostvars[inventory_hostname]['ansible_enp0s9']['ipv4']['address'] }}/24"
        - "{{ hostvars[inventory_hostname]['ansible_enp0s10']['ipv4']['address'] }}/24"
        - "{{ hostvars[inventory_hostname]['ansible_enp0s16']['ipv4']['address'] }}/24"
      networks_v6:
        - "1::3/64"
```

Below is an example of a BGP summary based on the above configuration:

```bash
BGP table version is 13, local router ID is 1.1.1.1
Status codes: s suppressed, d damped, h history, * valid, > best, = multipath,
              i internal, r RIB-failure, S Stale, R Removed
Origin codes: i - IGP, e - EGP, ? - incomplete

   Network          Next Hop            Metric LocPrf Weight Path
*> 1.1.1.1/32       0.0.0.0                  0         32768 i
*>i2.2.2.2/32       192.168.250.11           0    100      0 i
*>i3.3.3.3/32       192.168.250.12           0    100      0 i
*> 192.168.10.0     0.0.0.0                  0         32768 i
*>i192.168.11.0     192.168.250.11           0    100      0 i
*>i192.168.12.0     192.168.250.12           0    100      0 i
*> 192.168.20.0     0.0.0.0                  0         32768 i
*>i192.168.21.0     192.168.250.11           0    100      0 i
*>i192.168.22.0     192.168.250.12           0    100      0 i
*> 192.168.30.0     0.0.0.0                  0         32768 i
*>i192.168.31.0     192.168.250.11           0    100      0 i
*>i192.168.32.0     192.168.250.12           0    100      0 i
* i192.168.250.0    192.168.250.11           0    100      0 i
* i                 192.168.250.12           0    100      0 i
*>                  0.0.0.0                  0         32768 i

Displayed  13 routes and 15 total paths
```

### OSPF

#### Enable OSPF

To enable OSPF routing, make sure that `ospfd: true` is configured under:

```yaml
frr_daemons:
  bgpd: false
  isisd: false
  ldpd: false
  nhrpd: false
  ospf6d: false
  ospfd: false
  pimd: false
  ripd: false
  ripngd: false
  zebra: true
```

#### Configuring OSPF

In order to configure OSPF, define the following based on your requirements:

```yaml
frr_ospf:
  areas:
    0:
      networks:
        - "{{ frr_router_id }}/32"
    1:
      networks:
        - "{{ hostvars[inventory_hostname]['ansible_enp0s8']['ipv4']['address'] }}/24"
      auth: true

    2:
      networks:
        - "{{ hostvars[inventory_hostname]['ansible_enp0s9']['ipv4']['address'] }}/24"
      type: nssa

  log_adjacency_changes: true
  passive_interfaces: # A list of interfaces to set passive
    - default
  redistribute: # A list of protocols to redistribute
    - bgp
    - connected
    - kernel
    - ospf
    - static
  distribute_list:
    - name: 10
      dir: out
      protocol: connected
```

### STATIC

#### Configuring STATIC routes

In order to configure static routes, define the following based on your requirements:

```yaml
frr_static: # A dict. key = destination, value = nexthop
  10.0.0.0/8: 192.168.1.1
  1.1.1.1: 192.168.1.1
  1.1.1.2: blackhole
frr_static_v6: # A dict. key = destination, value = nexthop
  2001:0db8:85a3:8a2e::/64 2001::1
```

## Interface Configuration

### Interfaces

```yaml
frr_interfaces: # A dict. key = iface name, value = iface data
  lo:
    ip: 10.0.0.0/32 # ip can be a single value or list
    ipv6: 2001:0db8:85a3:8a2e::1/64 # ipv6 can be a single value or list
    description: loopback
  eth0:
    ip: # ip can be a single value or list
      - 10.0.0.0/32
      - 172.16.0.0/32
    ipv6: # ipv6 can be a single value or list
      - 2001:0db8:85a3:8a2e::1/64
      - 2001:0db8:85a3:8a2e::2/64
    auth:
      id: 1
      key: supersecret
    other:
      - "no ipv6 nd suppress-ra"
      - "link-detect"
```

## Upgrade/Downgrade

> NOTE: FRR is unable to be downgraded from 6.0.2 using this role.

You can upgrade or downgrade FRR by setting the following variable:

`frr_version: 6.0.2` from `frr_version: 6.0`

## Quagga configuration

> NOTE: Quagga must be installed from the local repos of the OS

You can configure quagga instead of FRR by using the following variable:

`routing_type: quagga`

> Additional Quagga-specific configurations

```bash
frr_bgp:
  asns:
    65000:
      neighbors:
        swp1:
          **interface: true**
```

## License

MIT

## Author Information

Larry Smith Jr.

- [@mrlesmithjr](https://twitter.com/mrlesmithjr)
- [mrlesmithjr@gmail.com](mailto:mrlesmithjr@gmail.com)
- [http://everythingshouldbevirtual.com](http://everythingshouldbevirtual.com)

> NOTE: Repo has been created/updated using [https://github.com/mrlesmithjr/cookiecutter-ansible-role](https://github.com/mrlesmithjr/cookiecutter-ansible-role) as a template.
