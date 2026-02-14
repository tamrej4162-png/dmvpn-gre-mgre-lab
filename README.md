# DMVPN, GRE and mGRE Lab Implementation
Status
Completed and Verified
Lab Type: Hands-on Implementation

Project Overview

This project demonstrates the practical implementation of:
    GRE (Generic Routing Encapsulation)
    mGRE (Multipoint GRE)
    DMVPN (Dynamic Multipoint VPN)
    NHRP (Next Hop Resolution Protocol)
    IPsec tunnel protection

The objective was to understand tunnel encapsulation, dynamic spoke registration, secure communication over a public network, and packet-level behavior.
    Lab Environment
    Platform: EVE-NG
    Router OS: Cisco IOS
    Topology Type: Hub-and-Spoke

Devices
    Hub Router:
        Name: Bangalore   
        Public IP: 11.1.1.1
    Spoke Router:
        Name: Delhi
        Public IP: 11.3.3..2
        Name: Hyderabad
        Public IP: 11.4.4.1
        Name: Pune
        Public IP: 11.5.5.1
        
Network Design
  Tunnel Network: 192.168.100.0/24

The hub router uses mGRE to support multiple dynamic spokes.
Spokes register with the hub using NHRP.

Implementation Steps

Configured GRE tunnel between hub and spoke.

Converted hub tunnel to mGRE for multipoint support.

Configured NHRP with hub as NHS (Next Hop Server).

Applied IPsec profile to protect tunnel traffic.

Verified routing between internal LAN networks.

Key Configuration Sections
Hub

Tunnel interface (mGRE)

NHRP configuration

IPsec profile

Routing configuration

Spoke

Tunnel interface

NHRP mapping and NHS configuration

IPsec profile

Routing configuration

(Full configurations available inside /configs folder.)

Verification

The following commands were used to validate functionality:

show ip nhrp

show dmvpn

show crypto isakmp sa

show crypto ipsec sa

Results

Spoke successfully registered with hub (NHRP dynamic entry visible).

IPsec Security Associations established.

Tunnel interface status: up/up.

End-to-end ping between internal networks successful.

Packet Capture Analysis

Packet capture confirms:

Inner packet: Private IP communication (LAN to LAN).

Outer packet: Public IP encapsulation.

ESP header present when IPsec enabled.

This validates GRE encapsulation followed by IPsec encryption.

Issues Faced and Troubleshooting

NHRP registration failure due to incorrect mapping.

IPsec Phase 1 failure caused by pre-shared key mismatch.

Routing misconfiguration prevented internal network reachability.

Each issue was identified using verification commands and corrected accordingly.

Learning Outcomes

Clear understanding of GRE vs mGRE differences.

Practical implementation of DMVPN hub-and-spoke architecture.

Hands-on troubleshooting of NHRP and IPsec.

Deeper understanding of packet encapsulation flow.

Future Enhancements

Implement DMVPN Phase 3.

Add dual hub redundancy.

Deploy dynamic routing protocol (EIGRP/OSPF/BGP).

Automate configuration using Python and RESTCONF
