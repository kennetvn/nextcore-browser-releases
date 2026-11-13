# NextCore Kernel and NextCore E2E

[← Back to main page](../../README.en.md) · [Tiếng Việt](../kernel-e2e.md)

## What NextCore Kernel is

**NextCore Kernel** is the operating knowledge that runs inside NextCore Browser. It is the brain of two capabilities:

- **NextCore Command:** the role, the way of accepting work and the way of orchestrating the agent team ([details](terminal-command-quota.md)).
- **NextCore E2E:** testing of interface and behavior on real profiles.

What sets it apart from a set of prompts sitting in a repo: Kernel is **not in the installer** and **does not write into your repo**. The app sends the agent exactly the part it needs at run time, and decisions are computed on the NextCore server.

## Every decision has a code and an explanation

Kernel does not return a bare answer. Each decision carries:

- a stable English **decision code**, for example `accepted` (acceptance passed), `kept-session` (keep the live session), `parked-for-release` (waiting for a release);
- a sentence in Vietnamese or English saying **what was considered and what was concluded**;
- a list of next actions for the agent to carry out, in order.

The value ledger merges decisions into one readable sentence, for example «4 decisions: 3 acceptances passed, 1 live session kept».

## Learning from real outcomes

Kernel does not just decide and forget. The app records **the outcome of each decision that has a ticket**: after 24 hours and 7 days, whether the work passed, was reassigned, the issue was reopened, it was falsely reported done, or it exceeded one workday. If a person or agent does something different from the decision within 30 minutes (same task, same issue or same machine), the app records a "done differently" signal.

Privacy of this part: **only codes, action groups and measurements are sent**, no free text, no raw identifiers.

## Designed for real operation

| Property | How it works |
|---|---|
| **Computed on the server, bound to the license** | Decisions are tied to the machine's license and device key. If the license is revoked or expires, it stops immediately. |
| **Tolerates losing the network** | Without a network, the machine keeps running from the copy saved on the machine for up to 24 hours; after that it reports `NCK-0009` (unavailable) until the network is back. |
| **The installer carries no rules** | The knowledge is not in the installer. The server issues a key to a signed-in machine, stored encrypted on the machine; when a machine is revoked, the key is deleted. |
| **Call cap** | Too many calls in an hour report `NCK-0010`; normal use does not hit the cap. |
| **Remotely adjustable thresholds** | The thresholds for watching worker tabs (standing still, hung on a command, waiting to be picked up...) and the default orchestration settings are sent down by the server every 5 minutes, so they can be adjusted without users updating the app. Settings you saved yourself are kept. |
| **Stable error codes** | The `NCK-*` code family covers every unavailable, over-limit and locked situation, so agents handle them correctly instead of guessing. |

## Right of use

You may use NextCore Command and NextCore E2E for your own work. NextCore Kernel may only be **applied (Apply)**, not **extracted (Extraction)** or **distilled (Distillation)**: you and your AI agents call the software to receive results, and do not read, copy or reverse-engineer the rules, prompts or scoring methods from many applications. Details in [LICENSE.md](../../LICENSE.md) and [Terms of Use, section 7](https://homestaynextcore.org/terms).

## NextCore E2E: measure pages on real profiles

The `ncb_e2e*` set measures your web pages **on real, already logged-in profiles**, with no need to set up test accounts. An agent calls the test for your repo and gets back a report: what was measured, what failed, regressions, screenshots, and the next step to take. The scoring scripts live inside NCB and are not sent to the agent.

| Tool | Measures |
|---|---|
| `ncb_e2e` | One URL across many screen widths × light/dark × touch screen × slow or offline network: horizontal overflow, clipped text, small tap targets, contrast, console errors, security headers |
| `ncb_e2e_lo` | As above for a whole list of URLs, split across several profiles running in parallel (the number of profiles depends on free RAM and the machine's cores) |
| `ncb_e2e_toc_do` | Runs Lighthouse right inside the profile's browser |
| `ncb_e2e_seo` | Crawls the site on the same domain (robots.txt, sitemap.xml, internal links); plus readiness for AI search engines: llms.txt, AI bots in robots.txt, structured data by page type |
| `ncb_e2e_vai` | Opens the same URL list with several profiles of different roles (guest, staff, admin) to compare who sees what |
| `ncb_e2e_dinh_vi` | Before testing, identifies the real target: the website, the Dev build or the release build of the app; which code file a route corresponds to; whether the running build already has the commit to be tested. If the build lacks the change, it stops and says so, instead of testing the old build and reporting green |
| `ncb_e2e_kich_ban` | Runs a multi-step scenario (click, type, select, measure). A scenario only «Passes» when the record has the target, build, commit, at least one result-checking step and a timestamped screenshot; an empty check is rejected |
| `ncb_e2e_tu_issue` | Reads the `- [ ]` acceptance boxes of a GitHub issue, opens the target page on a profile, takes the real role and name of elements, and writes a scenario: one group of steps per criterion, with at least one checking step |

`ncb_e2e` and `ncb_e2e_lo` accept `quyTac` to set project-specific thresholds (tap target size, AA or AAA contrast level, LCP/CLS thresholds, ignored regions).

### View mode: see the agent really click

With `xem` on, the profile window shows NextCore Browser's cursor flying to each target, typing each key, and rippling only when the page really receives the click. Before each click the app aims at the target: if the target is covered, not yet visible or still animating, it does not click. When several agent sessions watch the same page, each session gets its own cursor color. Pass `record: true` to record video to a `.webm` file with a `.chapters.vtt` chapter file, one chapter per step.

## Why this matters

Agents often report «done» and «green» too early. Kernel and E2E put two checkpoints in exactly that place:

- **Acceptance with evidence.** Command does not accept a task just because the tab reported done.
- **Tests never report green when nothing was tested.** E2E rejects empty scenarios, identical screenshots and selectors that match nothing, and stops when the running build does not yet contain the commit to be tested.

## Detailed documentation

[About NextCore Kernel](https://docs.homestaynextcore.org/nextcore-browser/tong-quan/#ve-nextcore-kernel) · [NextCore E2E in MCP](https://docs.homestaynextcore.org/developer/mcp/)
