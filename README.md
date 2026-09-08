# Home Network Engineering Lab

A self-hosted network engineering lab running on a home Ubuntu server, built to design, test, and document enterprise routing, switching, security, and network-management scenarios on real Cisco IOS-XE behavior — not just theory.

---

## Lab Environment

| Component        | Detail                                                                 |
|-------------------|-------------------------------------------------------------------------|
| Host              | Ubuntu Server (bare-metal / home network)                               |
| Emulation platform| EVE-NG, self-hosted locally                                             |
| Device images     | Cisco IOS-XE (vIOS / IOSvL2)                                            |
| Monitoring        | SNMP (v2c and v3) server + NetFlow collector, deployed on a bare-metal Ubuntu NMS host (192.168.1.7) on the home network, reachable from EVE-NG via a management cloud interface |
| Documentation     | Lab manuals generated as `.docx` via Node.js (`docx` library) — dark-themed code blocks, color-coded callouts, verification-first structure |

---

## Network Topology (Overview)

```
                    [ EVE-NG Hypervisor ]
                            |
        ---------------------------------------
        |            |            |
     Router 1     Router 2     Router 3
        |            |            |
        -------------+------------
                      |
           [ Management Cloud Interface ]
                      |
                Home Network (LAN)
                      |
        [ Bare-Metal Ubuntu NMS Host — 192.168.1.7 ]
              (SNMP Server + NetFlow Collector)
```

The NMS host is not an emulated node — it's a physical Ubuntu server on the home LAN, bridged into the EVE-NG topology through a management cloud interface. Routers send SNMP polls/traps and NetFlow export across that bridge to the real host, mirroring how a production network would route management traffic to a physical NOC server.

---

## Projects

### 📊 Network Management Lab — SNMP / Syslog / NetFlow
Deployed a full monitoring stack on a bare-metal Ubuntu NMS host (192.168.1.7) on the home network, bridged to a 4-router EVE-NG topology via a management cloud interface:
- **SNMP** — configured and verified both SNMPv2c (community strings) and SNMPv3 (authPriv, user-based security model)
- **Syslog** — centralized logging from all routers to the NMS host
- **NetFlow** — both traditional NetFlow and Flexible NetFlow exporting to a collector (`nfcapd`), with flow analysis via `nfdump`

**Issues found and fixed during the build:**
- `snmptrapd.service` was missing its `[Install]` section on Debian/Ubuntu, preventing the service from enabling at boot — patched into the systemd unit file
- A file ownership mismatch was silently blocking trap logging to disk — corrected ownership/permissions on the trap log directory
- nfdump 1.7.x changed a CLI flag, which broke `nfcapd` on startup — pinned the compatible flag syntax and documented the version dependency

Each fix was patched directly into the build script so the environment rebuilds cleanly from scratch.

### 🔀 Routing & Switching
*(link out to your other lab manuals here — BGP, OSPF, FHRP/STP, etc.)*

### 🔐 Security & Segmentation
*(link out to ACL, VRF-Lite/GRE-IPsec, Site-to-Site VPN manuals here)*

---

## Repository Structure

```
/labs
  /network-management     # SNMP, syslog, NetFlow
  /bgp
  /ospf
  /switching-fhrp
  /acl
  /vrf-gre-ipsec
  /site-to-site-vpn
  /nat
/manuals                  # generated .docx lab manuals
/topologies                # EVE-NG topology exports / diagrams
/scripts                   # NMS build scripts, manual-generation tooling
```

---

## Skills Demonstrated

`EVE-NG` `IOS-XE` `SNMP v2c/v3` `Syslog` `NetFlow / Flexible NetFlow` `Linux Server Administration` `systemd` `OSPF` `BGP` `HSRP/VRRP/GLBP` `ACL/PACL/VACL` `VRF-Lite` `GRE/IPsec` `Node.js` `Technical Documentation`

---

## Contact

Toran — Network Engineer | CCNP-track
[LinkedIn] · [Email]
