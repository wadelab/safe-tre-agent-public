# Measurements

Each file here is the output of a measurement script run against
safe-tre-agent v0.14.6 (commit `245a196` of 2026-11-12) on
synthetic data. They are the evidence for the numbers in the
[README](../README.md) and in the paper. The files are JSON, written by the
scripts that produced them; field names follow the code.

## The cost of each control

| File | What it measures |
|---|---|
| `composite_cost.json` | Adding an external output checker to the built-in rules: 23 more cells withheld of 4,684, and complete Gaussian fits falling from 60 to 55 of 539 models. |
| `dispersion_sensitivity.json` | How many Gaussian models lose their standard errors when the dominance rule also applies to sums of squares: 36 of 539. |
| `rounding_distortion.json` | What rounding counts to a multiple of 5 does to released values and to models fitted from them. |
| `timing_channel_standin.json`, `timing_channel_external.json` | Response time against the size of the group asked about, at the gateway, with the built-in checker and with an external one (Spearman 0.86 unpadded). |
| `timing_channel_web_unpadded.json`, `timing_channel_padded.json` | The same at the web boundary, before and after padding: pairs of withheld groups that can be put in size order fall from 7 of 15 to 0 of 15. |
| `refusal_timing.json` | How long each kind of refusal takes as a person's remembered history grows, and how well one padded response tells them apart. |
| `rank_audit_cost.json` | The time to check each request against everything the person already holds, over honest workloads in several orders: the longest check takes 1.7 s. |
| `lineage_cost.json` | Time per request against the length of the remembered history. |
| `probe_limit_demo.json` | How many days honest and probing workloads take under each query budget and probe limit. |

## Attacks across sessions

| File | What it measures |
|---|---|
| `tracker_per_session_memory.json` | Trackers spread over many sessions, against a gateway that remembers only within a session: the exact totals of 2,400 of 2,400 targeted people are recovered. This is the design the lifelong memory replaced. |
| `tracker_lifelong_memory.json` | The same attack by one person against lifelong memory: 0 people recovered. |
| `tracker_colluding_review.json`, `tracker_colluding_monitor.json` | Several people pooling their answers. When the deployment holds such releases for review, none is recovered; when it only reports them, every target is recovered and every release is reported. This is the stated residual across people. |

## Checks on what was released

| File | What it measures |
|---|---|
| `smt_oracle_findings.json` | A constraint solver's verdict, for each replayed red-team session, on whether the released numbers determine any person's or small group's total; it agrees with the session auditor on 38 of 38 sessions. |
| `smt_solve_times.json` | How long the solver takes per session and per question. |
| `certify_demo-single.json` | Every session of up to three sums on the demonstration catalogue's single-dimension tables (238 releases, 506 people): which would pin down fewer people than the threshold, and whether the live gateway releases them (0 of 40 replayed). |
| `policy_sensitivity.json` | The 9 numeric policy settings varied together over 100 combinations, with every attack and two honest workloads run at each: disclosures, refusals and releases per setting. An attack discloses at 0. |
