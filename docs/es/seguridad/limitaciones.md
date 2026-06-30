# Seguridad y limitaciones

**human** documenta su alcance con honestidad.

## Solo testnet (hoy)

* Contratos en **Stellar testnet**.
* No auditado para producción en mainnet.

## Emisor KYC mock

El **emisor en testnet es mock**:

* Enrolamiento con **matcher documento + cara** (face-api.js), no proveedor KYC licenciado.
* Sin integración con autoridades de identidad nacionales en la demo actual.
* **El ZK prueba pertenencia al set del emisor** — no reemplaza la honestidad del emisor.

> El ZK no reemplaza al KYC. Alguien debe verificar identidad off-chain primero.

## Qué garantiza el ZK

| Garantía | Condición |
|---|---|
| Sin PII on-chain | Uso correcto de cliente + circuito |
| Un registro por persona | Nullifier + binding del emisor |
| Prueba atada al address | `addressHash` en contrato |
| Solo credenciales confiables | `issuerRoot` configurado |

## Qué no garantiza

| Limitación | Detalle |
|---|---|
| Honestidad del emisor | Emisor malicioso podría firmar credenciales falsas |
| Fuerza del matcher | Face match testnet ≠ KYC legal |
| Correlación por timing | Tx KYC vs primer post en plataforma |
| Relayer de fees | Infraestructura no debe filtrar vínculos |

## Antes de producción

- [ ] Proveedor KYC licenciado
- [ ] Auditoría de seguridad independiente
- [ ] Mainnet + ceremonia de setup del circuito
- [ ] Relayer de fees con análisis de privacidad
- [ ] Gobernanza de issuer root y moderación
