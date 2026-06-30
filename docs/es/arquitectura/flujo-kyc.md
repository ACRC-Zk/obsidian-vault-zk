# Flujo KYC de punta a punta

Recorrido desde verificación de identidad hasta acceso en una dApp.

## Fase 1 — Emisión de credencial (una vez)

```mermaid
sequenceDiagram
    participant U as Usuario
    participant W as Wallet
    participant I as Emisor KYC
    U->>W: inicia onboarding
    W->>I: documento + selfie
    I->>I: verifica identidad
    I->>W: credencial firmada
    Note over U,I: PII solo visible para el emisor
```

## Fase 2 — Generación de prueba

```mermaid
sequenceDiagram
    participant W as Wallet
    participant P as Prover
    W->>P: credencial + predicado + address
    P->>P: witness privado + nullifier
    P->>W: prueba + entradas públicas
```

## Fase 3 — Verificación on-chain

```mermaid
sequenceDiagram
    participant W as Wallet
    participant V as KycVerifier
    participant R as Registro
    W->>V: verify_and_register
    V->>V: verify_groth16 ✅
    V->>R: registrar address + nullifier
```

## Fase 4 — Consumo por dApp

```mermaid
sequenceDiagram
    participant D as dApp
    participant R as Registro
    D->>R: is_verified(address)?
    R-->>D: true
```

## Propiedades de seguridad

| Propiedad | Mecanismo |
|---|---|
| Address binding | Prueba atada a `addressHash` |
| Anti-Sybil | Nullifier on-chain |
| Emisor confiable | `issuerRoot` en contrato |
| PII contenida | Solo hacia emisor en Fase 1 |

## Referencias de código

| Fase | Código |
|---|---|
| 1 | `identity/issuer/matcher/` |
| 2 | `packages/sdk/` |
| 3 | `identity/contracts/kyc_verifier/` |
| E2E | `scripts/e2e_demo.sh` |
