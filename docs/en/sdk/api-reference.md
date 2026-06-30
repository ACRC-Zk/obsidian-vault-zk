# API reference

Reference for the **human** SDK (Layer 1 + Layer 2 public surface).

> Signatures reflect the current internal SDK; names may change slightly in the public `@human/kyc-zk` release.

## Configuration

```typescript
interface HumanConfig {
  network: 'testnet' | 'mainnet';
  rpcUrl: string;
  kycVerifierContractId: string;
  opinionBoardContractId?: string; // Layer 2
  issuerRoot?: string;             // hex or bytes
}
```

## Layer 1 — Identity

### `generateProof(params)`

Generate a Groth16 proof client-side.

**Input:**

| Field | Type | Description |
|---|---|---|
| `credential` | `Capa1Credential` | Signed credential from issuer |
| `address` | `string` | Stellar address (G...) |
| `predicate` | `Predicate` | e.g. `{ minAge: 18 }` |

**Output:**

| Field | Type |
|---|---|
| `proof` | `Groth16Proof` |
| `publicInputs` | `string[]` |

### `verifyAndRegister(config, params)`

Submit `verify_and_register` to `kyc_verifier`.

**Input:** `address`, `proof`, `publicInputs`, `signTransaction` callback.

**Output:** transaction result / hash.

### `isVerified(config, address)`

Query on-chain registry.

**Returns:** `boolean`

## Layer 2 — Platform (planned public)

### `derivePlatformId(secret, scope)`

Derive stable anonymous identity.

**Returns:** `platformId` (hex)

### `generatePlatformProof(params)`

Prove Merkle membership + bind `platformId` and `contentHash`.

### `postOpinion(config, params)`

Anchor post on `opinion_board` with ephemeral fee payer.

## Types (shared)

From `packages/shared/`:

* `Capa1Credential` — issuer-signed credential + Merkle path material.
* `Predicate` — compliance conditions proved in-circuit.
* `Groth16Proof` — proof points A/B/C encoded for Soroban.

## Contract methods (on-chain)

### `kyc_verifier`

| Method | Description |
|---|---|
| `init(trusted_root, vk)` | Admin bootstrap |
| `verify_and_register(proof, public_inputs)` | Verify + register |
| `is_verified(address)` | Query |

### `opinion_board`

| Method | Description |
|---|---|
| `register_identity(proof, ...)` | Register `platformId` |
| `post(proof, ...)` | Anchor content hash |

## Circuit artifacts

| File | Purpose |
|---|---|
| `kyc.wasm` | Witness generator |
| `kyc_final.zkey` | Proving key |
| `verification_key.json` | VK embedded in contract |

Located under `identity/circuits/build/` after compile + trusted setup.

## Related

* [SDK overview](overview.md)
* [Layer 1 architecture](../architecture/layer-1-identity.md)
* [Layer 2 architecture](../architecture/layer-2-platform.md)
