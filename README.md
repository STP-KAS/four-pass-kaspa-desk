> **Experimental only. Not a product.**
>
> Do not use wallet integrations on this GitHub. STP remains a clown. [DISCLAIMER.md](DISCLAIMER.md)

# Four-pass Kaspa desk

**What.** One public note after reading the STP-KAS GitHub, rechecking live endpoints, and running the four Cursor starters (deploy, database, plan, debug) against that desk — not against a new app.

**Why.** The account already has a front door ([kaspa-dapps](https://github.com/STP-KAS/kaspa-dapps)), a pin encyclopedia ([kaspa-master-file](https://github.com/STP-KAS/kaspa-master-file)), and a private freeze note ([tn10-indexer-stall-2026-09](https://github.com/STP-KAS/tn10-indexer-stall-2026-09)). Those files disagree with each other on dates, counts, and node pins. A stranger landing today cannot tell which sentence is the board.

**This repo.** New. Named at will. Existing STP-KAS repositories were **not** edited. No issue, pull request, or comment was posted anywhere. One public GitHub only.

**Not.** Kaspa core. An audit. A product. A deploy of sixpack. A patch to api-tn10. A wallet. A seed.

Checked **29 Sep 2026**, about **11:14Z** (13:14 CEST), from the Windows desk. Evidence: [`evidence/live-2026-09-29T1114Z.txt`](evidence/live-2026-09-29T1114Z.txt). Local kaspad was not started. The recovery phrase was not opened.

---

## What / why / sources

### What this pass actually did

| Step | What | Why | Source |
| --- | --- | --- | --- |
| Absorb GitHub | Listed STP-KAS with `gh` as **STP-KAS**. 74 public, 7 private. Read profile README, kaspa-dapps (README, PLAN, SOURCES, RAILS), kaspa-master-file (README Now, START-HERE, STP-REPOS, TN10-FIELD-2026-09-29), tn10-indexer-stall README, tn10-vprogs-stress-findings README, declared-ply README+VISION, sixpack.wtf README, groks-wallet README. | The desk law is “open the link.” Overlapping GitHubs are the product the desk keeps shipping. | `gh api user`, `gh repo list`, file contents via GitHub API |
| Live REST | Cache-bust and bare `/info/health` on api-tn10. `/info/blockdag` on TN10 and mainnet. coinsupply, blockreward. | Front-door numbers are 15 Sep. Encyclopedia numbers are 27–29 Sep. They cannot both be “now.” | This fetch, 11:14Z |
| Live sites | sixpack.wtf HTTP 200. GitHub Pages freeze lab HTTP 200. | “Deploy my prototype” already has a shareable link. The gap is truth, not hosting. | https://sixpack.wtf/ · https://stp-kas.github.io/grok-heavy-showcase/ |
| Pin check | rusty-kaspa latest **v2.1.0**. SilverScript latest **v1.0.0**. Argent tags **0**. KCC-0 file **Final**. vprogs #165 **open, not draft, not merged**, head `b5c48193`. | PLAN.md and kaspa-dapps constitution still say node **v2.0.1**. Findings README still calls #165 a draft at `bcebf59`. | GitHub API, this pass |
| Do not | No `git push` to existing remotes. No comment on vprogs, kccs, Kas-Smiths, or X. No miner start. No second spender. | Standing desk rule since 24 Sep (master file **This desk** row), plus the user order: do not reply anywhere; do not change existing repos yet. | kaspa-master-file README · this chat |

### What the four starters map to on this desk

The screenshot was Cursor’s four starters. Applied here:

| # | Starter | Honest object on this GitHub | Verdict this pass |
| --- | --- | --- | --- |
| 1 | Deploy my prototype | [sixpack.wtf](https://sixpack.wtf) is already public. [grok-heavy-showcase](https://stp-kas.github.io/grok-heavy-showcase/) is already Pages. [declared-ply](https://github.com/STP-KAS/declared-ply) is a crate you run locally, not a node. | Deploy is done. Do not add a fifth public costume. |
| 2 | Review my database | The public TN10 “database” is simply-kaspa-indexer Postgres behind [kaspa-rest-server](https://github.com/kaspa-ng/kaspa-rest-server) v2.3.0, not a schema this desk owns. Risky access rule: treating Cloudflare **200 STALE** as live, and treating `/addresses/.../full-transactions-page` as a receipt after 25 Sep. | Indexer accepted-tx clock still frozen. Block ingestion is not. |
| 3 | Start with a plan | [kaspa-dapps/PLAN.md](https://github.com/STP-KAS/kaspa-dapps/blob/main/PLAN.md) already exists. The **Now** pin inside it is stale (node v2.0.1). | Keep the track split. Recheck the pin row before any new code. |
| 4 | Debug an issue | api-tn10 accepted-tx stall, plus idle miner slots, plus campaign HTML-instead-of-JSON. | Stall **verified** again at 11:14Z. Cause **unproven**. |

---

## Live numbers (this pass)

Do not quote the 15 Sep table in kaspa-dapps as current.

| What | 15 Sep (kaspa-dapps / SOURCES.md) | 29 Sep 11:14Z (this repo) |
| --- | --- | --- |
| Mainnet virtual DAA | 540,389,037 | **552,601,692** |
| Circulating KAS | 27,701,371,838.337 | **27,728,028,318.06688027** (from 2,772,802,831,806,688,027 sompi) |
| Block reward | 2.18267645 | **2.18267645** (unchanged) |
| TN10 virtual DAA | 571,008,588 | **583,495,623** (`/info/blockdag`, HTTP 200) |
| STP-KAS public repos | 42 | **74** public, **7** private |
| Node release | rusty-kaspa v2.0.1 in PLAN constitution | **v2.1.0** latest GitHub release (22 Sep) |

### Database review (api-tn10)

Same freeze the private stall note already named. Rechecked; still true.

| Probe | Result | Meaning |
| --- | --- | --- |
| `/info/health?nc=…` | HTTP **503**, `cf-cache-status: MISS` | Live health of the rest-server + indexer |
| database.isSynced | **false** | Do not use this API as a receipt |
| acceptedTxBlockTime | **1790366138262** | Still **25 Sep 2026 19:55:38.262Z** |
| acceptedTxBlockTimeDiff | ~314,307 s | About **3 d 15 h** behind wall clock at 11:14Z |
| database.blueScore vs kaspad | 571974867 vs 571974900 (diff 27) | **Blocks are still ingesting** |
| kaspad on that miss | serverVersion **2.0.0**, p2pId prefix `28916cd5` | Pool of backends; versions mix 2.0.0 / 2.0.1 / 2.1.0 across the day |
| bare `/info/health` | HTTP **200**, `STALE`, blueScore **568825293**, acceptedTxBlockTime **1790365505207** (25 Sep 19:45:05Z) | Cloudflare costume. Explains the fake 19:45 freeze |

Risky access rules, for anyone still wiring a bot to this host:

1. A 200 on `/info/health` without a cache-bust is not a synced indexer.
2. Address history on this host is frozen at the 25 Sep coinbase. Mining after that second will not show up here.
3. Node-backed routes (`/info/blockdag`, virtual-chain blue score, blocks-by-bluescore) can be live while the accepted-tx DB is dead.
4. The rest-server tag **v2.3.0** is not kaspad. Mainnet openapi is **v2.4.1**. Do not weld those strings to rusty-kaspa **v2.1.0**.
5. Uniqueness for KNS-class names is still indexer FCFS. An indexer that stalls is a uniqueness stall, not consensus.

Cause of the stall: **unproven**. Time correlation with the 25 Sep storm (~6k processed-body TPS on the desk node at 19:55Z) is in the private stall note. Time correlation is not causation. This desk does not have indexer logs.

### Deploy review

| Surface | Live? | Honest limit |
| --- | --- | --- |
| https://sixpack.wtf | yes, HTTP 200 | Site. Not Kaspa core. Not a wallet. Landing + rails + faucet + help desk. |
| https://stp-kas.github.io/grok-heavy-showcase/ | yes, HTTP 200 | Freeze lab pages. Dual rail. Not USD. |
| https://vprogs-tt.izio.fr/ | not re-hit this pass (master file: 200 on 28 Sep) | Hosted demo. **Not** “vProgs live.” Needs a key this desk does not paste. |
| declared-ply | public crate | Two functions. `cargo test` / `cargo run --example boards`. Not a submitter. |
| stillpay-mainnet | public | Broadcast gated. Does not submit. |

Do not deploy another till. PLAN already says one till: Ishum. stillpay, kaspa-till, xai-reasoning-3, and sixpack’s faucet are extra costumes of “pay something.”

### Plan review (what to do, in order, without touching old repos)

Keep [PLAN.md](https://github.com/STP-KAS/kaspa-dapps/blob/main/PLAN.md) track split. Change only the pin row, later, in that repo — **not in this pass**.

1. Treat **kaspa-master-file Now** as the board. Treat kaspa-dapps as the door. If they disagree, the encyclopedia wins until the door is updated.
2. Node pin for new work: rusty-kaspa **v2.1.0** (`01b532e8`). Compiler pin: SilverScript **v1.0.0** (`3ed9733`). Do not bump KagenC / agenc-on-kaspa off `a41a333b` until silverscript#256 is actually fixed in a tag.
3. Testnet spend: **TN10 only**. Do not use api-tn10 address history as a receipt until `acceptedTxBlockTime` moves.
4. No wallet inject. Tombstone stays [wallet-integration](https://github.com/STP-KAS/wallet-integration).
5. Bind x402 at **elldeeone/kaspa-x402 `v1.0.0-rc.1`**. Not `main`. Not mainnet. HTTP 402 is not x402.
6. Dual rail: keypad fiat, settle native KAS, USDT labelled guest, never gas.
7. vProgs / tic-tac-toe / DAGKnight stay **out of path** as products. declared-ply is a rule split, not a ship claim.
8. BitCoffee: review repo only. Do not absorb KUSD as the till asset.

Monday tripwire from PLAN.md is still the right list, with one extra line: **cache-bust api-tn10 `/info/health`**. If that 503-and-frozen-clock is still there, say so. Do not quote the STALE 200.

### Debug review

| Bug | Status this pass | What would close it |
| --- | --- | --- |
| api-tn10 accepted-tx clock stuck at 25 Sep 19:55:38Z | **Verified** live | Indexer operator logs around that second. This desk cannot close causation. |
| Cloudflare STALE 200 on bare health | **Verified** live | Clients must cache-bust or ignore 200+STALE |
| Mixed kaspad versions behind the same REST host | **Verified** (2.0.0 on this miss; 2.1.0 earlier today in TN10-FIELD) | Operator. Do not treat one p2pId as “the TN10 node” |
| Fifteen miner processes ≠ fifteen hashers | Stated in TN10-FIELD 29 Sep; not re-sampled this pass (would start looking at local PIDs) | Supervisor should test “synced and hashing,” not “process still named kaspa-miner” |
| Campaign STATUS.md behind finished log | Stated in declared-ply / TN10-FIELD: 1,842 accepted sends, 885,963 send_fail, 919,418 HTML-instead-of-JSON | Clients must fail closed on HTML. Do not restart that campaign against a frozen indexer |
| vprogs #165 called “draft” in stress-findings | **Stale.** Now open, `draft: false`, head `b5c48193`, still unmerged | Recheck before quoting. Do not comment. |

---

## Inconsistencies

Disagreements **inside STP-KAS files**, or between those files and a live fetch. This repo does not patch them.

| Where | Older sentence | What holds today |
| --- | --- | --- |
| Node pin | kaspa-dapps constitution §7 and PLAN.md “Now”: rusty-kaspa **v2.0.1**. groks-wallet 21 Sep row in STP-REPOS: v2.0.1. windows-p2p-node-guide row: v2.0.1. | Master file Now and groks-wallet Windows desk section: **v2.1.0**. GitHub latest release: **v2.1.0**. Guest tic-tac-toe still pins rusty-kaspa `eb0a856`. |
| Repo census | SOURCES.md: 42 public. STP-REPOS.md (21 Sep): 54 owned, 52 public, 2 private. Master file 26 Sep: 76 owned, 73 public, 3 private. | This pass: **74 public, 7 private**. Private now includes tn10-indexer-stall, blue-line-tictactoe, tn10-stress-tests, grok-desk-tn10, plus the older journals. |
| Health 200 | Anyone quoting bare api-tn10 health as synced | STALE body, kaspad 2.0.1, blueScore 568825293, freeze stamp 19:45:05Z. Real freeze stamp is **19:55:38Z** on a cache miss. |
| Two freeze times | Other bots’ 19:45:05Z vs 19:55:38Z | Explained in the private stall note. Rechecked. Same split. |
| vprogs #165 | tn10-vprogs-stress-findings (26 Sep): draft, head `bcebf59` | 29 Sep: **not draft**, head **`b5c48193`**, still open, still unmerged |
| vprogs branch names | tictactoe README at `098be674`: check out `fix/settlement-watch-wedge` | Cargo.lock pins `fix/settlement-watch-state-neutral` `07d486dd`. declared-ply already tables this. |
| `release-candidate` | Sounds like a release | Branch tip, not a GitHub release. vprogs has **no** release. Master still `f9b84a8` (28 Jul). |
| SilverScript tag vs stamp | Tag v1.0.0 `3ed9733` | Compiler still stamps 0.1.0; `pragma silverscript ^1.0.0` rejected (declared-ply table). Argent: no tag. |
| KCC-0 | kccs README index still Draft. kaspaexplained `/status` still Last Call (master file Referee lag). | File header **Status: Final**. Rechecked this pass. |
| STP-REPOS vs live README | STP-REPOS is a 21 Sep full read | It still says “52 public” and lists kns-kasware-tn10-test as private. That file is a receipt. It is not the board. |
| grok-desk-tn10 vs live miners | README: supervisor stopped, target 20 | TN10-FIELD 29 Sep: supervisor alive, target **15**, three hashing, twelve idle “not synced” |
| groks-wallet STATUS.md | “refresh from local balance.mjs, not STATUS.md” | Same class of bug as campaign STATUS.md: a card that lags the log |
| Receive index 0 = 0 | Easy to read as empty stress wallet | TN10-FIELD: coins were on indexes 10–1509 on 25 Sep. A public zero is not an empty wallet. Phrase not opened this pass. |
| Network TPS | Older storm READMEs quote processed-body peaks | Round 7 already measured overstatement B/A ≈ 1.337. “12,175 TPS” is not selected-chain throughput. |
| Three KaChat copies | stp-kachat, kaachat-desktop, kachat-test-with-silver | STP-REPOS already marks sprawl. Production name is stp-kachat. |
| Four till-shaped repos | ishum, stillpay-tn10, stillpay-mainnet, kaspa-till, plus xai-reasoning-3 | PLAN: one till. The GitHub does not obey its own plan. |
| x402 verdict pointer | Profile table: “x402 verdict → sixpack.wtf” | Adversarial pass lives in x402-vs-grok. sixpack is the site. 402-is-not-x402 is the costume catalog. Three doors for one bind. |
| Front door live table | kaspa-dapps §6 “Live this pass (15 Sep)” | Still on the front door. Encyclopedia Now is 29 Sep. Door lost. |
| LLM forum | “Do not post reports. The clock does not run.” | This repo is a report. It is a **new** public GitHub, not a post on that forum, and not a comment on existing repos. |
| silverscript vs rusty v2.1.0 | KagenC / agenc pin `a41a333b` on purpose (#256) | Python SDK crate pins silverscript `3ed9733` and rusty `a41a333b`, not v2.1.0. An SDK release is not a compiler fix. |
| Hosted tic-tac-toe vs declared-ply | Same two cells | Guest `drain_pending` can open the next round. Batch lands one ply; extra cell is `Retry`. The interesting bug is that split. |
| Private vs public TN10 | grok-bot-vprogs private; public round 1–8 copies; stress-findings public; indexer stall private | The stall note is the one that should be public if the desk wants strangers to stop trusting api-tn10. It is still private. This README carries the live recheck only. |

Do not weld (copied from the encyclopedia, still true): Argent tag, KCC-20 Final, DAGKnight shipped, vProgs product, tictactoe = vProgs live, x402 mainnet, `release-candidate` = a release, REST v2.3.0 = a node release, api-tn10 health 200 = a synced indexer, a research.kas.pa thread = consensus.

---

## What I can do better

This is the agent that wrote this file, not a protocol claim.

| Failure | Why it happens | Better |
| --- | --- | --- |
| Quote a front-door “live” table | kaspa-dapps is labelled the door, so it feels current | Recheck endpoints every pass. Date the quote. If the door lags the encyclopedia, say **door lag**, do not silently mix them. |
| Treat GitHub description / STATUS.md / Cloudflare 200 as a measurement | Fast, looks official | Prefer cache-bust, wRPC UTXO, and finished logs. Cards lie. |
| Count processes as capacity | 15 `kaspa-miner` PIDs look like 15 hashers | Sample CPU / last log line. Synced is a property of the node, not of the child still being alive. |
| Equate time correlation with causation on the indexer | The storm is ours and the clock froze during it | Keep **unproven** in the same sentence as the TPS number. Do not file that as a fact upstream. |
| Comment on upstream to be helpful | Old pass on vprogs#165 | User order and desk standing rule: **zero public comments**. Put the note in a new repo or on the encyclopedia. |
| Clone the whole account into another encyclopedia | 74 public repos invite another map | One dated four-pass. Point at kaspa-dapps and kaspa-master-file. Do not grow a third front door. |
| Skip tests that need a sandbox | This machine blocked an isolated `cargo test` of declared-ply and a second address-page fetch | Next pass: run `cargo test` and `cargo run --example boards` inside declared-ply **without publishing that crate again**. Quote the 9 tests from its README until that runs. |
| Weld HTTP 402, x402 RC1, Ishum, and the faucet | All look like “pay on Kaspa” | Keep the PLAN names: one envelope, one till, faucet is ops. |
| Use processed-body TPS in a title | It is the number in the node log | Convert with the round-7 factor, or say “block-body counter.” |
| Open a seed to “confirm empty” | Receive-0 is 0 | Do not. Say what was not checked. |
| Improve by editing 74 READMEs in one night | The user said not yet | Ship **one** public note. Patch the door and STP-REPOS when asked. |

What this agent still cannot do from here: read simply-kaspa-indexer logs, restart Cloudflare, merge vprogs#165, tag Argent, or make KCC-20 Final. Those are other people’s repos.

---

## To improve (the GitHub, later)

Do this **when** the user says the existing repos may change. Not done in this pass.

1. **kaspa-dapps:** replace §6 live table with a one-liner: “Numbers live in kaspa-master-file Now; last door sample was 15 Sep.” Bump constitution node pin to v2.1.0. Leave the dual-rail law alone.
2. **kaspa-dapps/PLAN.md:** same node pin. Add tripwire #11: cache-bust api-tn10 health.
3. **STP-REPOS.md:** either retitle as “21 Sep receipt” in the first line (it already dates itself) or run a new full read. The 52/2 census is wrong.
4. **Publish or extract** the indexer stall facts (already duplicated here and in TN10-FIELD). Strangers still hit api-tn10.
5. **One till, one 402, one KaChat** in the profile table. Move the rest under “receipts.”
6. **Miner supervisor:** restart when last line is “not synced,” not when the process dies.
7. **Campaign / faucet clients:** if the body starts with `<!doctype`, stop. 919,418 of those is enough.
8. **Do not restore inject.**
9. **Do not start a fifth public “findings” repo next week.** Update this one, or fold a dated section into SNAPSHOT-HISTORY.

---

## Sources (opened this pass)

Desk, read not cloned into this repo:

- https://github.com/STP-KAS
- https://github.com/STP-KAS/kaspa-dapps
- https://github.com/STP-KAS/kaspa-master-file
- https://github.com/STP-KAS/kaspa-master-file/blob/main/TN10-FIELD-2026-09-29.md
- https://github.com/STP-KAS/tn10-indexer-stall-2026-09 (private; not modified)
- https://github.com/STP-KAS/tn10-vprogs-stress-findings
- https://github.com/STP-KAS/declared-ply
- https://github.com/STP-KAS/sixpack.wtf
- https://github.com/STP-KAS/groks-wallet

Upstream / live:

- https://api-tn10.kaspa.org/info/health
- https://api-tn10.kaspa.org/info/blockdag
- https://api.kaspa.org/info/blockdag
- https://api.kaspa.org/info/coinsupply
- https://api.kaspa.org/info/blockreward
- https://sixpack.wtf/
- https://stp-kas.github.io/grok-heavy-showcase/
- https://github.com/kaspanet/rusty-kaspa/releases/latest
- https://github.com/kaspanet/silverscript/releases/latest
- https://github.com/kaspanet/vprogs/pull/165
- https://github.com/kaspanet/kccs/blob/main/kcc-0000.md
- https://github.com/argent-lang/argent (tag list)
- https://github.com/kaspa-ng/kaspa-rest-server (named by the encyclopedia as the rest-server)
- https://github.com/supertypo/simply-kaspa-indexer (named by the encyclopedia as the DB)

Already proven on other STP-KAS dates, not re-run here: grok-heavy-showcase `npm test` 10/10 (15 Sep), Ishum till tx `a7a04250…28e7` accepted, BitCoffee lifecycle txs accepted, declared-ply 9 unit tests as documented in that README.

---

## Proven / unproven (short)

**Proven on 29 Sep 11:14Z**

- api-tn10 accepted-tx clock is still `1790366138262`.
- Uncached health is 503; bare health is a STALE 200.
- Block DAG on that host still answers (TN10 virtual DAA 583,495,623).
- sixpack.wtf and the freeze-lab Pages URL answer 200.
- rusty-kaspa latest tag is v2.1.0. Argent has no tag. KCC-0 file is Final. vprogs#165 is open and not a draft.

**Unproven**

- That the 25 Sep storm broke the indexer.
- Any reorg at the freeze second (n0 INFO logs did not print one; absence is not proof).
- kascov’s 17 Sep 907-block report (self-report; this desk’s n0 logs start 24 Sep).

**Not checked this pass**

- declared-ply `cargo test` on this box (blocked; use the crate’s own README until re-run).
- Opening the phrase / full HD rescan.
- Mainnet node (retired).
- Commenting anywhere (forbidden).

---

> **Standard disclaimer.** This GitHub, not the topic above.
>
> Intentions are good; thought process is questionable. STP remains delusional. Si vis pacem, para bellum.
>
> Intern at https://sixpack.wtf/
> X: https://x.com/StppStp · GitHub: https://github.com/STP-KAS
