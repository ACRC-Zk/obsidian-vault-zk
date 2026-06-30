# Configuración del entorno

Herramientas para construir y ejecutar **human** localmente.

```bash
git clone https://github.com/ACRC-Zk/beHuman.git
cd beHuman
```

## Stellar / Soroban

```bash
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
rustup target add wasm32-unknown-unknown
cargo install --locked stellar-cli
stellar keys generate --global alice --network testnet
stellar keys fund alice --network testnet
```

## Toolchain ZK (Circom)

```bash
git clone https://github.com/iden3/circom.git
cd circom && cargo build --release && cargo install --path circom
npm install -g snarkjs
npm install circomlib
```

## Node.js

```bash
npm install   # desde la raíz del monorepo
```

## Checklist

- [ ] `rustc` + `wasm32-unknown-unknown`
- [ ] `stellar --version`
- [ ] Key testnet fondeada
- [ ] `circom` + `snarkjs`
- [ ] `stellar contract build` OK

## Servicios locales

| Servicio | Puerto |
|---|---|
| Matcher identidad | 8787 |
| API plataforma | 8788 |
| Web (Vite) | 5173 |

Ver [Ejecutar la demo](ejecutar-demo.md).
