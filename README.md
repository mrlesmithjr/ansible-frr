<!-- START doctoc generated TOC please keep comment here to allow auto update -->

<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

-   [ansible-frr](#ansible-frr)
    -   [Requirements](#requirements)
    -   [Role Variables](#role-variables)
    -   [Dependencies](#dependencies)
    -   [Example Playbook](#example-playbook)
    -   [Supported Routing Protocols](#supported-routing-protocols)
        -   [BGP](#bgp)
            -   [Enable BGP](#enable-bgp)
            -   [Configuring BGP](#configuring-bgp)
            -   [Example BGP](#example-bgp)
        -   [OSPF](#ospf)
            -   [Enable OSPF](#enable-ospf)
            -   [Configuring OSPF](#configuring-ospf)
    -   [License](#license)
    -   [Author Information](#author-information)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# ansible-frr

An [Ansible](https://www.ansible.com) role to install/configure [FRR](https://frrouting.org/)

> NOTE: FRRouting (FRR) is an IP routing protocol suite for Linux and Unix
> platforms which includes protocol daemons for BGP, IS-IS, LDP, OSPF, PIM, and RIP.

## Requirements

## Role Variables

[defaults/main.yml](defaults/main.yml)

## Dependencies

## Example Playbook

## Supported Routing Protocols

| Protocol      | Implemented | Notes               |
| ------------- | ----------- | ------------------- |
| [BGP](#bgp)   | X           | Only initial config |
| [OSPF](#ospf) | X           | Only initial config |

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
frr_bgp: []
  # asns:
  #   65000:
  #     log_neighbor_changes: true
  #     neighbors:
  #       192.168.250.11:
  #         asn: 65000
  #         default_originate: false
  #         description: node1
  #         next_hop_self: true
  #       192.168.250.12:
  #         asn: 65000
  #         default_originate: false
  #         description: node2
  #         next_hop_self: true
  #     networks:
  #       - "{{ frr_router_id }}/32"
  #       - "{{ hostvars[inventory_hostname]['ansible_enp0s8']['ipv4']['address'] }}/24"
  #     redistribute: []
  #       # - bgp
  #       # - connected
  #       # - kernel
  #       # - ospf
  #       # - static
```

#### Example BGP

Below is an example of a BGP configuration:

```yaml
frr_bgp:
  asns:
    65000:
      log_neighbor_changes: true
      neighbors:
        192.168.250.11:
          asn: 65000
          default_originate: false
          description: node1
          next_hop_self: true
        192.168.250.12:
          asn: 65000
          default_originate: false
          description: node2
          next_hop_self: true
      networks:
        - "{{ frr_router_id }}/32"
        - "{{ hostvars[inventory_hostname]['ansible_enp0s8']['ipv4']['address'] }}/24"
        - "{{ hostvars[inventory_hostname]['ansible_enp0s9']['ipv4']['address'] }}/24"
        - "{{ hostvars[inventory_hostname]['ansible_enp0s10']['ipv4']['address'] }}/24"
        - "{{ hostvars[inventory_hostname]['ansible_enp0s16']['ipv4']['address'] }}/24"
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
frr_ospf: []
  # areas:
  #   0:
  #     networks:
  #       - "{{ frr_router_id }}/32"
  #   1:
  #     networks:
  #       - "{{ hostvars[inventory_hostname]['ansible_enp0s8']['ipv4']['address'] }}/24"
  #   2:
  #     networks:
  #       - "{{ hostvars[inventory_hostname]['ansible_enp0s9']['ipv4']['address'] }}/24"
  # log_adjacency_changes: true
  # passive_interfaces: []
  #   # - default
  # redistribute: []
  #   # - bgp
  #   # - connected
  #   # - kernel
  #   # - ospf
  #   # - static
```

## License

MIT

## Author Information

Larry Smith Jr.

-   [EverythingShouldBeVirtual](http://everythingshouldbevirtual.com)
-   [@mrlesmithjr](https://www.twitter.com/mrlesmithjr)
-   <mailto:mrlesmithjr@gmail.com>
