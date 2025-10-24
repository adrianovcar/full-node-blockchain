# Hyperledger Besu — Ficha Técnica

> Execution Client corporativo para redes públicas e privadas

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

**Hyperledger Besu** — Binário principal `besu`.

### Blockchain

**Ethereum (Mainnet e Testnets)** e **Consórcios Privados** (Hyperledger / Quorum).

Besu é frequentemente usado em ambientes corporativos devido à compatibilidade PoA e opções de permissionamento.

### Repositório Oficial

- **GitHub:** [hyperledger/besu](https://github.com/hyperledger/besu)
- **Licença:** Apache 2.0 (adequado para uso corporativo)

---

## 🔧 Especificações Técnicas

### Linguagem de Programação

**Java** — Implementado em Java 11+, usando bibliotecas modernas de rede e criptografia.

### Mecanismo de Consenso

**Besu suporta múltiplos algoritmos:**

**Proof-of-Authority (PoA)**
- Usado em redes permissionadas
- Algoritmos: IBFT 2.0, Clique
- Ideal para consórcios corporativos

**Proof-of-Stake (PoS)**
- Pós-Merge na Mainnet
- Besu funciona como execution client
- Conectado a consensus client via Engine API

**Flexibilidade:** Cada modo altera validação de blocos e consenso. PoA para redes privadas, PoS para públicas.

### Descrição Geral

Hyperledger Besu é um full node Ethereum corporativo e versátil. Oferece:

- ✅ Execução e validação de transações Ethereum
- ✅ Suporte a redes públicas e privadas (permissionadas)
- ✅ APIs compatíveis com JSON-RPC, WebSocket e GraphQL
- ✅ Auditoria, monitoramento, tracing e métricas avançadas
- ✅ Integração com consensus clients PoS via Engine API

---

## 💻 Requisitos de Hardware

### Recomendações Práticas

**Para Full Node Mainnet/Produção:**

| Componente | Mínimo | Recomendado |
|------------|--------|-------------|
| **⚙️ CPU** | 4 núcleos | 4-8 núcleos modernos (JVM eficiente) |
| **🧠 Memória RAM** | 16 GB | ≥ 32 GB (nodes públicos pesados) |
| **💾 Armazenamento** | SSD | **NVMe essencial** |
| **🌐 Rede** | Estável | Alta banda para sync inicial |

### Espaço em Disco por Modo

| Modo | Espaço Necessário |
|------|-------------------|
| **Full Node Mainnet** | ~500 GB |
| **Archive** | > 4 TB |

### Tempo de Sincronização

Com hardware moderno (NVMe + boa conexão):

- **Snap/Full Sync:** Horas a dias
- **Archive Sync:** Semanas

> ⚠️ **Importante:** Archive nodes exigem armazenamento massivo e JVM tuning adequado.

---

## 📊 Performance e Métricas

### Métricas da Rede

| Métrica | Valor |
|---------|-------|
| **⏱️ Tempo médio de bloco** | ~12-15 segundos (PoS) |
| **⚡ TPS (transações/segundo)** | Dezenas a centenas (variável) |
| **📦 Blocos por segundo** | ~1 bloco por slot |
| **✔️ Finalidade** | Determinada pelo consensus client PoS |

### Diferenciais Corporativos

- **📊 Auditoria completa** — Rastreamento detalhado de transações
- **🔍 Tracing de contratos** — Debug e análise avançada
- **🔐 Permissioning** — Controle de acesso granular
- **📈 Monitoramento** — Métricas e eventos de rede avançados

**Nota:** Besu não finaliza blocos sozinho; depende do consensus client em PoS.

---

## 🔌 APIs e Interfaces

### JSON-RPC (Principal Interface)

Interface HTTP/WebSocket compatível com Ethereum.

**Principais endpoints:**

- `eth_blockNumber` — Número do bloco atual
- `eth_getBalance` — Consultar saldo
- `eth_sendRawTransaction` — Enviar transação
- `eth_call` — Executar call sem state change

### WebSocket

Subscriptions e eventos em tempo real.

### GraphQL

Interface para consultas flexíveis e estruturadas.

### Engine API / AuthRPC

Comunicação entre execution client (Besu) e consensus client para operações PoS.

### APIs Exclusivas

- **Permissioning APIs** — Controle de acesso e permissões
- **Tracing APIs** — Debug detalhado de transações
- **Metrics & Monitoring** — Prometheus, logs estruturados

**Documentação:**
- [Besu API Documentation](https://besu.hyperledger.org/public-networks)
- [Besu Private Networks](https://besu.hyperledger.org/private-networks)

---

## 📈 Análise

### ✅ Pontos Fortes

- ✅ **Suporte corporativo e licença permissiva** — Apache 2.0
- ✅ **Múltiplos modos de consenso** — PoS e PoA
- ✅ **APIs ricas** — Tracing, metrics, permissioning
- ✅ **Flexibilidade** — Redes públicas e privadas
- ✅ **Auditoria avançada** — Ideal para compliance
- ✅ **Integração empresarial** — Hyperledger ecosystem

### ⚠️ Pontos de Atenção

- ⚠️ **Mais pesado em recursos** — Comparado a Geth para nós simples
- ⚠️ **Menor popularidade** — Menos exemplos para DApps públicas
- ⚠️ **JVM tuning necessário** — Para nodes de alta performance
- ⚠️ **Consumo de memória** — Requer mais RAM que alternativas

### 🎯 Casos de Uso Ideais

- 🏢 **Empresas e consórcios privados** — PoA / redes permissionadas
- 🏦 **Infraestrutura corporativa Ethereum** — PoS execution client
- 📊 **Analytics e tracing** — Monitoramento de contratos inteligentes
- 💱 **Exchanges e gateways** — Integração RPC/WebSocket robusta
- 🔐 **Ambientes regulados** — Auditoria e compliance
- 🤝 **Blockchain de consórcio** — Hyperledger/Quorum networks

### 💡 Quando Usar Besu

**Use Besu se:**
- Precisa de redes privadas/permissionadas (PoA)
- Requer auditoria e compliance rigorosos
- Opera em ambiente corporativo/enterprise
- Necessita de tracing avançado
- Trabalha com Hyperledger ecosystem
- Precisa de múltiplos modos de consenso

**Use Geth/Erigon se:**
- Foco apenas em rede pública
- Prioriza menor consumo de recursos
- Não precisa de permissioning
- Opera DApps simples

---

## 📚 Referências

### Documentação Oficial

- [Hyperledger Besu — GitHub](https://github.com/hyperledger/besu)
- [Besu — Public Networks](https://besu.hyperledger.org/public-networks)
- [Besu — Private Networks](https://besu.hyperledger.org/private-networks)
- [Besu — API Documentation](https://besu.hyperledger.org/public-networks/reference/api)

### Recursos Técnicos

- [Hyperledger Besu Wiki](https://lf-hyperledger.atlassian.net/wiki/spaces/BESU/overview)
- [Ethereum Execution APIs](https://ethereum.github.io/execution-apis/)
- [Hyperledger Foundation](https://www.hyperledger.org/)

---
