# Stellar y Soroban

Por qué **human** está construido sobre Stellar.

## Stellar

Blockchain enfocada en pagos, stablecoins y RWAs. **human** aprovecha:

* Host functions ZK (Protocolos 25–26).
* Contratos Soroban en Rust → Wasm.
* Ecosistema con casos de uso sensibles a identidad.

## Contratos de human

| Contrato | Capa | Propósito |
|---|---|---|
| `kyc_verifier` | 1 | Verificar Groth16; registrar addresses |
| `opinion_board` | 2 | Anclar posts (`platformId` + `contentHash`) |

## Host functions (primitivas ZK)

| Primitiva | Rol |
|---|---|
| `verify_groth16` | Verificar SNARK |
| Poseidon | Hashes en circuito |
| MSM | Verificación eficiente |

## KycVerifier

1. Verificar prueba ZK contra VK embebida.
2. Validar entradas públicas (issuer root, address binding, nullifier).
3. Registrar `address → verificado`.
4. Exponer `is_verified(address)`.

## Redes

| Red | Estado |
|---|---|
| **Testnet** | Desplegado y demostrable |
| **Mainnet** | Pendiente — requiere auditoría + emisor de producción |
