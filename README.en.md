<div align="center">

<img src="assets/banner.svg" alt="NextCore Browser" width="100%">

# NextCore Browser

**A multi-profile browser with automation and AI agents, in one app for Windows, macOS and Linux.**

[![Latest release](https://img.shields.io/github/v/release/kennetvn/nextcore-browser-releases?label=latest&color=0293DA&style=flat-square)](https://github.com/kennetvn/nextcore-browser-releases/releases/latest)
[![Downloads](https://img.shields.io/github/downloads/kennetvn/nextcore-browser-releases/total?color=16181D&style=flat-square)](https://github.com/kennetvn/nextcore-browser-releases/releases)
![Platforms](https://img.shields.io/badge/platforms-Windows%20%C2%B7%20macOS%20%C2%B7%20Linux-0293DA?style=flat-square)
![License](https://img.shields.io/badge/license-commercial%20%C2%B7%20closed%20source-16181D?style=flat-square)

[**Download**](#download) · [Features](#features) · [Use cases](#use-cases) · [For developers](#for-developers-and-ai-agents) · [Docs](https://docs.homestaynextcore.org/nextcore-browser/) · [Product page](https://homestaynextcore.org/nextcore-browser) · [Tiếng Việt](README.md)

</div>

---

> **This repository only holds installers, release notes and product documentation.** NextCore Browser is commercial, closed-source software. Every installer here is byte-identical to the one on [homestaynextcore.org](https://homestaynextcore.org/nextcore-browser); verify with the `SHA512SUMS` file attached to each release.

## The problem

Anyone who runs many accounts on the same website hits the same wall:

| Common problem | Result |
|---|---|
| One shared Chrome for every account | Cookies mix, constant logging out and back in |
| Juggling many windows and Chrome profiles | Wrong-account mistakes, no overview |
| A proxy that applies to the whole browser | No per-account network, no way to see which proxy died |
| Automation tools that start a blank browser every run | Login lost on every run, extra login steps to write |
| 2FA codes living on a phone or another app | Tens of seconds lost on every login |
| Repetitive work done by hand across dozens of accounts | Slow, hard to track what is finished |
| AI agents limited to one blank browser | Cannot hand work to many signed-in accounts at once |

## The solution

**NextCore Browser** puts it all in one app:

- **One profile per account.** Each profile is its own Chromium browser with its own cookies, sessions, site data, extensions, proxy and fingerprint. Accounts stay signed in between runs.
- **One place to see and control everything.** The profile list shows live data: status, proxy, latency, 2FA code. Select many profiles and open, close, assign a proxy or tile the windows in one action.
- **Scripts for the repetitive part.** Chain steps into a script, run it across profiles, space the runs out, and pause for you where a decision is needed.
- **AI agents working alongside you.** The app ships an MCP server and a Local API. Claude Code, Cursor, VS Code, Antigravity or your own scripts create, open and drive profiles through them.
- **Your data stays on your machine.** Profiles, cookies and 2FA keys live locally. Machines exchange work through a relay, never passwords, 2FA or cookies.

<div align="center">
<img src="assets/screens/nb-danh-sach.webp" alt="Profile manager: 12 profiles in groups with proxy, 2FA code and status per row" width="860">
<br><sub>Profile manager. Screenshot from the real app, sample data.</sub>
</div>

## Use cases

| Who | What they do with it |
|---|---|
| **Sellers with several shops and channels** | One signed-in profile per shop. Open the right shop without cookies leaking between shops. |
| **Customer-support teams** | One profile per agent and channel. Tile many windows on a second screen to watch them together. |
| **Agencies and content-operations teams** | Manage pages and community groups for many clients, one account set per client. Posting scripts run on a schedule, spaced between groups, with per-group results. |
| **Market research and group data** | A local group store records member counts and posting rhythm. Filter by region, size and rhythm. |
| **QA and web testing** | One profile per user role. Playwright or Puppeteer attach to a profile over CDP. Measure UI at several device widths with the built-in e2e suite. |
| **Developers using AI agents** | Let Claude Code, Cursor or Antigravity create, open and drive many signed-in profiles instead of a blank browser each run. |
| **Software teams running many agents** | NEXTCORE TERMINAL runs Claude Code, Codex, Gemini and Antigravity in the app's tabs. One main machine coordinates a team of agents across machines. |
| **Design teams** | NEXTCORE DESIGN lets several agents draw in parallel, 20 cells per screen (5 states × 4 widths), export PNG or SVG, and share a view link with people who do not have the app. |

> You are responsible for following the terms of the websites you use. NextCore Browser is a management tool and does not change any platform's rules.

## Features

The app has **24 modules** in four groups. Full list and guides in the [docs](https://docs.homestaynextcore.org/nextcore-browser/).

**Browser:** profiles and proxy (HTTP, HTTPS, SOCKS4, SOCKS5) · browser fingerprint (seeded per profile; timezone, language and location follow the proxy IP) · bulk actions · window tiling across monitors · shared proxy store with GB and cost per period · 2FA codes on the row · encrypted `.ncbak` backups (AES-256) · per-profile VPN where a dead node blocks opening so the real IP never leaks.

**Data and customers:** NEXTCORE GROUPCRAWL (local group store with member counts, posting rhythm and each profile's role) · NEXTCORE CUSTOMERPOST (reads posts from customers looking for rooms in Facebook groups) · NEXTCORE CRM, SHEET and PMS (open inside the app, signed in to the right NextCore account).

**Automation:** NEXTCORE AUTOMATIONS (scripts across profiles, schedule or run by hand, record actions on one profile and replay on another) · NEXTCORE AGENT (connect your API keys for Anthropic, OpenAI, Gemini and a dozen more, ordered into a fallback chain) · NEXTCORE MEDIA (images, video and short films using the free quota of signed-in AI-service profiles) · NCB COMMAND (hand work to a team of agents by GitHub issue number).

**For developers:** Local API + CDP · MCP · NEXTCORE TERMINAL · NCB_E2E · NEXTCORE DESIGN.

**Coming:** profile sync across machines · scheduled script runs · multi-user teams with permissions and an audit log of who opened which profile.

## Multi-machine

Machines on the same NextCore account see each other through a relay on the local network, with no port opened to the Internet. Pick one **main machine**; the others take work from it.

<div align="center">
<img src="assets/screens/nb-tram-nhieu-may.webp" alt="Multi-machine settings: main machine, offline machines, Hand over role button" width="760">
</div>

- See every tab on every machine at once: running, waiting for your approval, quota exhausted.
- Hand the main-machine role to another machine with one button in Settings.
- If the app crashes or is killed, it reopens itself within seconds and restores the running profiles.
- Passwords, 2FA, OTP and cookies never pass through the relay.

## For developers and AI agents

```bash
# Open a profile and get a wsEndpoint for Playwright
curl -X POST -H "Authorization: Bearer $NCB_TOKEN" \
  http://127.0.0.1:19880/api/v1/profiles/p_7f3a/start
```

```json
{ "pid": 18244, "debugPort": 52144,
  "wsEndpoint": "ws://127.0.0.1:52144/devtools/browser/9c1e…" }
```

- **MCP built in.** Agents connect to `http://127.0.0.1:<port>/mcp` with a token. Nothing is exposed to the Internet.
- **One-click setup** for Claude Code, Cursor, VS Code and Antigravity: the app writes the config file with a separate token per assistant.
- **Page control with `browser_*`**, the same tool names as the official Playwright MCP, so agents already know them.
- **One MCP session per profile.** Open more sessions to run profiles in parallel; a profile held by one session is refused to another, so two agents never step on each other.

Docs: [Local API](https://docs.homestaynextcore.org/developer/local-api/) · [MCP for AI agents](https://docs.homestaynextcore.org/developer/mcp/).

## Security and privacy

- Profile data stays on your machine. `.ncbak` backups use AES-256.
- Local API and MCP listen on `127.0.0.1` only, with one token per machine.
- The multi-machine relay does not carry passwords, 2FA, OTP or cookies.
- The app must reach `homestaynextcore.org` at least once every 3 days to keep your session.
- Update manifests (`latest*.yml`) carry an ed25519 signature. Verify downloads with `SHA512SUMS`.
- Report vulnerabilities as described in [SECURITY.md](SECURITY.md).

## Download

**Latest: 0.3.191** (2026-11-12). Get the installers and `SHA512SUMS` from the [Releases page](https://github.com/kennetvn/nextcore-browser-releases/releases/latest).

| Platform | File | Size |
|---|---|---|
| **Windows** 10 and 11, 64-bit | `Setup.exe` installer | about 145 MB |
| **Windows** portable | `Portable.exe`, no install | about 145 MB |
| **macOS** Apple Silicon (M1 to M4) | `mac-arm64.dmg` | about 163 MB |
| **macOS** Intel | `mac-x64.dmg` | about 171 MB |
| **Linux** (Ubuntu, Debian), version 0.3.190 | `AppImage` and `.deb` | about 134 to 179 MB |

**Install in three steps, about two minutes:** download the installer; run it (if Windows shows the blue "Windows protected your PC" screen, choose *More info*, then *Run anyway*); sign in to NextCore: the app shows an 8-character code, approve it on [homestaynextcore.org](https://homestaynextcore.org). During the beta there is no limit on the number of machines. A free trial is available before you pick a plan. The app downloads updates itself and applies them when you restart.

## Support

- **App bugs and suggestions:** [open an issue](https://github.com/kennetvn/nextcore-browser-releases/issues/new/choose) with the app version and OS. Never paste passwords, tokens or 2FA keys.
- **Account and plan questions:** contact us through [homestaynextcore.org](https://homestaynextcore.org).
- **Security vulnerabilities:** see [SECURITY.md](SECURITY.md); do not post publicly.

## License

NextCore Browser is commercial, **closed-source** software, used under the [Terms of Use](https://homestaynextcore.org/terms). Details in [LICENSE.md](LICENSE.md).

---

<div align="center">
<sub>© 2026 NextCore · <a href="https://homestaynextcore.org/nextcore-browser">homestaynextcore.org/nextcore-browser</a></sub>
</div>
