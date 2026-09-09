---
layout: default
title: Home
permalink: /
description: >-
  Cisco network engineering labs, manuals, and notes covering nearly the full
  CCNP ENCOR v1.2 blueprint — built and documented in EVE-NG.
---

# Network Engineering Lab Portfolio

This repository is a collection of Cisco network engineering labs built and documented in EVE-NG — covering routing, switching, security, address translation, network management, and automation. It contains exported EVE-NG lab topologies, professional lab manuals, and PPT notes for almost all topics in CCNP-ENCOR blueprint v1.2.

---

## Repository Contents

* **EVE-NG exported lab topologies** — `.unl`/exported topology files for every lab, so any environment can reload the exact same setup
* **Lab manuals** — detailed, verification-first documentation for each lab (configuration steps, expected output, troubleshooting notes)
* **PPT notes** — supporting slide decks summarizing concepts, topology diagrams, and key takeaways for each lab

---

## EVE-NG Deployment Environment

### Local Deployment (Current)

EVE-NG Community Edition is deployed locally on a Dell XPS laptop:

|Component|Detail|
|-|-|
|Platform|EVE-NG Community Edition|
|CPU|Intel Core i7 (supports nested virtualization — required for EVE-NG's own VM/container-based device emulation)|
|RAM|8 GB|
|Storage|238 GB SSD|

Running EVE-NG locally keeps the lab fully self-contained and avoids ongoing cloud costs, at the trade-off of being limited by the laptop's RAM/CPU for larger, denser topologies.

### Cloud Deployment Experience

EVE-NG was also tried on Google Cloud Platform using the free-tier account. This worked well initially, but became too costly once the free credits expired, so the lab was moved back to local deployment.

GCP deployment details (for reference):

* Compute: spot/preemptible GCE VM
* Storage: shared persistent disk for EVE-NG lab data, with systemd mount ordering
* Access: IAP-based tunnel (no public IP exposed) — used because the network account had no static home IP
* Network tier: Premium

---

## Repository Structure

```
/EVE-NG-Topology-files      # EVE-NG exported lab topology files
/Lab-Pcap-files              # Pcap files from labs to visualise protocols operation
/Labs-Manuals                # Lab manuals (per-lab documentation)
/Notes                        # PPT notes and supporting slide decks
```

---

## Browse the Repository

- [📖 Browse Lab Manuals]({{ site.baseurl }}/lab-manuals/)
- [🗺️ Browse EVE-NG Topology Files]({{ site.baseurl }}/eve-ng-topology-files/)
- [📦 Browse Packet Captures]({{ site.baseurl }}/lab-pcap-files/)
- [📝 Browse Notes]({{ site.baseurl }}/notes/)

## Note

```
For lab topologies that do not have pdf manuals, follow OCG book section for that topic such as ZBFW and CoPP. Credit to EVE-NG community for some lab topologies and manuals such as VTP, Etherchannels, SPAN and RSPAN.
```


## Skills Demonstrated

`EVE-NG` `IOS-XE` `Nested Virtualization` `Static Routing` `OSPF` `BGP` `HSRP/VRRP/GLBP` `ACL/PACL/VACL` `VRF-Lite` `GRE/IPsec` `SNMP` `NetFlow` `EEM/Ansible` `SPAN/RSPAN/ERSPAN` `STP/RSTP/MST` `VTP/DTP/EtherChannels`

---

## Contact

Toran Shahi | Network Engineer | CCNP-track
[LinkedIn](https://www.linkedin.com/in/toran-shahi-b587231b1/) · [Email](mailto:toranjungshahi@gmail.com)
