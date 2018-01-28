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

| Protocol | Implemented | Notes               |
| -------- | ----------- | ------------------- |
| BGP      |             | N/A                 |
| OSPF     | X           | Only initial config |

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
