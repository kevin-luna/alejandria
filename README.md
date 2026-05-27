# Alejandría

Repositorio académico abierto y descentralizado. Una DApp que registra propiedad intelectual académica en blockchain y almacena documentos completos en IPFS, como alternativa gratuita a plataformas centralizadas como arXiv.org.

---

## ¿Qué es Alejandría?

Alejandría permite a estudiantes, docentes e investigadores registrar publicaciones académicas (tesis, artículos, libros, actas) con **prueba criptográfica de autoría** en la red de prueba Sepolia de Ethereum. El documento completo se almacena en IPFS; el contrato inteligente guarda los metadatos y el CID de forma inmutable. Cualquier persona puede consultar el catálogo sin necesidad de cartera digital; solo se requiere MetaMask para publicar.

---

## Estructura del monorepo

Este repositorio es el **monorepo raíz**. Cada subcarpeta es un submódulo Git independiente con su propio README detallado.

```
alejandria/
├── alejandria-contracts/   # Contratos Solidity + Hardhat
└── alejandria-frontend/    # Aplicación Angular (SPA)
```

| Submódulo | Descripción | README |
|---|---|---|
| [`alejandria-contracts`](alejandria-contracts/) | Contrato `AlejandriaRegistry` en Solidity, tests y scripts de despliegue con Hardhat Ignition | [ver README](alejandria-contracts/README.md) |
| [`alejandria-frontend`](alejandria-frontend/) | SPA Angular con integración MetaMask, búsqueda de publicaciones y formulario de registro | [ver README](alejandria-frontend/README.md) |

---

## Arquitectura

```
Usuario (Angular SPA)
    │
    ├── MetaMask Connect-EVM ──► Red Sepolia (Ethereum Testnet)
    │                                └── AlejandriaRegistry.sol
    │
    └── IPFS Client ──────────► Red IPFS (documentos completos)
```

| Capa | Tecnología |
|---|---|
| Frontend | Angular, MetaMask Connect-EVM |
| Contrato inteligente | Solidity 0.8.28, Hardhat 3 |
| Almacenamiento | IPFS |
| Red blockchain | Ethereum Sepolia Testnet |

**Contrato desplegado en Sepolia:**
[`0xD54baC82fEDC77c1f74DDC4137A36398694F14CA`](https://sepolia.etherscan.io/address/0xD54baC82fEDC77c1f74DDC4137A36398694F14CA)

---

## Inicio rápido

### 1. Clonar con submódulos

```bash
git clone --recurse-submodules git@github.com:kevin-luna/alejandria.git
cd alejandria
```

Si ya clonaste sin `--recurse-submodules`:

```bash
git submodule update --init --recursive
```

### 2. Contratos

```bash
cd alejandria-contracts
npm install
npx hardhat test          # ejecuta tests Solidity y TypeScript
```

### 3. Frontend

```bash
cd alejandria-frontend
npm install
ng serve                  # http://localhost:4200
```

Necesitas MetaMask configurado en Sepolia con ETH de prueba para publicar documentos. La consulta y búsqueda son públicas.

---

## Requisitos

| Requisito | Detalle |
|---|---|
| Node.js | ≥ 20 |
| Angular CLI | ≥ 19 |
| MetaMask | Para registrar publicaciones (no necesario para consultar) |
| ETH de prueba | Sepolia faucet: [sepoliafaucet.com](https://sepoliafaucet.com) |

---

## Documentación de referencia

- [Visión del producto](alejandria-frontend/ALEJANDRIA-VISION-README.md) — problema, posicionamiento, stakeholders y requisitos
- [Contratos](alejandria-contracts/README.md) — funciones del contrato, despliegue y configuración de redes
- [Sepolia Etherscan](https://sepolia.etherscan.io/address/0xD54baC82fEDC77c1f74DDC4137A36398694F14CA)

---

> **Estado:** En desarrollo &nbsp;|&nbsp; **Red:** Sepolia Testnet &nbsp;|&nbsp; **Licencia:** MIT
