# Quickstart

Gate an action behind **human** verification in a few steps.

> Uses the internal SDK from the monorepo today. Adjust import path when the public package ships.

## 1. Install (monorepo)

```bash
git clone https://github.com/ACRC-Zk/beHuman.git
cd beHuman
npm install
```

## 2. Configure testnet

Use contract IDs from `.deploy/` or your own deployment:

```typescript
import { HumanConfig } from '@behuman/sdk'; // → @human/kyc-zk when published

const config: HumanConfig = {
  network: 'testnet',
  kycVerifierContractId: '<from .deploy/>',
  rpcUrl: 'https://soroban-testnet.stellar.org',
};
```

## 3. Check verification

```typescript
import { isVerified } from '@behuman/sdk';

const address = 'G...'; // user's Stellar address
const verified = await isVerified(config, address);

if (!verified) {
  // redirect to human enrollment flow
}
```

## 4. Full registration (sketch)

```typescript
import { generateProof, verifyAndRegister } from '@behuman/sdk';

// After user holds a signed credential from the issuer:
const { proof, publicInputs } = await generateProof({
  credential,
  address,
  predicate: { minAge: 18 },
});

await verifyAndRegister(config, {
  address,
  proof,
  publicInputs,
  signTransaction: wallet.sign, // Stellar wallet adapter
});
```

## 5. Gate your dApp

```typescript
async function protectedAction(userAddress: string) {
  if (!(await isVerified(config, userAddress))) {
    throw new Error('human verification required');
  }
  // ... your logic
}
```

## Browser integration

The reference implementation is in `web/src/kyc/`:

* `KycFlow` — consent → document → face → proof → on-chain register.
* Stellar Wallets Kit for signing.

## Next

* [API reference](api-reference.md)
* [KYC flow](../architecture/kyc-flow.md)
* [Running the demo](../developer-guides/running-the-demo.md)
