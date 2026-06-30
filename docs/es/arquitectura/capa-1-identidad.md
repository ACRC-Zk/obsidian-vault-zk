# Capa 1 — Identidad (KYC-ZK)

Núcleo de **prueba de persona única** de human.

## Objetivos

* Una persona real se registra **una vez**.
* Registro **anónimo on-chain** (sin PII).
* Cualquier dApp consulta `is_verified(address)`.

## Pipeline

```mermaid
flowchart LR
    A[Enrolamiento<br/>matcher] --> B[Credencial firmada]
    B --> C[Prueba ZK]
    C --> D[verify_and_register]
    D --> E[is_verified]
```

## Gate de enrolamiento (testnet)

1. Foto del documento.
2. Selfie en vivo (liveness).
3. Matcher confirma coincidencia + anti-duplicado.
4. Emisor crea credencial firmada.

Producción: emisor licenciado (ej. integración con autoridad de identidad nacional).

## Circuito (`kyc.circom`)

Prueba: credencial del emisor confiable, inclusión Merkle, predicado, nullifier atado al address.

Curva: **BLS12-381** (Groth16).

## Contrato (`kyc_verifier`)

| Función | Propósito |
|---|---|
| `init` | Bootstrap issuer root + VK |
| `verify_and_register` | Verificar + registrar |
| `is_verified` | Consulta para dApps |

## Medidas anti-fraude

* Cotejo OCR datos ↔ documento.
* Corte temprano si `is_verified` ya es true.
* Nullifier on-chain.
* De-duplicación por documento.
