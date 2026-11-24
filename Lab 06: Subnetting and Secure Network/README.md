# Lab 06: Subnetting and Secure Network

## Overview
In this lab, I divided a `192.168.10.0/24` network into two equal `/25` subnets, configured router interfaces, tested connectivity, and implemented basic router security using SSH.

## Objectives
- Divide a `/24` network into two `/25` subnets.
- Configure router interfaces and end devices.
- Test connectivity between two different subnets.
- Enforce a minimum password length.
- Configure login blocking after repeated failed attempts.
- Enable SSH Version 2.
- Disable Telnet and allow SSH-only remote access.

## Network Topology
- 1 Router (Router0)
- 2 Switches (Switch0 and Switch1)
- 2 Laptops (Laptop0 and Laptop1)

## Subnetting

Original Network: `192.168.10.0/24`

Borrowed Bits: `1`

New Prefix: `/25`

Subnet Mask: `255.255.255.128`

| Network | Network Address | Usable IP Range | Broadcast |
|---|---|---|---|
| Net A | 192.168.10.0/25 | 192.168.10.1 - 192.168.10.126 | 192.168.10.127 |
| Net B | 192.168.10.128/25 | 192.168.10.129 - 192.168.10.254 | 192.168.10.255 |

## IP Addressing Table

| Device | Interface | IP Address | Subnet Mask | Gateway |
|---|---|---|---|---|
| Router0 | G0/0 | 192.168.10.1 | 255.255.255.128 | N/A |
| Router0 | G0/1 | 192.168.10.129 | 255.255.255.128 | N/A |
| Laptop0 | NIC | 192.168.10.2 | 255.255.255.128 | 192.168.10.1 |
| Laptop1 | NIC | 192.168.10.130 | 255.255.255.128 | 192.168.10.129 |

## Router Configuration

### 1. Configure Interfaces

```cisco
enable
configure terminal

interface gigabitEthernet 0/0
ip address 192.168.10.1 255.255.255.128
no shutdown
exit

interface gigabitEthernet 0/1
ip address 192.168.10.129 255.255.255.128
no shutdown
exit
```

### 2. Configure Router Security

```cisco
security passwords min-length 10

login block-for 120 attempts 3 within 60

username admin secret <SSH_PASSWORD>
```

### 3. Enable SSH Version 2

```cisco
ip domain-name lab.local
crypto key generate rsa
ip ssh version 2
```

### 4. Configure SSH-Only Remote Access

```cisco
line vty 0 4
login local
transport input ssh
exit

end
write memory
```

## Connectivity Testing

| Test | Result |
|---|---|
| Laptop0 → Router0 (192.168.10.1) | Successful |
| Laptop1 → Router0 (192.168.10.129) | Successful |
| Laptop0 → Laptop1 (192.168.10.130) | Successful |

## Security Verification

| Test | Result |
|---|---|
| SSH from Laptop0 | Successful |
| SSH from Laptop1 | Pending troubleshooting |
| Telnet access | Rejected |
| SSH Version 2 | Enabled |
| Configuration saved | Successful |

## Commands Used for Verification

```cisco
show ip interface brief
show ip ssh
show running-config
```

## Skills Learned
- IPv4 subnetting and borrowing host bits.
- Router interface configuration.
- Inter-subnet communication.
- Password security.
- Login attack protection.
- SSH configuration and remote access.
- Disabling insecure Telnet access.

## Tools
- Cisco Packet Tracer
- Cisco IOS CLI

**Note:** This README documents the current test results. Update the Laptop1 SSH result after troubleshooting.
