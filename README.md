# PurpleSkjaldborg

<p align="center">
  <img src="static/logo.png" alt="PurpleSkjaldborg Logo" width="280">
</p>

**Purple-team threat modeling in the browser.** Zero dependencies. One HTML file. Offense *and* defense on one canvas.

> *Skjaldborg* (Old Norse) — a **shield wall** formation where defenders interlock shields against attackers.
> This tool helps you build that digital shield wall.

---

<p align="center">
  <img src="static/demo.gif" alt="PurpleSkjaldborg Demo" width="100%">
</p>

---

## What Is This?

PurpleSkjaldborg is a visual threat modeling tool that combines **red team attack paths** with **blue team defensive controls** in a single diagram. It integrates four industry-standard frameworks:

| Framework | Role in Skjaldborg |
|-----------|-------------------|
| **STRIDE** | Threat categorization per element (Spoofing, Tampering, Repudiation, Info Disclosure, DoS, EoP) |
| **PASTA** | 7-stage risk-centric methodology mapped to canvas constructs |
| **MITRE ATT&CK** | Adversary techniques auto-mapped to Red Team nodes and attack edges |
| **MITRE D3FEND** | Defensive countermeasures auto-mapped to Blue Team shields and boundaries |

---

## Quick Start

```bash
# No build. No install. Just open it.
open index.html

# Or serve locally:
python -m http.server 8765
# then navigate to http://localhost:8765
```

The app loads an **AD Attack Chain** sample by default. Click **Sample** in the toolbar to explore all 5 built-in scenarios.

---

## Features

### Red Team Arsenal

- **C2 Frameworks** — Cobalt Strike, Brute Ratel, Sliver, Havoc, ArachneC2, AdaptixC2
- **Phishing Infra** — EvilGinx2, GoPhish, Tangled, PhishingClub
- **Pivoting & Tunneling** — Ligolo-ng, Chisel, SSH tunnels, SOCKS proxies, dnscat2, iodine
- **Living off the Land** — LOLBins, LOLDrivers, file transfer utilities
- **Auto ATT&CK** — Every Red Team node ships with pre-mapped technique IDs

### Blue Team Shields

- **EDR/XDR** — CrowdStrike Falcon, Microsoft Defender, Elastic Security, Sysmon
- **NDR/NOC** — Darktrace, Vectra AI, Zeek
- **Network Filtering** — pfSense, Suricata IDS/IPS, Squid
- **Cloud Security** — Prisma Cloud, CASB, AWS GuardDuty
- **Hardening & Deception** — ASR/GPO, Kyverno, HoneyPots/Decoys

> Blue tools attach as **shields on assets** (force-ring + D3FEND coverage), not floating boxes.

### Canvas & Visualization

- **Animated tunnel edges** — Red glow for offensive pivots, blue glow for defensive VPN
- **Force-field boundaries** — Trust (blue), Privacy/PII (green), Cloud (gradient), Network (dashed)
- **Click-to-grab boundary movement** — Click once to grab, move, click again to place
- **Auto-arrange** — Organizes nodes by role (corporate / DMZ / cloud / red team)
- **Context menus** — Right-click anything for quick rename, duplicate, toggle, delete
- **Zoom & pan** — Scroll to zoom, drag background to pan

### Analysis & Reporting

- **Per-boundary risk scoring** — Attack surface vs. countermeasure coverage
- **STRIDE matrix** — Visual applicability grid for all elements
- **PASTA stages** — 7-stage methodology walkthrough mapped to your diagram
- **Markdown report export** — Full threat model document ready for wikis/PRs
- **JSON import/export** — Save and share models with your team

---

## Built-in Scenarios

| Scenario | Kill Chain | Key Techniques |
|----------|-----------|----------------|
| **AD Attack Chain** | Phishing → Credential Theft → Lateral Movement → Domain Dominance | Kerberoasting, DCSync, Golden Ticket, WireGuard VPN pivot |
| **K8s Cluster Compromise** | Initial Access → Pod Escape → Control Plane Takeover | RBAC abuse, etcd dump, Ligolo-ng tunnel, Chisel backup |
| **Cloud Identity Breach** | Token Theft → Privilege Escalation → Data Exfiltration (Azure) | Consent phishing, MFA bypass, Service Principal abuse |
| **Supply Chain Attack** | CI/CD Poisoning → Registry Tampering → Cloud Workload Compromise | Pipeline injection, IRSA abuse, ECR poisoning |
| **Ransomware (Double Extortion)** | RDP Brute → Cobalt Strike → DCSync → Exfil → GPO Deploy | BYOVD EDR kill, rclone exfil, VSS/Veeam deletion |

---

## Keyboard Shortcuts

| Key | Action |
|-----|--------|
| `?` | Toggle Help panel |
| `Shift` + click | Keep tool armed (place multiple) |
| `Esc` | Cancel armed tool / deselect |
| `Delete` / `Backspace` | Delete selected element |
| Double-click edge | Toggle attack vector (offensive) |
| Right-click | Context menu |
| Scroll | Zoom |
| Drag background | Pan |

---

## Architecture

```
index.html (single file, ~3000 lines)
├── <style>       — CSS: dark theme, animations, modal/overlay styles
├── <body>        — HTML: toolbar, palette, SVG canvas, inspector, overlays
└── <script>      — JS: state management, rendering, interactions, samples
    ├── COMPONENTS[]     — Node type definitions (icon, role, ATT&CK/D3FEND defaults)
    ├── STRIDE/PASTA     — Framework data structures
    ├── Render pipeline  — SVG: boundaries → edges → nodes (layered)
    ├── Interaction      — Drag, select, arm tools, context menus
    ├── Sample library   — 5 pre-built scenarios with spatial layout
    └── Help system      — Full-screen tabbed help (Tutorial/Metamodels/Workflow/Shortcuts/About)
```

**Zero dependencies.** No React, no D3, no build step. Opens in any modern browser, works offline.

---

## Philosophy

Most threat modeling tools make you choose: either you model the attacker *or* you model the defenses. PurpleSkjaldborg lets you do both on the same canvas because **purple teams need both perspectives simultaneously**.

- Attack paths and defenses rendered together expose gaps visually
- Residual risk scoring quantifies where you're under-defended
- Auto-mapped ATT&CK/D3FEND means you don't need encyclopedic MITRE knowledge
- Sample kill chains let you start from realistic scenarios and adapt

---

## Further Reading

- [Threat Modeling — Culture & Practice](https://benjitrapp.github.io/cultures/2022-06-11-threat-modeling/) — Foundational concepts on STRIDE, PASTA, and integrating threat modeling into engineering workflows
- [MITRE ATT&CK](https://attack.mitre.org/) — Adversary tactics & techniques knowledge base
- [MITRE D3FEND](https://d3fend.mitre.org/) — Defensive countermeasure taxonomy
- [Incident Response Playbooks](https://github.com/BenjiTrapp/incident-response-playbooks) — Companion IR visualization project

---

## License

MIT

---

<p align="center">
  <b>PurpleSkjaldborg</b> — Build your digital shield wall.<br>
  <sub>Purple-Team Threat Modeling &middot; STRIDE &middot; PASTA &middot; ATT&CK &middot; D3FEND</sub>
</p>
