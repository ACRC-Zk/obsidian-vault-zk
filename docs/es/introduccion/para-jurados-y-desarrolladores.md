# Para jurados y desarrolladores

---

## Para jurados (lectura de 5 minutos)

### Elevator pitch

**human** es el primer stack de prueba de personhood con ZK construido para **Stellar**: verificar humanos reales on-chain sin exponer datos personales, y permitirles participar en una plataforma de opinión de forma anónima.

### Por qué el ZK es esencial

Sin pruebas Zero-Knowledge, un contrato debe recibir datos personales para confiar en identidad. Con ZK, solo recibe una **prueba matemática** de que:

* el usuario tiene una credencial válida firmada por el emisor,
* cumple un predicado (edad, país, etc.),
* no se registró antes (nullifier),
* la prueba está atada a su address Stellar.

Sin ZK, el modelo de privacidad colapsa.

### Qué es demostrable hoy (testnet)

| Componente | Demo |
|---|---|
| Matcher documento + cara | DNI + selfie en vivo |
| Circuito ZK (Circom / BLS12-381) | Prueba Groth16 de credencial + Merkle |
| Contrato `kyc_verifier` | `verify_and_register` + `is_verified` |
| Web app | Flujo completo en navegador |
| Plataforma Capa 2 | `platformId` anónimo, ancla on-chain, feed off-chain |
| Curaduría | Agente IA + cola humana (off-chain) |

### Limitaciones honestas

* Emisor **mock** en testnet.
* Solo **testnet**.
* SDK público **planificado**.

Ver [Seguridad y limitaciones](../seguridad/limitaciones.md).

### Ruta de demo sugerida

1. Conectar wallet → enrolar (foto DNI + cara).
2. Generar prueba → `verify_and_register` en testnet.
3. Consultar `is_verified(address)` → true.
4. Ir a plataforma → derivar `platformId` → publicar opinión anclada on-chain.

Detalle: [Ejecutar la demo](../guias/ejecutar-demo.md).

---

## Para desarrolladores

### Repositorio

Código: **https://github.com/ACRC-Zk/beHuman**

> Nombre legacy del repo en GitHub; el producto es **human**.

### Monorepo por capas

```text
human/
├── identity/          # Capa 1
├── platform/          # Capa 2
├── packages/sdk/
├── web/
└── scripts/
```

Ver [Estructura del repositorio](../guias/repositorio.md).

### Camino de integración

1. [Configuración del entorno](../guias/configuracion-entorno.md)
2. [Flujo KYC](../arquitectura/flujo-kyc.md)
3. [Inicio rápido SDK](../sdk/inicio-rapido.md)
4. [Referencia de API](../sdk/referencia-api.md)

### Contratos clave (testnet)

| Contrato | Rol |
|---|---|
| `kyc_verifier` | Verificar prueba ZK; `is_verified` |
| `opinion_board` | Anclar posts por `platformId` + `contentHash` |

IDs en `.deploy/` del repo.
