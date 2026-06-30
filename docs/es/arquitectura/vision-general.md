# Visión general del sistema

Vista de pájaro de los componentes de **human**.

## Componentes

```mermaid
flowchart TB
    subgraph OFF["Off-chain"]
        ISS["Emisor KYC"]
        WALLET["Wallet / cliente"]
        PROVER["Prover"]
    end
    subgraph ON["On-chain"]
        VERIFIER["KycVerifier"]
        REGISTRY["Registro KYC"]
        DAPP["dApp consumidora"]
    end
    USER[Usuario] --> WALLET
    WALLET --> ISS
    ISS --> WALLET
    WALLET --> PROVER
    PROVER --> VERIFIER
    VERIFIER --> REGISTRY
    DAPP --> REGISTRY
```

## Principio de diseño

* **Probar** = off-chain (costoso, privado).
* **Verificar** = on-chain (barato con primitivas ZK de Stellar).

## Las dos capas de producto

```mermaid
flowchart TB
    subgraph C1["CAPA 1 · Identidad"]
        ISS2[Emisor + Merkle] --> PROV[Prover]
        PROV --> VER[kyc_verifier]
        VER --> REG2[Registro + nullifier]
    end
    subgraph C2["CAPA 2 · Plataforma"]
        BOARD[opinion_board]
        API[platform/api]
    end
    ISS2 --> ROOT[issuerRoot]
    ROOT -->|prueba ZK membresía| BOARD
    BOARD --> API
```

### Dos puentes desde Capa 1

| Puente | Uso | Vinculabilidad |
|---|---|---|
| `is_verified(address)` | dApps genéricas | Pseudónimo |
| Membresía en `issuerRoot` | Plataforma anónima | Anónimo (`platformId`) |

## Mapeo a código

| Componente | Ruta |
|---|---|
| Emisor + matcher | `identity/issuer/` |
| Circuito Capa 1 | `identity/circuits/` |
| `kyc_verifier` | `identity/contracts/kyc_verifier/` |
| Plataforma | `platform/contracts/opinion_board` + `platform/api` |
| SDK | `packages/sdk/` |
| Frontend | `web/src/kyc/` + `web/src/platform/` |
