# Glossary

Key terms used across **human** documentation.

## Zero-Knowledge

| Term | Definition |
|---|---|
| **ZKP** | Proof that a statement is true without revealing extra information |
| **zk-SNARK** | Succinct non-interactive proof; Groth16 is a SNARK |
| **Circuit** | Program defining provable constraints |
| **Witness** | Inputs satisfying the circuit (public + private) |
| **Public inputs** | Values visible to the verifier |
| **Proving / verifying key** | Setup keys; VK embedded in contract |
| **Trusted setup** | Ceremony generating SNARK parameters |
| **Nullifier** | Unique anti-replay value without revealing identity |
| **Commitment** | Binding hash to hidden attributes |
| **Merkle root** | Root of tree proving set membership |

## Curves & hashes (Stellar)

| Term | Definition |
|---|---|
| **BLS12-381** | Pairing curve for Groth16 on Soroban |
| **BN254** | Alternative pairing curve on Stellar |
| **Poseidon** | ZK-friendly hash; native host function |
| **MSM** | Multi-scalar multiplication host function |

## Stellar

| Term | Definition |
|---|---|
| **Stellar** | L1 blockchain (payments, stablecoins, RWAs) |
| **Soroban** | Stellar smart contract platform (Rust → Wasm) |
| **Host function** | Native runtime primitive (cheaper than Wasm) |
| **XLM** | Native Stellar asset |
| **Testnet / Mainnet** | Test vs production network |

## Identity / KYC

| Term | Definition |
|---|---|
| **KYC** | Know Your Customer — identity verification process |
| **Issuer** | Trusted entity signing credentials |
| **Credential** | Signed attestation over user attributes |
| **PII** | Personally identifiable information |
| **Predicate** | Condition proved (e.g. age ≥ 18) |
| **Proof of personhood** | Prove real + unique human anonymously |
| **Sybil attack** | One person, many fake identities |
| **issuerRoot** | Merkle root of all valid credentials |

## Platform

| Term | Definition |
|---|---|
| **platformId** | Anonymous stable identity on Layer 2 |
| **contentHash** | Hash of post body bound in ZK proof |
| **Curation** | Content quality / safety review |
| **Ephemeral account** | Throwaway Stellar account for fees |

## Tools

| Term | Definition |
|---|---|
| **Circom** | DSL for ZK circuits (Groth16) |
| **snarkjs** | Groth16 prove/verify tooling |
| **Noir** | Alternative circuit language (UltraHonk) |
| **Groth16** | Classic SNARK with small proofs |
