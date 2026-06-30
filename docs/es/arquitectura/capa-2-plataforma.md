# Capa 2 — Plataforma anónima

Plataforma de **opinión y publicación verificada** — participación anónima sobre Capa 1.

## Problema resuelto

Publicar con el address del KYC permite vincular opiniones a tu identidad on-chain. Capa 2 usa **`platformId`** — derivado del `secret` de Capa 1, no vinculable al address Stellar.

## Componentes

| Pieza | Ubicación | Rol |
|---|---|---|
| Circuito plataforma | `platform/circuits/` | Membresía + `platformId` + `contentHash` |
| `opinion_board` | `platform/contracts/` | Ancla on-chain |
| `platform/api` | Off-chain | Perfil, feed, artículos |
| Curaduría | `platform/curation/` | IA + moderación humana |

## Cuenta efímera para fees

Alguien paga el fee de transacción. Usar el wallet del KYC deanonimizaría.

**Solución:** cuenta desechable fondeada en testnet (friendbot). Producción: relayer o meta-transacciones.

## Puente a Capa 1

Capa 2 **no** usa `is_verified(address)`. Prueba **membresía Merkle en `issuerRoot`** — mismo set de humanos, sin revelar cuál.

Ver [Identidad de plataforma (platformId)](identidad-plataforma.md).
