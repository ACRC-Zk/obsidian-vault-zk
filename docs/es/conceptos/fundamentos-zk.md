# Fundamentos de Zero-Knowledge

Breve introducción a la criptografía detrás de **human**.

## Prueba Zero-Knowledge (ZKP)

Prueba criptográfica de que una afirmación es cierta **sin revelar nada más que su veracidad**.

## Términos clave

| Término | Significado |
|---|---|
| **Circuito** | Programa que define qué se prueba |
| **Witness** | Entradas públicas + privadas que satisfacen el circuito |
| **Entradas públicas** | Visibles para el verificador (issuer root, predicado, address hash) |
| **Nullifier** | Valor único anti-replay sin revelar identidad |
| **Commitment** | Hash que compromete atributos |
| **Raíz Merkle** | Prueba pertenencia a un conjunto |

## zk-SNARKs

**human** usa **Groth16** (Circom) verificado en Soroban con BLS12-381.

## Dónde corre cada cosa

* **Generar prueba** = off-chain (dispositivo del usuario).
* **Verificar prueba** = on-chain (Soroban + host functions).

## Curvas y hashes en Stellar

* **BLS12-381** — curva para Groth16 en Soroban.
* **Poseidon** — hash ZK-friendly; host function nativa.
