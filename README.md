# Leveraged Strategies

A free educational reference documenting the mechanics of six major leveraged ETF strategy frameworks. No paywalls, no registration, no financial advice.

**Live site:** https://azqato.github.io/leverage/

---

## What this site covers

Six strategies, each with its own dedicated page covering five sections: Overview, Rules and Logic, Performance Notes, Risks and Caveats, and Resources.

**Quarterly value-averaging signal plans (Jason Kelly)**
- **3 Sig**: targets 3% quarterly growth in a stock index fund (IJR or SPY) against a bond buffer. The unleveraged, conservative tier.
- **6 Sig**: targets 6% quarterly growth in MVV (2x leveraged midcap). The middle tier between 3 Sig and 9 Sig.
- **9 Sig**: targets 9% quarterly growth in TQQQ (3x Nasdaq-100) with two additional safeguards for managing 3x leverage.

**Daily and event-driven algorithms**
- **TQQQ For The Long Term**: a daily rules-based algorithm using SPY's 200-day moving average and 10-day RSI to rotate among TQQQ, UVXY, TECL, UPRO, SQQQ, and TLT. Created by u/derecknielsen (2022).
- **Holy Grail**: a TQQQ FTLT variant using TQQQ's own 200-day SMA, adding SOXL for bear-mode mean reversion and BSV as the defensive hold. Event-driven rebalancing with a 5% corridor.

**Leveraged risk parity**
- **HFEA**: Hedgefundie's Excellent Adventure. A quarterly-rebalanced portfolio of 55% UPRO and 45% TMF, pairing 3x leveraged equities with 3x leveraged long-duration Treasuries.

---

## Who this is for

Self-directed investors researching leveraged ETF strategies before committing capital. The site is written for readers who want to understand how a strategy actually works, including its failure modes, without wading through scattered forum threads, paywalled newsletters, or community backtests with implementation errors.

---

## Status

Live. All six strategies are fully documented.

---

## Documentation

Technical documentation, design system, setup instructions, and full project context: [/docs](docs/)
