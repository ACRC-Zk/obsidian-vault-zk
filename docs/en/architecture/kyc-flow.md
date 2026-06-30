# KYC end-to-end flow

Step-by-step journey from identity verification to dApp access.

## Phase 1 — Credential issuance (once)

```mermaid
sequenceDiagram
    participant U as User
    participant W as Wallet
    participant I as KYC issuer

    U->>W: start onboarding
    W->>I: identity data (document, selfie)
    I->>I: verify identity
    I->>I: commitment = Poseidon(attributes, secret)
    I->>W: signed credential
    W->>W: store credential locally
    Note over U,I: PII only visible to issuer. Never on-chain.
```

**Testnet:** verification = document photo + live face match (matcher gate).

## Phase 2 — Proof generation (each time needed)

```mermaid
sequenceDiagram
    participant W as Wallet
    participant P as Prover

    W->>P: credential + predicate + address
    P->>P: build witness (PII stays private)
    P->>P: nullifier = Poseidon(secret, addressHash)
    P->>P: generate ZK proof
    P->>W: proof + public inputs
```

Output is a proof — not raw data.

## Phase 3 — On-chain verification and registration

```mermaid
sequenceDiagram
    participant W as Wallet
    participant V as KycVerifier
    participant R as Registry

    W->>V: verify_and_register(address, proof, public_inputs)
    V->>V: issuer_root trusted?
    V->>V: address == invoker?
    V->>R: nullifier already used?
    R-->>V: no
    V->>V: verify_groth16 ✅
    V->>R: register address + nullifier
    V-->>W: success
```

## Phase 4 — dApp consumption

```mermaid
sequenceDiagram
    participant U as User
    participant D as dApp
    participant R as Registry

    U->>D: request regulated action
    D->>R: is_verified(address)?
    R-->>D: true
    D-->>U: access granted (identity unknown)
```

## Security properties

| Property | Mechanism |
|---|---|
| **Address binding** | Proof tied to `addressHash`; invoker must match |
| **Anti-Sybil** | Nullifier stored on-chain; reuse rejected |
| **Trusted issuer** | Only credentials under configured `issuerRoot` accepted |
| **PII containment** | PII only sent to issuer in Phase 1 |

## Implementation references

| Phase | Code |
|---|---|
| 1 | `identity/issuer/matcher/` |
| 2 | `packages/sdk/` (`generateProof`) |
| 3 | `identity/contracts/kyc_verifier/` |
| 4 | `is_verified` query via SDK |
| E2E | `scripts/e2e_demo.sh` |

## Related

* [Layer 1 — Identity](layer-1-identity.md)
* [Running the demo](../developer-guides/running-the-demo.md)
