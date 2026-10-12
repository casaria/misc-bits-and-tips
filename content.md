# Misc Bits & Tips

### A running collection of notes, specs, and maintenance tips across the Casaria home systems

---

## Overview

This is a catch-all reference — equipment specs, part numbers, maintenance intervals, and other bits worth keeping track of, that don't belong to any single project. Entries are added as they come up.

## Honeywell F300 Electronic Air Cleaner

**Model:** F300E1019
**Type:** Whole-house electronic air cleaner (electrostatic precipitator)
**Size:** 16 × 25

| Spec | Value |
|---|---|
| Rating | 1400 CFM |
| Electrical | 120 VAC, 60 Hz, 0.4 A (240V conversion kit: 203365A) |
| Efficiency | Up to 98% of particles, 3.0–10.0 micron |
| Cabinet dimensions | 16-3/16 in H × 25-1/2 in W × 6-3/4 in D |
| Duct opening (nominal) | 16 × 25 |
| Mounting | Return air duct, upstream of the evaporator coil |
| Config | Two-cell model with media post-filters ("E" version) |
| Warranty | 10-year Clean Coil Guarantee |

### Replacement parts

- **Electronic cells:** `FC37A1130` (12.5 × 16) — qty 2, washable/reusable
- **Prefilters:** `203371` (pack of 2) — washable; also referenced as `203368`
- **Media post-filters:** `50000293-002` (16 × 12.5) — qty 2, consumable

### Maintenance intervals

- **Cells & prefilters:** Wash regularly — twice a year with normal use, more often with heavy use. A quick cleaning can be done frequently; a full cleaning can wait for yearly maintenance since efficiency stays high even as the cells load up.
- **Media post-filters:** Replace every 6 months. Do not wash them — washing neutralizes the factory-applied electrostatic charge.
- **Washing method:** Wash cells first, then prefilters the same way. Make sure both are fully dry before reinstalling.
- **Operating tip:** For best results, leave the air cleaner switch on at all times and set the thermostat fan to "On" for continuous circulation.

Full manual: [68-0240EFS.pdf](https://digitalassets.resideo.com/damroot/Original/10014/68-0240EFS.pdf)

## Home Network & Handover Notes

**Network:** Ubiquiti UniFi (gateway, switching, access points)
**Purpose:** Handover reference for the new homeowner
**Prepared:** October 12, 2026

> **Do not rename the SSIDs `CASARIA-CL2` and `CASARIA-24`, and do not change their passkeys.** The configured IoT devices depend on them — either change means reconfiguring every device to keep it operational. Use a separate SSID for personal use.

### Network

| Item | Detail |
|---|---|
| Hardware | All Ubiquiti UniFi — business-grade, fully compatible, managed centrally |
| Performance | Very high throughput and reliability; easily runs 3 wireless video streams at once, 1500 Mbit and upwards possible |
| Controller | UniFi Network controller runs on the laptop and is used for configuration |
| Gateway | White box, ~5 × 5 × 1 in — router and gateway in one, already configured |
| Access point | UniFi Pro AP on the 2nd floor, covers the whole house and yard |

**Connection chain:**

```
RG6 coax → cable modem → Ethernet (Cat5) → UniFi gateway WAN port → private LAN IPs
```

The gateway takes whatever public IP the provider assigns and translates it to private IPs for the home network. Don't replace the UniFi gear with a typical homeowner-style router or gateway.

### Cox / Spectrum modem

- **Modem only:** Ask Cox for a modem-only unit, **or** put the rented combo unit (modem + router + access point) in **bridge mode**.
- **Why:** Otherwise you get a double NAT, which makes remote access and port forwarding practically impossible and is very tricky to configure.

### Applications

| App | Notes |
|---|---|
| Home Assistant | `http://homeassistant.local:8123` or `http://192.168.13.159:8123`, from any browser on the network |
| Home Assistant Companion app | Highly recommended — Android and iOS, including Apple Watch |
| Remote access | By default the app and browser only work on the local network; for outside access, sign up for Home Assistant Cloud (Nabu Casa) |
| Rachio sprinkler timer | Transfers to the new homeowner via a simple transfer screen in the app |
| Garage door (myQ) | We assume you've already reset the access — let us know if you need us to transfer anything |

### Internet connection first

Transfers can't be done until a working internet connection to the UniFi gateway is established. This is plug and play — no other network configuration is required. Just connect the new modem to the gateway's **WAN port**.

### Modem swap steps

1. **Locate the existing combo unit** (modem, router and access point in one). It has a two-prong AC power cord, an RG6 coax input with an F-type connector, and an Ethernet port.
2. **Disconnect the power.**
3. **Remove the RG6 coax connector.**
4. **Identify the Ethernet patch cable** (note its color; it's Cat5) and unplug it from the existing unit.
5. **Connect the new cable modem** supplied by the provider: attach the coax, plug in the Ethernet patch cable, and connect power. If it's a combo unit, set it to bridge mode.
6. **Return the existing unit** to Shelly, our realtor.

## Status

Living document — more entries get added here as they come up.
