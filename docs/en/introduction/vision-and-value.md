# Vision and value proposition

## What we are building

A system where **each person registers and validates their real identity once**, in a way that is:

* **Unique** — one real person = one identity (anti-Sybil).
* **Anonymous** — no personal data on the blockchain.
* **Verifiable on Stellar** — proofs checked inside Soroban contracts.

On that foundation, **human** enables a **public square for verified humans**: opinions, articles, and research that carry the weight of a real person without exposing who they are.

## Value for the ecosystem

| Stakeholder | Benefit |
|---|---|
| **Users** | Prove humanity once; participate privately across apps |
| **dApps on Stellar** | Gate regulated features with `is_verified(address)` — no PII handling |
| **Society** | Reduce bot noise; elevate discourse from verified humans |

## Design principles

1. **PII stays off-chain** — only commitments, nullifiers, and proofs touch the chain.
2. **ZK does the heavy lifting** — the contract never sees documents or biometrics.
3. **Layered architecture** — identity core (Layer 1) is reusable; applications (Layer 2+) compose on top.
4. **Honest scope** — mocks and testnet limitations are documented openly.

## The two bridges between layers

Applications can consume Layer 1 identity in two ways:

| Bridge | Use case | Linkability |
|---|---|---|
| `is_verified(address)` | Generic dApps (ramps, pools, RWAs) | Pseudonymous (linked to Stellar address) |
| Merkle membership in `issuerRoot` | Anonymous platform (Layer 2) | Anonymous (`platformId`, not address) |

The opinion platform uses the **second** bridge so posting activity cannot be tied back to the KYC transaction.

## Reference inspiration

**human** is inspired by [zk.me](https://www.zk.me/) — ZK KYC on other chains — adapted for Stellar's ZK host functions and Soroban.

## Related

* [What is human?](what-is-human.md)
* [Architecture overview](../architecture/overview.md)
* [Platform identity (platformId)](../architecture/platform-identity.md)
