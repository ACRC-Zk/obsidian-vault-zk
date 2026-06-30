# Funding ZK (futuro)

**Estado:** Exploratorio — **no** forma parte del alcance actual del producto human.

## Visión

Crowdfunding anónimo y condicional en Stellar:

* Donar sin vincular wallet a identidad.
* Una opinión por humano por campaña (nullifier ZK por campaña).
* Liberar fondos por hitos o reembolso si falla la meta.
* Yield opcional en fondos idle (integración DeFindex / Blend explorada).

## Por qué es Capa 3

| Capa | Rol |
|---|---|
| 1 | Probar humanidad única |
| 2 | Opiniones anónimas verificadas |
| 3 | Participación económica anónima verificada |

## Componentes explorados (código existe, no productizado)

| Pieza | Descripción |
|---|---|
| Circuito `funding_opinion` | Nullifier por campaña |
| `campaign_controller` | Release / refund no custodial |
| `funding/api` | Campañas, donaciones, hitos |
| DeFindex | Yield en XLM (validado testnet) |
| Trustless Work | Escrow (validado testnet) |

## Cuándo se publica

Después del SDK público Capa 1, emisor de producción y estabilización Capa 2.

Ver [Roadmap](roadmap.md).
