# Running the demo

End-to-end testnet demo for **human**.

## Prerequisites

Complete [Environment setup](environment-setup.md) and ensure contracts are deployed (or use existing `.deploy/` IDs from the repo).

## Option A — Automated E2E script (Node)

From the code repo root:

```bash
./scripts/e2e_demo.sh
```

This script exercises:

1. Matcher enrollment (or fixture credentials).
2. Proof generation via SDK.
3. `verify_and_register` on testnet.
4. `is_verified` check.

## Option B — Browser demo (recommended for judges)

### 1. Start backend services

```bash
# Terminal 1 — identity matcher
cd identity/issuer/matcher && npm run dev

# Terminal 2 — platform API
cd platform/api && npm run dev

# Terminal 3 — web app
cd web && npm run dev
```

### 2. Layer 1 flow

1. Open the web app (typically `http://localhost:5173`).
2. Connect a Stellar wallet (Freighter or supported kit).
3. If already verified → UI shows existing identity (no re-enrollment).
4. Upload ID document photo → live face scan.
5. Generate proof → sign `verify_and_register` transaction.
6. Confirm `is_verified` shows success.

### 3. Layer 2 flow

1. Navigate to the platform section.
2. Derive anonymous `platformId` from stored credential.
3. Create profile / username.
4. Compose and publish a post → on-chain anchor + off-chain content.
5. View feed.

## What to observe

| Step | Proves |
|---|---|
| Matcher gate | Real enrollment before ZK (testnet mock) |
| On-chain registration | Groth16 verification in Soroban |
| `is_verified` | dApp-consumable registry |
| `platformId` post | Anonymous layer decoupled from KYC address |
| Ephemeral fee payer | KYC wallet not exposed in platform txs |

## Troubleshooting

| Issue | Check |
|---|---|
| Proof verification fails | Contract VK matches compiled circuit; correct `issuerRoot` |
| Matcher rejects face | Lighting, document quality; see matcher logs on :8787 |
| Transaction fails | Testnet XLM balance; correct network in wallet |
| Already verified | Expected — nullifier prevents re-registration |

## Related

* [KYC flow](../architecture/kyc-flow.md)
* [For judges and developers](../introduction/for-judges-and-developers.md)
* [Security & limitations](../security/limitations.md)
