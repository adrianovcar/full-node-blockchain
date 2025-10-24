# Geth (Go-Ethereum) — Ficha Técnica

> Execution Client de referência da rede Ethereum

---

## 📋 Índice

- [Identificação](#-identificação)
- [Especificações Técnicas](#-especificações-técnicas)
- [Requisitos de Hardware](#-requisitos-de-hardware)
- [Performance e Métricas](#-performance-e-métricas)
- [APIs e Interfaces](#-apis-e-interfaces)
- [Análise](#-análise)
- [Referências](#-referências)

---

## 🏷️ Identificação

### Nome do Cliente

**Geth (Go-Ethereum)** — Binários comumente `geth` (daemon), `geth attach` e `geth console`.

### Blockchain

**Ethereum** — Execução de contratos EVM, rede pública (Mainnet) e diversas testnets. Geth é o execution client mais usado para Ethereum.

### Repositório Oficial

- **GitHub:** [ethereum/go-ethereum](https://github.com/ethereum/go-ethereum)
- **Licença:** LGPL-3.0 (biblioteca) / GPL-3.0 (binários)

---

## 🔧 Especificações Técnicas

### Linguagem de Programação

**Go (Golang)** — Implementação oficial "go-ethereum".

### Mecanismo de Consenso

**Proof-of-Stake (PoS)** — Após o Merge

**Arquitetura:**

- **Geth** é um **execution client** — executa transações, mantém o estado EVM e expõe APIs
- Para participar totalmente do consenso PoS, Geth é emparelhado com um **consensus client** (ex.: Prysm, Lighthouse, Nimbus) através do Engine API / AuthRPC
- **Divisão de responsabilidades:**
  - Geth → Execução e estado
  - Consensus client → Blocos, proposição e finalização via PoS

### Descrição Geral

Geth é a implementação em Go do protocolo Ethereum, amplamente usada por desenvolvedores, provedores de infraestrutura e operadores de nós. Oferece:

- ✅ Execução de transações e manutenção do estado EVM
- ✅ Sincronização com a rede via vários sync modes (snap, full, light)
- ✅ APIs JSON-RPC / WebSocket para apps e serviços
- ✅ Integração com consensus clients para operações PoS

---

## 💻 Requisitos de Hardware

### Recomendações Práticas

**Para Full Node de Produção (Mainnet, serving RPC moderado):**

| Componente | Mínimo | Recomendado |
|------------|--------|-------------|
| **⚙️ CPU** | 4 núcleos | Quad-core moderno (4+ cores, alto GHz) |
| **🧠 Memória RAM** | 8 GB | ≥ 16 GB (cache, GC da Go) |
| **💾 Armazenamento** | SSD | **NVMe essencial** |
| **🌐 Rede** | Estável | Baixa latência, alta banda |

### Espaço em Disco por Modo

| Modo | Espaço Necessário |
|------|-------------------|
| **Full/Snap** | Centenas de GB (crescente) |
| **Archive** | Múltiplos TB (planejar expansão) |

### Tempo de Sincronização

Com hardware moderno (NVMe + boa conexão):

- **Snap Sync:** Horas a algumas dezenas de horas
- **Archive Sync:** Dias ou semanas

> ⚠️ **Importante:** Archive nodes exigem armazenamento massivo e são muito custosos.

---

## 📊 Performance e Métricas

### Métricas da Rede

| Métrica | Valor |
|---------|-------|
| **⏱️ Tempo médio de bloco** | ~12-15 segundos (PoS) |
| **⚡ TPS (transações/segundo)** | Dezenas a centenas (variável) |
| **📦 Blocos por segundo** | Definido pela rede (bloco por slot) |
| **✔️ Finalidade** | Garantida pelo consenso PoS |

### Sobre as Métricas

- **Block/Tx throughput:** Definido pelo protocolo e atividade da rede, não pelo Geth
- **Finalidade:** Responsabilidade do consensus PoS
- **Confirmações:** Uma transação é confirmada quando incluída em blocos; confiança aumenta com confirmações/finality

**Dados em tempo real:** Use exploradores on-chain (Etherscan, Beaconcha.in)

---

## 🔌 APIs e Interfaces

### JSON-RPC (Principal Interface)

Interface HTTP/WebSocket para automações e integrações.

**Principais endpoints:**

- `eth_blockNumber` — Número do bloco atual
- `eth_getBalance` — Consultar saldo
- `eth_sendRawTransaction` — Enviar transação
- `eth_call` — Executar call sem state change

**Documentação:**
- [Geth JSON-RPC Server](https://geth.ethereum.org/docs/interacting-with-geth/rpc)
- [Ethereum Execution APIs](https://ethereum.github.io/execution-apis/api-documentation/)

### Engine API / AuthRPC

Comunicação entre execution client (Geth) e consensus client para operações PoS.

### Modos de Sincronização

- **Snap Sync** — Rápido, padrão para full nodes
- **Full Sync** — Sincronização completa desde genesis
- **Light Sync** — Cliente leve (menor recursos)

**Documentação:** [Geth Sync Modes](https://geth.ethereum.org/docs/fundamentals/sync-modes)

### Monitoramento

- **Prometheus Metrics** — [Docs de métricas](https://geth.ethereum.org/docs/monitoring/metrics)

---

## 📈 Análise

### ✅ Pontos Fortes

- ✅ **Maturidade e compatibilidade** — Implementação amplamente usada e testada
- ✅ **Ecossistema robusto** — Documentação extensa, ferramentas e suporte da comunidade
- ✅ **Integração PoS** — Engine API suportado, pronto para consensus clients
- ✅ **Estabilidade** — Cliente de referência com histórico comprovado
- ✅ **Interoperabilidade máxima** — Padrão da indústria Ethereum

### ⚠️ Pontos de Atenção

- ⚠️ **Uso elevado de disco e memória** — Archive nodes são muito custosos
- ⚠️ **Crescimento contínuo** — Full nodes aumentam de tamanho com o tempo
- ⚠️ **Performance em indexação histórica** — Erigon frequentemente supera Geth em leitura histórica e throughput RPC
- ⚠️ **Não ideal para analytics pesado** — Considerar Erigon para casos de uso intensivo em dados

### 🎯 Casos de Uso Ideais

- 🏦 Operadores de nós públicos e privados
- 💱 Backend para exchanges e DApps
- 🔍 Desenvolvimento e testes de contratos
- 💳 Provedores de infraestrutura RPC
- 🛡️ Validadores Ethereum (com consensus client)
- 📡 Serviços que precisam de máxima compatibilidade

### 💡 Quando Considerar Alternativas

**Use Erigon se:**
- Precisa de leitura histórica massiva
- Requer menor footprint em disco
- Foco em analytics e indexação heavy
- Pode usar arquitetura combinada: Geth para execução + Erigon para indexação

---

## 📚 Referências

### Documentação Oficial

- [Geth — GitHub](https://github.com/ethereum/go-ethereum)
- [Geth — Sync Modes](https://geth.ethereum.org/docs/fundamentals/sync-modes)
- [Geth — Hardware Requirements](https://geth.ethereum.org/docs/getting-started/hardware-requirements)
- [Geth — JSON-RPC Server](https://geth.ethereum.org/docs/interacting-with-geth/rpc)

### Recursos Técnicos

- [Ethereum Execution APIs](https://ethereum.github.io/execution-apis/api-documentation/)
- [Geth — Prometheus Metrics](https://geth.ethereum.org/docs/monitoring/metrics)
- [Ethereum.org — Run a Node](https://ethereum.org/en/developers/docs/nodes-and-clients/)

---
