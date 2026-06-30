# Inicio rápido

Gatear una acción detrás de verificación **human** en pocos pasos.

## 1. Instalar (monorepo)

```bash
git clone https://github.com/ACRC-Zk/beHuman.git
cd beHuman && npm install
```

## 2. Configurar testnet

```typescript
const config = {
  network: 'testnet',
  kycVerifierContractId: '<desde .deploy/>',
  rpcUrl: 'https://soroban-testnet.stellar.org',
};
```

## 3. Verificar estado

```typescript
import { isVerified } from '@behuman/sdk';

const verified = await isVerified(config, address);
if (!verified) {
  // redirigir a flujo de enrolamiento human
}
```

## 4. Registro completo (boceto)

```typescript
import { generateProof, verifyAndRegister } from '@behuman/sdk';

const { proof, publicInputs } = await generateProof({
  credential,
  address,
  predicate: { minAge: 18 },
});

await verifyAndRegister(config, {
  address,
  proof,
  publicInputs,
  signTransaction: wallet.sign,
});
```

## Referencia en navegador

Implementación de referencia: `web/src/kyc/KycFlow`.
