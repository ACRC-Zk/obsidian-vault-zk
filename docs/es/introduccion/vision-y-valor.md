# Visión y propuesta de valor

## Qué construimos

Un sistema donde **cada persona registra y valida su identidad real una sola vez**, de forma:

* **Única** — una persona real = una identidad (anti-Sybil).
* **Anónima** — sin datos personales en la blockchain.
* **Verificable en Stellar** — pruebas chequeadas dentro de contratos Soroban.

Sobre esa base, **human** habilita una **plaza pública para humanos verificados**: opiniones, artículos e investigación con el peso de una persona real sin exponer quién es.

## Valor para el ecosistema

| Actor | Beneficio |
|---|---|
| **Usuarios** | Demostrar humanidad una vez; participar en privado en múltiples apps |
| **dApps en Stellar** | Gatear con `is_verified(address)` sin manejar PII |
| **Sociedad** | Reducir ruido de bots; elevar el discurso de humanos verificados |

## Principios de diseño

1. **PII off-chain** — solo commitments, nullifiers y pruebas tocan la cadena.
2. **El ZK hace el trabajo pesado** — el contrato nunca ve documentos ni biometría.
3. **Arquitectura por capas** — núcleo de identidad (Capa 1) reutilizable; apps (Capa 2+) se componen encima.
4. **Alcance honesto** — mocks y limitaciones de testnet documentados abiertamente.

## Los dos puentes entre capas

| Puente | Caso de uso | Vinculabilidad |
|---|---|---|
| `is_verified(address)` | dApps genéricas (rampas, pools, RWAs) | Pseudónimo (address Stellar) |
| Pertenencia Merkle en `issuerRoot` | Plataforma anónima (Capa 2) | Anónimo (`platformId`) |

La plataforma de opinión usa el **segundo** puente.

## Inspiración

**human** se inspira en [zk.me](https://www.zk.me/) — KYC con ZK en otras cadenas — adaptado a las host functions ZK de Stellar y Soroban.
