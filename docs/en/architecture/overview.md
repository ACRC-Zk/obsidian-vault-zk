# System overview

Bird's-eye view of **human** components and how they connect.

## Components

```mermaid
flowchart TB
    subgraph OFF["Off-chain"]
        ISS["KYC issuer<br/>(verifies identity, signs credential)"]
        WALLET["Wallet / client"]
        PROVER["Prover<br/>(generates ZK proof)"]
    end

    subgraph ON["On-chain (Stellar / Soroban)"]
        VERIFIER["KycVerifier"]
        REGISTRY["KYC registry"]
        DAPP["Consuming dApp"]
    end

    USER[User] --> WALLET
    WALLET -->|identity data| ISS
    ISS -->|signed credential| WALLET
    WALLET --> PROVER
    PROVER -->|proof + public inputs| VERIFIER
    VERIFIER --> REGISTRY
    DAPP -->|is_verified?| REGISTRY
```

## Responsibilities

| Component | Location | Role |
|---|---|---|
| **KYC issuer** | Off-chain | Verify real identity; issue signed credential. Testnet: face matcher (document + selfie). |
| **Wallet / client** | Off-chain | Store credential; orchestrate flow |
| **Prover** | Off-chain | Generate ZK proof from credential + predicate |
| **KycVerifier** | Soroban | Verify proof via host functions; register address |
| **Registry** | On-chain storage | `address → verified` + used nullifiers |
| **Consuming dApp** | Soroban / off-chain | Gate features with `is_verified(address)` |

## Design principle: where each thing runs

* **Prove** = off-chain (expensive, private).
* **Verify** = on-chain (cheap with Stellar ZK primitives).

## human's two product layers

```mermaid
flowchart TB
    subgraph C1["LAYER 1 · Identity (KYC-ZK)"]
        ISS2[Issuer + Merkle tree] --> PROV[Prover]
        PROV --> VER[kyc_verifier]
        VER --> REG2[Registry + nullifier]
        ISS2 --> ROOT[issuerRoot]
    end
    subgraph C2["LAYER 2 · Opinion platform"]
        BOARD[opinion_board]
        API[platform/api]
        CUR[Curation]
    end
    ROOT -->|ZK membership proof| BOARD
    BOARD --> API
    API --> CUR
```

### Two bridges from Layer 1

| Bridge | Use case | Linkability |
|---|---|---|
| `is_verified(address)` | Generic dApps | Pseudonymous (Stellar address) |
| Merkle `issuerRoot` membership | Anonymous platform | Anonymous (`platformId`) |

The opinion platform uses **issuerRoot membership** — never the KYC address.

## Code mapping

| Component | Repo path |
|---|---|
| Issuer + matcher | `identity/issuer/` |
| Layer 1 circuit | `identity/circuits/` |
| `kyc_verifier` | `identity/contracts/kyc_verifier/` |
| Layer 2 circuit | `platform/circuits/` |
| `opinion_board` | `platform/contracts/opinion_board/` |
| Feed / profile API | `platform/api/` |
| Curation | `platform/curation/` |
| SDK | `packages/sdk/` |
| Frontend | `web/src/kyc/` + `web/src/platform/` |

## Related

* [Layer 1 — Identity](layer-1-identity.md)
* [Layer 2 — Platform](layer-2-platform.md)
* [KYC flow](kyc-flow.md)
* [Repository structure](../developer-guides/repository-structure.md)
