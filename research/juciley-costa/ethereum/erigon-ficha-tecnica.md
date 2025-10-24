# Erigon — Ficha Técnica

> Execution Client otimizado para eficiência e analytics

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

**Erigon** — Binário principal `erigon` (daemon).

### Blockchain

**Ethereum** — Execução de transações e manutenção do estado EVM. Suporta mainnet, testnets públicas e redes privadas.

### Repositório Oficial

- **GitHub:** [ledgerwatch/erigon](https://github.com/ledgerwatch/erigon)
- **Licença:** LGPL-3.0 / GPL-3.0

---

## 🔧 Especificações Técnicas

### Linguagem de Programação

**Go + Rust** — Implementação otimizada para eficiência de disco e processamento.

### Mecanismo de Consenso

**Proof-of-Stake (PoS)** — Após o Merge

**Arquitetura:**

- **Erigon** é um **execution client** otimizado para eficiência
- Compatível com **consensus clients** via Engine API / AuthRPC
- Mantém total compatibilidade com Geth em termos de APIs

### Descrição Geral

Erigon é um full node Ethereum otimizado para eficiência, velocidade e consultas históricas. Oferece:

- ✅ Baixo uso de disco (até 80% menos que Geth full sync)
- ✅ Sincronização mais rápida e eficiente
- ✅ APIs compatíveis com Geth (JSON-RPC, WebSocket, GraphQL)
- ✅ Consultas históricas e análise de blockchain aceleradas
- ✅ Preparado para trabalhar com consensus clients PoS

---

## 💻 Requisitos de Hardware

### Recomendações Práticas

**Para Full Node Mainnet:**

| Componente | Mínimo | Recomendado |
|------------|--------|-------------|
| **⚙️ CPU** | 4 núcleos | 4-8 núcleos modernos (alto single-core) |
| **🧠 Memória RAM** | 16 GB | 16-32 GB (cache otimizado) |
| **💾 Armazenamento** | SSD | **NVMe essencial** |
| **🌐 Rede** | Estável | Alta banda para sync inicial |

### Espaço em Disco por Modo

| Modo | Espaço Necessário |
|------|-------------------|
| **Full Sync** | ~500 GB |
| **Archive** | 4-6 TB |

> ⚡ **Diferencial:** Erigon usa até 80% menos disco que Geth no full sync

### Tempo de Sincronização

Com hardware moderno (NVMe + boa conexão):

- **Snap Sync:** Algumas horas a ~1 dia
- **Full Sync:** 1-2 dias
- **Archive Sync:** Semanas

> ⚡ **Vantagem:** Sincronização significativamente mais rápida que Geth

---

## 📊 Performance e Métricas

### Métricas da Rede

| Métrica | Valor |
|---------|-------|
| **⏱️ Tempo médio de bloco** | ~12-15 segundos (PoS) |
| **⚡ TPS (transações/segundo)** | Dezenas a centenas (variável) |
| **📦 Blocos por segundo** | Definido pela rede (bloco por slot) |
| **✔️ Finalidade** | Garantida pelo consenso PoS |

### Diferenciais de Performance

- **🚀 Queries históricas** — Mais rápidas que Geth
- **📊 Exportação de dados** — Otimizada para explorers e analytics
- **💾 Eficiência de armazenamento** — Indexação massiva mais eficiente
- **⚡ Velocidade de sync** — Superior ao Geth

**Dados em tempo real:** Use exploradores on-chain (Etherscan, Beaconcha.in)

---

## 🔌 APIs e Interfaces

### JSON-RPC (Principal Interface)

Interface HTTP compatível com Geth para automações e integrações.

**Endpoints padrão Ethereum:**

- `eth_blockNumber` — Número do bloco atual
- `eth_getBalance` — Consultar saldo
- `eth_sendRawTransaction` — Enviar transação
- `eth_call` — Executar call sem state change

**Namespaces suportados:** `eth_`, `net_`, `web3_`

### WebSocket RPC

Subscriptions e eventos em tempo real.

### GraphQL

Interface opcional para consultas flexíveis (ideal para DApps e analytics).

### Engine API / AuthRPC

Comunicação entre execution client (Erigon) e consensus client para operações PoS.

### Compatibilidade

✅ **100% compatível com APIs do Geth** — Permite migração de scripts e ferramentas existentes sem modificações.

---

## 📈 Análise

### ✅ Pontos Fortes

- ✅ **Redução significativa de uso de disco** — Até 80% menos espaço
- ✅ **Consultas históricas rápidas** — Superior ao Geth para analytics
- ✅ **Total compatibilidade com Geth** — Migração facilitada
- ✅ **Sincronização mais rápida** — Snap/full sync acelerado
- ✅ **Otimizado para indexação** — Ideal para explorers e dashboards
- ✅ **Menor custo operacional** — Economia em storage

### ⚠️ Pontos de Atenção

- ⚠️ **Menor popularidade que Geth** — Menos exemplos comunitários
- ⚠️ **Mais consumo de RAM** — Para full node padrão
- ⚠️ **Archive ainda custoso** — Exige espaço massivo (4-6 TB)
- ⚠️ **Documentação menor** — Comunidade menor que Geth

### 🎯 Casos de Uso Ideais

- 📊 **Infraestrutura de analytics** — Explorers, dashboards, indexação histórica
- 🔍 **RPC providers** — Melhor performance em dados históricos
- 💱 **Exchanges e gateways** — Consultas rápidas ao histórico
- 🧪 **Testnets e desenvolvimento** — Simulações com histórico completo
- 📈 **Data warehousing** — Exportação e análise massiva de dados
- 🛡️ **Validadores PoS** — Com consensus client

### 💡 Quando Usar Erigon vs Geth

**Use Erigon se:**
- Precisa de leitura histórica massiva
- Quer reduzir custos de storage (até 80%)
- Foco em analytics e indexação
- Opera explorers ou dashboards
- Necessita queries históricas rápidas

**Use Geth se:**
- Operação simples de execução
- Prioriza maior documentação/exemplos
- Não precisa de analytics pesado
- Prefere a solução mais popular/testada

---

## 📚 Referências

### Documentação Oficial

- [Erigon — GitHub](https://github.com/ledgerwatch/erigon)
- [Erigon — Documentation](https://github.com/ledgerwatch/erigon/blob/master/docs/Readme.md)
- [Erigon — Sync Modes](https://github.com/ledgerwatch/erigon/wiki)

### Recursos Técnicos

- [Ethereum Execution APIs](https://ethereum.github.io/execution-apis/)
- [Ethereum PoS Merge & Engine API](https://ethereum.github.io/execution-apis/api-documentation/)

---
