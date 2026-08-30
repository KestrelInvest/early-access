# Example tester profiles

**These are illustrative scenarios, not real testers.** They show how different allocations exercise different parts of Kestrel, and the kind of report each one is likely to produce — so you can see where your own testing fits. Real cohort feedback lives in [Issues](../../issues) and [Discussions](../../discussions), never here.

---

### Profile A — "Capital preservation first"
**Allocation:** Roost — 50 % equity (SPY 25 / SCHD 15 / AAPL 10), 50 % Treasuries.
**What this tester watches:** the Treasury sleeve. Does the tracker's cash line hold steady while equities move? Does a 6 % equity rally trip the band, and does the re-true-up sell equity back into SGOV rather than the other way round?
**Typical report:** "Roost tracker moved +0.4 % on a day SPY was flat — is the SGOV accrual right?" (Exactly the kind of pricing-source question Phase 1 exists to surface.)

### Profile B — "Set it and forget it"
**Allocation:** Perch — 70 % stocks, 5 % metals (GLD 3 / SILV 2), 25 % Treasuries.
**What this tester watches:** small-position behaviour. Silver is a 2 % target; the relative band floor should stop it churning on noise. They also watch whether the holdings table on the portfolios page matches the live tracker's units.
**Typical report:** "Perch shows 8 holdings on /portfolios but the homepage tracker lists 7 — which is right?" (A real class of drift between page and tracker; the fix is a single source of truth for units.)

### Profile C — "Growth with a spine"
**Allocation:** Soar — 85 % stocks led by NVDA/QQQ at 20 % each, 5 % metals, 10 % Treasuries.
**What this tester watches:** single-name dispersion. When NVDA runs, does the engine trim it into the laggards and the sleeve on the next band trip, and does the 20 h cooldown hold?
**Typical report:** "NVDA hit 24 % of Soar yesterday but the tracker still shows target weights — where's the drift view?" (A feature request: drifted weights next to targets.)

### Profile D — "Risk capital, eyes open"
**Allocation:** Apex — 90 % stocks across eight names, 10 % metals, no cash.
**What this tester watches:** liquidity gates. SPCX and MSTR are the names most likely to fail spread/depth screening at rebalance time; this tester wants to see the substitution ladder hold rather than force-sell.
**Typical report:** "PLTR is in the Apex table but not in the tracker units — is it excluded?" (Yes, until its tokenized mint passes verification; the README now says so.)

### Profile E — "The deep end"
**Allocation:** Edge — five Solana memecoins, 20 % each.
**What this tester watches:** entries and rails. New names enter six hours after their pool opens, never in the launch hour; the tracker discloses that thin early liquidity isn't achievable at size. This tester tries to catch an entry that violates the rule or a mark that doesn't match the pool.
**Typical report:** "fone entry shows 2:04 AM ET at $0.00565 — the pool's 2:04 candle closed at $0.0057, close enough, but where's the source?" (Answer: GeckoTerminal minute close; a link per entry is a reasonable ask.)

---

**Where you fit:** pick the profile closest to how you'd actually invest, test that portfolio hardest, and file what you find. Cross-profile reports — "Edge tracker refreshes but Perch doesn't" — are the most valuable of all.
