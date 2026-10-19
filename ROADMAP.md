# Roadmap

Two items are planned. Each one stays marked Planned until it runs.

## Trading system: Planned

A trading system built on the risk rules I've traded by for five years. It trades paper money first and moves to real money only once it earns it on paper. Every decision gets logged.

Status today: planning. The code isn't written yet, no accounts are connected and no money is involved.

### The rules

These come from the paper ledger on [kayabraham.com](https://kayabraham.com).

| Rule | What it says |
|---|---|
| R1 | Paper first, for weeks, with written exit criteria before any real money. |
| R2 | A daily loss cap. When the system hits it, it stops for the day, and the stop can't be overridden. |
| R3 | Leverage capped at 3x. |
| R4 | A trade needs signal confluence: more than one independent signal has to agree. |
| R5 | A kill switch I can hit from my phone. |
| R6 | Every decision logged with its inputs, the reasoning and the outcome. |
| R7 | Wallet addresses and referral links stay off everything I publish. |

It's judged on drawdown and consistency over weeks. The equity curve on the site reads a `ledger.json` file, published with a delay once the paper run starts. It stays empty until then.

## Expansion Engine showcase: Planned

A redacted showcase of the [Expansion Engine](engine/): a public write-up of the design with counts only. Customer names, contract values and internal numbers stay out.
