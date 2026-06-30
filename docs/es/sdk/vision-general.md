# Visión general del SDK

El SDK de **human** envuelve generación de pruebas e interacción con contratos Stellar.

> **Estado:** El SDK en `packages/sdk/` es interno hoy. Un **release público** curado está planificado.

## Objetivos

Permitir que dApps en Stellar agreguen **proof of personhood anónimo** con poco código.

## Alcance público planificado (v0.1)

| Incluir | Excluir |
|---|---|
| Capa 1: `generateProof`, `verifyAndRegister`, `isVerified` | Helpers de funding (Capa 3) |
| Capa 2: membresía anónima + `platformId` | Encoders de bajo nivel internos |
| Config testnet overrideable | Utilidades privadas del monorepo |

## Nombre del paquete

Producto: **human**. El paquete npm público podría ser `@human/kyc-zk` (nombre interno actual: `@behuman/sdk`).
