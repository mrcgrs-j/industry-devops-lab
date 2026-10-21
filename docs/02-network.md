# Network Architecture

## Network Configuration

| Parameter | Value |
|---|---|
| Network | `172.16.10.0/24` *(provisional)* |
| Subnet mask | `255.255.255.0` *(verify)* |
| Default gateway | `172.16.10.1` *(Windows ICS, if enabled)* |
| DNS | Verify actual configuration |
| Topology | Single Ethernet LAN |
| Industrial switch | Moxa EDS-205 |
| VLANs | None configured |

## Network Topology

```mermaid
flowchart TB
    NET["LAB NETWORK<br/>172.16.10.0/24 — provisional<br/>Mask: 255.255.255.0 — verify<br/>Gateway: 172.16.10.1 — verify"]

    subgraph LAPTOP["Physical laptop — Windows"]
        subgraph VB["Oracle VirtualBox"]
            WIN11["VM: win11-siemens<br/>Windows 11"]
            TIA["TIA Portal V18"]
            NIC["VirtualBox NIC 1<br/>Bridged"]
            WIN11 --- TIA
            WIN11 --- NIC
        end
        USB["TP-LINK Gigabit Ethernet USB Adapter"]
        NIC --- USB
    end

    SW["Moxa EDS-205<br/>5-port Fast Ethernet switch"]

    RPI["Raspberry Pi 5<br/>VMware ESXi on Arm Fling<br/>IP: 172.16.10.2"]
    VM["Ubuntu VM<br/>IP: 172.16.10.6"]
    PLC["Siemens S7-1200 CPU 1212C<br/>IP: TBD"]
    HMI["Siemens KTP600 Basic PN<br/>IP: TBD"]

    NET --- SW
    USB <-->|Ethernet| SW
    SW <-->|Ethernet| RPI
    SW <-->|Ethernet| PLC
    SW <-->|Ethernet| HMI
    RPI --- VM
```

## Known IP Addresses

| Device | IP address | Subnet mask | Status |
|---|---|---|---|
| Laptop / ICS interface | `172.16.10.1` | Verify | Previously reported |
| ESXi management | `172.16.10.2` | Verify | Previously reported |
| Ubuntu VM | `172.16.10.6` | `255.255.0.0` reported earlier | Verify current config |
| PLC | TBD | TBD | Not confirmed |
| HMI | TBD | TBD | Not confirmed |
| Windows 11 VirtualBox VM | TBD | TBD | Check inside guest OS |

## Notes

- VirtualBox Adapter 1 is configured as Bridged to
  `TP-LINK Gigabit Ethernet USB Adapter`.
- TIA Portal V18 runs inside the Windows 11 guest VM.
- The laptop, PLC, HMI and ESXi management interface are intended
  to communicate over one shared Ethernet LAN.
- Confirm the actual subnet mask and IP addresses before treating
  this document as the final network configuration.
- Do not publish credentials, private keys or access tokens.

