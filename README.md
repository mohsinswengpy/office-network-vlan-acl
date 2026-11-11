# office-network-vlan-acl
Multi-department office network in Cisco Packet Tracer with 5 VLANs, inter-VLAN routing on a Layer 3 switch, ACL security, and PAT.
# Office Network: VLANs, Inter-VLAN Routing and ACL Security

A multi-department office network designed and configured in Cisco Packet Tracer.

## Topology

![Topology](screenshots/topology.png)

## Design

| VLAN | Name | Subnet | Gateway (MLS1) |
|---|---|---|---|
| 10 | IT_ADMIN | 192.168.10.0/24 | 192.168.10.1 |
| 20 | SALES | 192.168.20.0/24 | 192.168.20.1 |
| 30 | FINANCE | 192.168.30.0/24 | 192.168.30.1 |
| 40 | GUEST | 192.168.40.0/24 | 192.168.40.1 |
| 50 | SERVERS | 192.168.50.0/24 | 192.168.50.1 |
| 99 | MGMT | 192.168.99.0/24 | 192.168.99.1 |

- MLS1 (3560-24PS) performs inter-VLAN routing through SVIs.
- R1 (2911) provides PAT toward a simulated ISP.
- Trunks use native VLAN 999, with DTP disabled.

## Security

- Extended ACLs: `SALES_IN`, `FINANCE_IN`, `GUEST_IN`
- Port security and BPDU Guard on access ports
- SSH management limited to the IT VLAN (`SSH_ADMIN`)

## Verification

| Test | Command | Expected result |
|---|---|---|
| Cross-VLAN ping (allowed) | `ping 192.168.30.11` from IT-PC1 | Success |
| ACL block | `ping 192.168.30.11` from SALES-PC1 | Fail |
| Trunk status | `show interfaces trunk` on MLS1 | Gi0/1 and Gi0/2 trunking |


## Tools

Cisco Packet Tracer, Cisco IOS CLI
