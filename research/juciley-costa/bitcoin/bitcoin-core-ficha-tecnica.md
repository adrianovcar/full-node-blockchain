# Bitcoin Core — Ficha Técnica

> Full Node de referência da rede Bitcoin

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

**Bitcoin Core**

### Blockchain

**Bitcoin (BTC)** — A primeira rede de criptomoeda descentralizada, projetada para transferências de valor entre pares (peer-to-peer).

### Repositório Oficial

- **GitHub:** [bitcoin/bitcoin](https://github.com/bitcoin/bitcoin)
- **Site oficial:** [bitcoincore.org](https://bitcoincore.org) | [bitcoin.org](https://bitcoin.org)
- **Licença:** MIT

---

## 🔧 Especificações Técnicas

### Linguagem de Programação

**C++** — Implementação principal mantida como projeto Bitcoin Core.

**Componentes:**

- \`bitcoind\` — Daemon / Full Node
- \`bitcoin-cli\` — Ferramenta RPC CLI

### Mecanismo de Consenso

**Proof-of-Work (PoW)**

Mineradores competem para resolver um problema computacional (hashing SHA-256) para produzir um bloco válido. O bloco vencedor recebe uma recompensa (nova emissão + taxas) e é propagado para a rede.

**Ajuste de Dificuldade:** Periódico para manter tempo médio de ~10 minutos entre blocos.

**Papel do Full Node:**

- Valida blocos e transações conforme as regras do protocolo
- Verifica assinaturas, formato, dificuldade e regras de consenso
- Aceita apenas a cadeia com maior trabalho acumulado (proof-of-work)

### Descrição Geral

Bitcoin Core é o cliente full node de referência para a rede Bitcoin. Um full node operando com Bitcoin Core:

- ✅ Conecta-se à rede P2P e valida blocos/transações
- ✅ Mantém cópia completa (ou pruned) da blockchain local
- ✅ Oferece interface RPC para consultas e envio de transações (JSON-RPC)
- ✅ Opera como wallet (opcional), explorer local ou backend para serviços

---

## 💻 Requisitos de Hardware

### Recomendações Práticas

| Componente | Mínimo | Recomendado |
|------------|--------|-------------|
| **💾 Armazenamento** | ≥ 350 GB | NVMe/SSD (I/O rápido) |
| **🧠 Memória RAM** | 1 GB | 8–16 GB |
| **⚙️ CPU** | 2 núcleos | 4+ vCPUs |
| **🌐 Rede** | Estável | Hundreds MB/dia |

### Modos de Armazenamento

| Modo | Descrição |
|------|-----------|
| **Full (padrão)** | Armazena todos os blocos desde o genesis |
| **Pruned** | Mantém apenas blocos necessários (reduz espaço, sem histórico completo) |

### Tempo de Sincronização

Com hardware moderno (SSD NVMe + boa conexão):

- **Estimativa:** 12–72 horas
- **Variável:** Depende do modo (full/pruned) e capacidade do hardware

---

## 📊 Performance e Métricas

### Métricas da Rede

| Métrica | Valor |
|---------|-------|
| **⏱️ Tempo médio de bloco** | ~10 minutos (600s) |
| **⚡ TPS (transações/segundo)** | ~1 a 7 tps |
| **📦 Tamanho médio do bloco** | Centenas de KB a ~1 MB |
| **✔️ Finalidade** | Não instantânea (baseada em confirmações) |

### Confirmações

Bitcoin não possui finalidade instantânea. Transações ganham segurança com confirmações sucessivas:

- **1 confirmação** — Transações pequenas/baixo risco
- **6 confirmações** — Padrão para maior segurança
- Cada confirmação reduz a probabilidade de reversão

**Dados em tempo real:** [bitinfocharts.com/bitcoin](https://bitinfocharts.com/bitcoin/)

---

## 🔌 APIs e Interfaces

### JSON-RPC (Principal Interface)

Interface HTTP para automações e integrações.

**Exemplos de comandos:**

- \`getblockchaininfo\` — Informações da blockchain
- \`getrawtransaction\` — Dados de transação
- \`sendrawtransaction\` — Enviar transação

**Documentação:** [developer.bitcoin.org/reference/rpc](https://developer.bitcoin.org/reference/rpc/)

### Protocolo P2P

Comunicação entre nós para propagar blocos e transações (essencial para funcionamento da rede).

### CLI Local

\`bitcoin-cli\` — Ferramenta de linha de comando que usa IPC/HTTP para comunicar com \`bitcoind\`.

---

## 📈 Análise

### ✅ Pontos Fortes

- ✅ **Cliente de referência** amplamente testado e confiável
- ✅ **Alto nível de descentralização** e compatibilidade
- ✅ **Segurança sólida** com regras de consenso validadas globalmente
- ✅ **Grande ecossistema** de ferramentas e documentação
- ✅ **Comunidade ativa** e manutenção contínua

### ⚠️ Pontos de Atenção

- ⚠️ **Baixa taxa de transações** comparada a blockchains modernas
- ⚠️ **Requisitos de armazenamento crescentes** (blockchain sempre aumenta)
- ⚠️ **Sincronização inicial demorada** — I/O intensivo (requer SSD/NVMe)
- ⚠️ **Não adequado para alto throughput** (limitação por design do protocolo)

### 🎯 Casos de Uso Ideais

- 🏦 Serviços de custódia de Bitcoin
- 💱 Backend para exchanges e gateways
- 🔍 Auditoria e análise da blockchain
- 💳 Infraestrutura de pagamentos
- 🛡️ Operações que exigem máxima independência e segurança

---

## 📚 Referências

### Documentação Oficial

- [Bitcoin Core — GitHub](https://github.com/bitcoin/bitcoin)
- [Bitcoin.org — Full Node Guide](https://bitcoin.org/en/full-node)
- [Bitcoin Core Features & Requirements](https://bitcoin.org/en/bitcoin-core/features/requirements)
- [RPC API Reference](https://developer.bitcoin.org/reference/rpc/)

### Recursos Técnicos

- [Whitepaper Original — Satoshi Nakamoto](https://bitcoin.org/bitcoin.pdf)
- [Métricas da Rede Bitcoin — BitInfoCharts](https://bitinfocharts.com/bitcoin/)
- [Blockchain Charts — TPS & Stats](https://www.blockchain.com/charts/transactions-per-second)

---