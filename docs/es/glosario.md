# Glosario

Términos clave en la documentación de **human**.

## Zero-Knowledge

| Término | Definición |
|---|---|
| **ZKP** | Prueba de veracidad sin revelar información extra |
| **zk-SNARK** | Prueba sucinta no interactiva; Groth16 es un SNARK |
| **Circuito** | Programa de restricciones provables |
| **Witness** | Entradas que satisfacen el circuito |
| **Nullifier** | Valor anti-replay sin revelar identidad |
| **Commitment** | Hash que compromete atributos ocultos |
| **Raíz Merkle** | Raíz del árbol de pertenencia |

## Stellar

| Término | Definición |
|---|---|
| **Stellar** | Blockchain L1 |
| **Soroban** | Plataforma de smart contracts (Rust → Wasm) |
| **Host function** | Primitiva nativa del runtime |
| **Testnet / Mainnet** | Red de prueba vs producción |

## Identidad / KYC

| Término | Definición |
|---|---|
| **KYC** | Verificación de identidad del cliente |
| **Emisor** | Entidad que firma credenciales |
| **Credencial** | Atestación firmada sobre atributos |
| **PII** | Información personal identificable |
| **Predicado** | Condición probada (ej. edad ≥ 18) |
| **Proof of personhood** | Probar humano real + único + anónimo |
| **Ataque Sybil** | Una persona, muchas identidades falsas |
| **issuerRoot** | Raíz Merkle de credenciales válidas |

## Plataforma

| Término | Definición |
|---|---|
| **platformId** | Identidad anónima estable en Capa 2 |
| **contentHash** | Hash del contenido atado en la prueba ZK |
| **Curaduría** | Revisión de calidad / seguridad del contenido |
| **Cuenta efímera** | Cuenta Stellar desechable para pagar fees |

## Herramientas

| Término | Definición |
|---|---|
| **Circom** | DSL para circuitos ZK (Groth16) |
| **snarkjs** | Herramientas Groth16 |
| **Groth16** | SNARK clásico con pruebas pequeñas |
