# Security & limitations

**human** documents its scope honestly. Read this before integrating or evaluating.

## Testnet only (today)

* Contracts deployed on **Stellar testnet**.
* Not audited for mainnet production use.
* Economic and operational security assumptions differ from production.

## Mock KYC issuer

The testnet **issuer is a mock**:

* Enrollment uses a **document photo + face matcher** (face-api.js), not a licensed KYC provider.
* No integration with national ID authorities (e.g. RENAPER) in the current demo.
* **ZK proves membership in the issuer's set** — it does not replace the issuer's honesty.

> ZK does not replace KYC. Someone must verify identity off-chain first. The circuits prove *"I belong to the set of verified humans"* without revealing which human.

## What ZK guarantees

| Guarantee | Condition |
|---|---|
| No PII on-chain | Correct client + circuit usage |
| One registration per person | Nullifier + issuer binding |
| Proof bound to address | `addressHash` checked in contract |
| Only trusted credentials | `issuerRoot` configured in contract |

## What ZK does not guarantee

| Limitation | Detail |
|---|---|
| Issuer honesty | Malicious issuer could sign fake credentials |
| Matcher strength | Testnet face match ≠ legal KYC |
| Timing correlation | KYC tx time vs first platform post may correlate |
| Ephemeral relayer trust | Fee payer infrastructure must not leak links |
| UI security | Client-side bugs could expose secrets |

## Cryptographic choices

* **Groth16** — requires per-circuit trusted setup; compromise of toxic waste breaks soundness.
* **BLS12-381** — curve used for current Circom → Soroban path.
* **Poseidon** — ZK-friendly hashing for commitments and nullifiers.

## Operational notes

* Rotate any testnet API keys shared during development.
* Do not use production PII on testnet without legal basis.
* Declare mock components in any public demo (we do in README and here).

## Before production

- [ ] Licensed KYC / identity provider integration
- [ ] Independent security audit (contracts + circuits + client)
- [ ] Mainnet deployment + key ceremony for circuit setup
- [ ] Fee relayer with privacy analysis
- [ ] Governance for issuer root updates and moderation

## Related

* [For judges and developers](../introduction/for-judges-and-developers.md)
* [Layer 1 — Identity](../architecture/layer-1-identity.md)
* [Roadmap](../whats-next/roadmap.md)
