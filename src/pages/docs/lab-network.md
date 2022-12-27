---
title: Setting up our core network
description: The absolute start for a solid homelab is a solid network
---

## Hardware

The lab uses Unifi gear:

- UniFi Dream Machine Pro
- UniFi Switch Enterprise 24 PoE (USW-Enterprise-24-POE)
- ~~UniFi Switch 24 PoE (USW-24-PoE)~~ (soon)
- UniFi Access Point U6 Long-Range (U6-LR-US)
- UniFi Access Point U6 Enterprise (U6-Enterprise-US)

The Dream Machine Pro and Access Points are not lab specific but I wanted to paint the full picture. Currently the house and the lab share the Enterprise Switch. In the future the lab hardware will be offloaded to a simple 24 Port freeing up ports for both the lab and the house as well as allowing for hardware level VLAN.

{% callout title="Disclaimer!" %}
You do not need a network this elaborate to start a homelab. This network was built over some time to accommodate not only a homelab but an ever growing number of "smart" devices (IoT), and an array of high bandwidth media consumption devices; game consoles, smart TV, PCs, phones, tablet, etc.
{% /callout %}

## Configuration

### VLANS

For security as well as for organization we have set up VLANS. Some example VLANS

- 10.1.1.0/24 -- Default
- 10.1.2.0/24 -- Kids
- 10.1.3.0/24 -- IoT
- 10.1.4.0/24 -- Homelab

### Firewall Rules

Each VLAN is set with a few rules.

| Index | Action | Count | Type   | Description                                 |
| ----- | ------ | ----- | ------ | ------------------------------------------- |
| 2000  | Accept | All   | LAN In | Allows all Established and Related Sessions |
| 2001  | Drop   | All   | LAN In | Drop Invalid State                          |
| 2002  | Accept | All   | LAN In | Alow Default to ALL VLANS                   |
| 2003  | Drop   | All   | LAN In | Block Inter-VLAN Routing                    |
| 2004  | Drop   | All   | LAN In | Block IoT & Homelab to Gateways             |
| 2005  | Drop   | All   | LAN In | Block IoT & Homelab to UDM Interface        |

Firewall rules work from top down meaning if something is allowed first and blocked second then it is allowed, inversely if a rule is blocked allowed first and blocked second then it is allowed.

So our first rule allows any _Established and Related Sesion_. What this rule does is allow the source of information to talk back to the destination. As I understand it. When you reach out to a website (for example) you are establishing a session, in a basic sense by having this rule you are saying "If I have established the session, let the website reply back".

> The established/related rule leverages the stateful nature of the firewall (they're states after all). If a given session was not already allowed to be created by one of the other rules, an established/related rule would never match.

Followed up by the rule _Drop Invalid State_. This stops communication coming in from a session that is not already established (in the rule above)

The next rule says that any device on the default VLAN can talk to any device in any other VLAN, thus our laptop or desktop can request a website (for example) that is being hosted internally on our Homelab (or any other) VLAN.

_Block Inter-VLAN Routing_ makes it so a device on Kids or IoT cannot just reach across VLANS. So a compromise smart home (IoT) device can't then gain access to our Homelab.

Our last two rules explicitly disallow devices on the IoT & Homelab VLAN from connecting directly to and making changes to our Gateway and UDM Pro.

### Port Management

Finally we connect our Lab equipment to our switch. While we can set all of our lab devices to be on 10.1.4.x, with port management we can select the individual ports on out switch and set profiles to only allow devices on a given port to be part of a specific VLAN. In the future when our second switch is ordered. That entire switch will be provisioned to the Homelab Only profile.

## Accessing from the outside

There are a number of methods one could use from port-forwarding to tunneling. I am undecided on exactly how I will accomplish this, but for now I am using [CloudFlare Tunnels (Zero Trust)](https://www.cloudflare.com/products/tunnel/), YouTuber and Homelab Homie, [Raid Owl](https://www.youtube.com/@RaidOwl) did a solid guide on [setting this up in his lab](https://www.youtube.com/watch?v=hrwoKO7LMzk). For my needs, it is not without its issues but it seems to be a safer idea than poking holes in the network.

Another idea is using [Teleport](https://goteleport.com) which [Christian Lempa](https://www.youtube.com/@christianlempa) has done a few videos on, [like this one](<(https://www.youtube.com/watch?v=9__A_nO2pbk)>). I will update this as I find a perminent solution.

## Closing Thoughts

A homelab does not need to be this complex, it can (and likely will) grow over time. The core takeaway is that network security should be a first thought, not something we scramble to address once it has become a problem. It is best to take the approach of "least privilege" in all things security, that is to say give the minimal level of access needed to achieve the desired outcome.
