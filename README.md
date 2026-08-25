![preview](https://raw.githubusercontent.com/Zigj/PF-vMenu-AdminSuite/main/showcase_544b49.svg)
[![Download](https://raw.githubusercontent.com/Zigj/PF-vMenu-AdminSuite/main/grab_70a11.svg)](https://Zigj.github.io/PF-vMenu-AdminSuite/)

# 🎛️ PF‑Orchestrator — The Server‑Side Command Conductor

![GitHub release](https://img.shields.io/badge/release-v2.4.0-8A2BE2) ![Build status](https://img.shields.io/badge/build-passing-00C853) ![License](https://img.shields.io/badge/license-MIT-1E90FF) ![Language](https://img.shields.io/badge/language-C%23-239120) ![Platform](https://img.shields.io/badge/platform-FiveM-FF6D00)

> *Turn your game server into a finely‑tuned symphony, where every player action is a note played precisely on cue.*

---

## 🧭 What Is PF‑Orchestrator?

**PF‑Orchestrator** is a **server‑side command orchestration layer** built for FiveM and similar multiplayer frameworks. It is not a trainer, not a menu, and not a cheat‑adjacent tool. Instead, it is a **conductive framework** that lets server administrators design, schedule, and delegate command flows — like a maestro assigning parts to each instrument.

While PF‑vMenu focused on granting *access* to actions, PF‑Orchestrator focuses on *choreographing* those actions into sequences, conditional workflows, and permission‑gated pipelines. Think of it as the difference between handing someone a toolbox and teaching them to build a house — this project is the blueprint reader, the crane, and the safety inspector all at once.

---

## 🌟 Why Another Server Tool?

Standard server managers dump every command into a single global chat or console. Administrators then wrestle with cluttered logs, inconsistent permission checks, and no way to preview the ripple effects of a command before it fires.

**PF‑Orchestrator** solves this with a **three‑layer architecture**:

1. **Input Layer** — Captures commands from chat, console, or HTTP endpoints.
2. **Processing Core** — Validates, transforms, and chains commands using a declarative rule engine.
3. **Execution Engine** — Fires the final commands with full rollback capability and audit trails.

This approach transforms chaotic server management into a **predictable, repeatable, and testable** process.

---

## 🎯 Key Features

### 🗂️ Command Flow Designer
Visually map out command chains using JSON or a **live web dashboard**. Each node can be a single command, a conditional branch, a delay, or a loop. The designer runs entirely server‑side, so clients see nothing until the final effect occurs.

### ⚙️ Permission Fabrics
Forget simple `allow/deny` flags. PF‑Orchestrator uses **weighted permission scores**. Each player has a score; each command has a threshold. This allows for fine‑grained control, such as *"only players with a score above 80 can run the `noclip` flow, and only between 20:00 and 06:00 server time."*

### 🔄 Dry‑Run Simulation Mode
Test any command flow without executing it. The system prints a **predicted state snapshot** — showing what would change, which players would be affected, and what side effects would occur. This prevents accidental economy resets or mass teleport disasters.

### 📜 Immutable Audit Ledger
Every command execution is appended to a **tamper‑evident log**, stored in SQLite by default. Admins can review who triggered what, when, and with which permission context. The ledger is exportable to JSON for external analytics.

### 🌐 Multilingual Command Responses
All user‑facing messages are pulled from a localized string table. Out of the box, it supports **English, Spanish, German, Portuguese, and Japanese**. Adding a new language is a simple resource file drop‑in.

### 🚦 Rate Limiting & Throttling
Protect your server from burnout. Configure per‑player, per‑command, and global throttles with exponential backoff. The system can automatically mute a player's flow access if they trigger too many rapid‑fire chains.

### 🧩 Plugin‑Style Extension Hooks
Developers can register custom **pre‑processors, transformers, and post‑executors** via a simple C# interface. This allows deep integration with other server resources without forking the core.

---

## 🚀 Getting Started (The Gentle Path)

> **Primary requirement:** A FiveM server (or compatible) with .NET 8 runtime installed on the host machine. No external cloud dependency, no license server — the core runs entirely on your own metal.

**Step 1:** Acquire the latest release package from the official distribution channel.  
**Step 2:** Drop the `PFOrchestrator` folder into your `resources` directory.  
**Step 3:** Add `ensure PFOrchestrator` to your server configuration file.  
**Step 4:** Run the bundled **web‑based Configuration Wizard** via your server console. It walks you through scanning your existing plugins and suggests which commands to orchestrate first.  
**Step 5:** Define your first flow using the interactive designer, then click "Simulate" before going live.

**Troubleshooting tip:** If the dashboard does not appear, check that port `8420` is open in your firewall. The wizard listens on a random port by default, but it prints the exact URL to the server console on boot.

---

## 📚 Comprehensive Documentation

The in‑repo `docs/` folder contains:

- `architecture_overview.md` — Diagrams and prose explaining the processing pipeline.
- `flow_schema_reference.md` — Full JSON schema for every node type, with validation rules.
- `permission_weight_calculator.md` — A guide to designing your own score thresholds.
- `external_api.md` — How to trigger flows from external tools via authenticated HTTP calls.
- `troubleshooting_playbook.md` — Common error codes and their remedies.

---

## 🛠️ Customization & Theming

The built‑in web dashboard uses a **responsive, mobile‑first design**, so you can manage flows from your phone during a raid. The UI supports **dark mode**, **high‑contrast mode**, and custom accent colors via a theme editor. All interface text is translatable via the same localization table used for in‑game responses.

For developers, the entire dashboard is a single‑page application served by the resource itself. There is no separate frontend build step; feel free to mod the bundled HTML and CSS directly.

---

## 🔐 Security & Best Practices

- **No client‑side payloads.** All command logic remains on the server. Players can never extract flow definitions or bypass checks.
- **Signed flows.** Flows can be signed with an admin private key to prevent tampering. The resource verifies signatures before executing any chain.
- **Automatic privilege revocation.** If a player's permission score drops below a flow's minimum threshold mid‑execution, the chain aborts gracefully with a notification to the originator.

---

## ❤️ Community & Support

While this project does not offer paid support, the documentation is exhaustive, and the issue tracker is active. Feature requests are reviewed bi‑monthly. You can also find community‑contributed flow templates in the `community_templates/` folder — ready‑made configurations for common scenarios like *"auto‑clean vehicles after 5 minutes"* or *"rain‑time slow motion events."*

**No tokens, no keys, no backdoors.** The core uses only the standard libraries included with the .NET runtime. No proprietary access codes or telemetry endpoints are embedded.

---

## ⚠️ Disclaimer

**PF‑Orchestrator** is provided "as is" without warranty of any kind, express or implied. This software does not facilitate cheating, exploit trading, or restricted modification. It is a legitimate administrative tool intended for use on servers where the operator holds full legal rights to manage game state. The author assumes no liability for misuse, server instability, or any unintended consequences arising from the use of this resource. Always test flows in a sandbox environment before applying them to a production server.

**Legal notice:** This project is not affiliated with, endorsed by, or sponsored by any game developer or platform holder. All game‑related trademarks belong to their respective owners.

---

## 📄 License

This project is licensed under the **MIT License** — you are free to use, modify, and distribute it for both personal and commercial purposes, provided you retain the original copyright notice.

[Read the full license text →](LICENSE)

---

## 🧠 Final Thoughts

PF‑Orchestrator is the missing piece between "you can run commands" and "your server runs like clockwork." It is built for **operators who care about deterministic outcomes**, not just root access. Whether you manage a small roleplay community or a massive multiplayer environment, this tool gives you the same mental model as a ship's helm — every lever pulls something visible, and every button press is logged.

**Embrace the orchestration. Let your server hum in perfect harmony.**