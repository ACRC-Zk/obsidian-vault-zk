# Ejecutar la demo

Demo end-to-end en testnet para **human**.

## Prerrequisitos

Completar [Configuración del entorno](configuracion-entorno.md).

## Opción A — Script E2E

```bash
./scripts/e2e_demo.sh
```

## Opción B — Navegador (recomendado para jurados)

### 1. Levantar servicios

```bash
# Terminal 1
cd identity/issuer/matcher && npm run dev

# Terminal 2
cd platform/api && npm run dev

# Terminal 3
cd web && npm run dev
```

### 2. Flujo Capa 1

1. Abrir `http://localhost:5173`
2. Conectar wallet Stellar
3. Subir foto DNI → escaneo facial
4. Generar prueba → firmar `verify_and_register`
5. Confirmar `is_verified`

### 3. Flujo Capa 2

1. Ir a sección plataforma
2. Derivar `platformId`
3. Crear perfil
4. Publicar opinión (ancla on-chain + contenido off-chain)

## Qué observar

| Paso | Demuestra |
|---|---|
| Matcher | Enrolamiento antes del ZK |
| Registro on-chain | Groth16 en Soroban |
| `is_verified` | Registro consumible por dApps |
| `platformId` | Capa anónima desacoplada del KYC |
| Fee efímero | Wallet KYC no expuesto en txs de plataforma |
