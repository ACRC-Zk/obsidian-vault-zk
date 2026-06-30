# Referencia de API

Referencia del SDK **human** (Capa 1 + Capa 2).

## Configuración

```typescript
interface HumanConfig {
  network: 'testnet' | 'mainnet';
  rpcUrl: string;
  kycVerifierContractId: string;
  opinionBoardContractId?: string;
  issuerRoot?: string;
}
```

## Capa 1 — Identidad

### `generateProof(params)`

Genera prueba Groth16 client-side.

**Entrada:** `credential`, `address`, `predicate`  
**Salida:** `proof`, `publicInputs`

### `verifyAndRegister(config, params)`

Envía `verify_and_register` a `kyc_verifier`.

### `isVerified(config, address)`

Consulta registro on-chain. Retorna `boolean`.

## Capa 2 — Plataforma (planificado público)

### `derivePlatformId(secret, scope)`

Deriva identidad anónima estable.

### `generatePlatformProof(params)`

Prueba membresía + `platformId` + `contentHash`.

### `postOpinion(config, params)`

Ancla post en `opinion_board`.

## Métodos on-chain

### `kyc_verifier`

| Método | Descripción |
|---|---|
| `init` | Bootstrap |
| `verify_and_register` | Verificar + registrar |
| `is_verified` | Consulta |

### `opinion_board`

| Método | Descripción |
|---|---|
| `register_identity` | Registrar platformId |
| `post` | Anclar contentHash |

## Artefactos del circuito

| Archivo | Propósito |
|---|---|
| `kyc.wasm` | Generador de witness |
| `kyc_final.zkey` | Proving key |
| `verification_key.json` | VK en contrato |

Ubicación: `identity/circuits/build/` tras compilar.
