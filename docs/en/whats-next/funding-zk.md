# Funding ZK (future)

**Status:** Exploratory — **not** part of the current human product scope. Documented here as **what's next**.

## Vision

Anonymous, conditional crowdfunding on Stellar:

* Donate without linking wallet to identity.
* Express one opinion per human per campaign (ZK nullifier scoped to campaign).
* Release funds on milestones (e.g. 2-of-3 multisig) or refund if goals fail.
* Optional yield on idle funds (DeFindex / Blend integration explored).

## Why it's Layer 3

| Layer | Role |
|---|---|
| 1 | Prove unique humanity |
| 2 | Anonymous verified opinions |
| 3 | Anonymous verified economic participation |

Layer 3 composes Layer 1 + 2 primitives but adds escrow, yield, and campaign logic — a separate product surface.

## Explored components (code exists, not productized)

| Piece | Description |
|---|---|
| `funding_opinion` circuit | Campaign-scoped nullifier + opinion proof |
| `campaign_controller` | Non-custodial release / refund rules |
| `funding/api` | Campaigns, donations, milestones |
| DeFindex integration | Yield on deposited XLM (testnet validated) |
| Trustless Work integration | Escrow single-release (testnet validated) |

## Privacy model (sketch)

* **Donation:** ephemeral wallet — not linked to KYC address.
* **Opinion:** `platformId` per campaign + nullifier (one voice per human per campaign).
* **On-chain:** zero PII.

## When it ships

After Layer 1 public SDK, production issuer path, and Layer 2 stabilization. Follow [Roadmap](roadmap.md) for priorities.

## Related

* [Architecture overview](../architecture/overview.md)
* [Roadmap](roadmap.md)
