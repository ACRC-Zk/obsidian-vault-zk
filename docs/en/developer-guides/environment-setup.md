# Environment setup

Tools required to build and run **human** locally.

Clone the code repository first:

```bash
git clone https://github.com/ACRC-Zk/beHuman.git
cd beHuman
```

## Stellar / Soroban

```bash
# Rust + wasm target
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
rustup target add wasm32-unknown-unknown

# Stellar CLI
cargo install --locked stellar-cli

# Verify
stellar --version

# Testnet identity
stellar keys generate --global alice --network testnet
stellar keys fund alice --network testnet
```

## ZK toolchain (Circom — current choice)

```bash
# circom
git clone https://github.com/iden3/circom.git
cd circom && cargo build --release && cargo install --path circom

# snarkjs (Groth16 proofs + trusted setup)
npm install -g snarkjs

# circomlib (Poseidon, Merkle)
npm install circomlib
```

## Node.js (frontend + SDK)

```bash
# From repo root
npm install
```

## Reference verifiers (study / compare)

```bash
# Official Groth16 verifier example
git clone https://github.com/stellar/soroban-examples

# UltraHonk (Noir, community)
git clone https://github.com/yugocabrio/rs-soroban-ultrahonk
```

## Ready checklist

- [ ] `rustc` + `wasm32-unknown-unknown`
- [ ] `stellar --version` works
- [ ] Testnet key created and funded
- [ ] `circom` + `snarkjs` installed
- [ ] `npm install` succeeds in monorepo root
- [ ] Contracts build: `stellar contract build`

## Running services locally

| Service | Port | Path |
|---|---|---|
| Identity matcher | 8787 | `identity/issuer/matcher/` |
| Platform API | 8788 | `platform/api/` |
| Web frontend | 5173 | `web/` (Vite default) |

See [Running the demo](running-the-demo.md) for the full flow.

## Related

* [Repository structure](repository-structure.md)
* [SDK quickstart](../sdk/quickstart.md)
