# Estructura del repositorio

La aplicación **human** es un **monorepo por capas**. La documentación vive en esta vault; el código en GitHub.

**Fuente:** https://github.com/ACRC-Zk/beHuman

```text
human/
├── identity/                 # CAPA 1 · KYC con ZK
│   ├── circuits/
│   ├── contracts/            # kyc_verifier
│   └── issuer/               # emisor mock + matcher
├── platform/                 # CAPA 2 · Plataforma
│   ├── circuits/
│   ├── contracts/            # opinion_board
│   ├── api/
│   └── curation/
├── packages/
│   ├── sdk/
│   └── shared/
├── web/
├── scripts/
└── .deploy/                  # IDs de contratos testnet
```

## Puente entre capas

```
is_verified(address)  →  contrato kyc_verifier
```

Capa 2 usa puente ZK (`issuerRoot`) en lugar del address.

## Mapeo docs → código

| Tema | Ruta |
|---|---|
| Circuito Capa 1 | `identity/circuits/src/kyc.circom` |
| KycVerifier | `identity/contracts/kyc_verifier/` |
| Matcher | `identity/issuer/matcher/` |
| Plataforma | `platform/contracts/opinion_board` + `platform/api` |
