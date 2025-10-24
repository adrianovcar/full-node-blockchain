# Stellar Core — Ficha Técnica

> Full Node da rede Stellar para pagamentos e ativos digitais

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

**Stellar Core** — Software oficial responsável por manter e validar o ledger da rede Stellar.

### Blockchain

**Stellar Network** — Blockchain pública voltada para pagamentos, remessas internacionais e emissão de ativos digitais.

Foco em eficiência e interoperabilidade financeira. Mantida pela **Stellar Development Foundation (SDF)**.

### Repositório Oficial

- **GitHub:** [stellar/stellar-core](https://github.com/stellar/stellar-core)
- **Licença:** Apache 2.0 (uso comercial e acadêmico permitido)

---

## 🔧 Especificações Técnicas

### Linguagem de Programação

**C++** — Implementação nativa para máxima eficiência, estabilidade e segurança.

### Mecanismo de Consenso

**Stellar Consensus Protocol (SCP)** — Modelo de consenso federado (FBA - Federated Byzantine Agreement).

**Diferente de PoW e PoS:**
- Cada nó escolhe um conjunto de quorums confiáveis (quorum slices)
- As decisões são tomadas quando o quorum entra em consenso
- Garante baixa latência, segurança bizantina e descentralização flexível

**Vantagens:**
- ✅ Consenso sem mineração
- ✅ Consumo de energia mínimo
- ✅ Finalidade rápida (~5 segundos)

**Papel do Stellar Core:**
- Executa o protocolo SCP
- Valida e propaga transações
- Mantém o estado do ledger
- Participa no consenso federado

### Descrição Geral

O Stellar Core é o motor de consenso e ledger da blockchain Stellar. Oferece:

- ✅ Recepção e validação de transações
- ✅ Propagação de blocos e estado de ledger
- ✅ Participação no consenso SCP
- ✅ Interação com Horizon (camada de API pública)
- ✅ Armazenamento de histórico de ledger e checkpoints

---

## 💻 Requisitos de Hardware

### Recomendações Práticas

**Para Mainnet Stellar:**

| Componente | Especificação |
|------------|---------------|
| **⚙️ CPU** | 4 núcleos modernos |
| **🧠 Memória RAM** | 8-16 GB |
| **💾 Armazenamento** | SSD ≥ 500 GB |
| **🌐 Rede** | ≥ 100 Mbps (baixa latência) |
| **🗄️ Banco de Dados** | PostgreSQL (obrigatório) |

### Sistema Operacional

- **Recomendado:** Linux (Ubuntu)
- **Suporte:** Windows e macOS (desenvolvimento)

### Considerações Importantes

> ⚠️ **Crítico:** Stellar Core requer PostgreSQL para armazenar ledger e histórico

**Impactos:**
- **PostgreSQL bem configurado** → Performance otimizada
- **SSD rápido** → Sync e queries eficientes
- **Rede estável** → Consenso sem atrasos

### Crescimento do Ledger

- **Crescimento:** Moderado e controlado
- **Checkpoints:** Sistema de snapshots reduz armazenamento
- **Storage:** 500 GB inicial, crescimento gradual

---

## 📊 Performance e Métricas

### Métricas da Rede

| Métrica | Valor |
|---------|-------|
| **⏱️ Ledger close time** | ~5 segundos |
| **⚡ TPS (médio)** | ~1.000 tps |
| **📦 TPS (pico)** | > 3.000 tps |
| **✔️ Finalidade** | Praticamente imediata (~5s) |
| **🔋 Consumo de energia** | Extremamente baixo (sem PoW/PoS) |

### Sobre as Métricas

**Throughput:**
- Média de ~1.000 transações por segundo
- Picos superiores a 3.000 tps em condições ideais
- Adequado para pagamentos globais e stablecoins

**Finalidade:**
- Consenso SCP garante finalidade em ~5 segundos
- Muito mais rápido que blockchains PoW
- Ideal para aplicações financeiras em tempo real

**Escalabilidade:**
- Projetado para pagamentos de alto volume
- Eficiente para transferências cross-border
- Baixíssimo custo por transação

---

## 🔌 APIs e Interfaces

### Horizon API (Principal Interface)

**Stellar Core não é acessado diretamente por DApps** — ele se comunica com **Horizon**, que fornece a API pública.

**Principais endpoints Horizon:**

- `/accounts` — Informações de contas
- `/transactions` — Histórico de transações
- `/payments` — Consultar pagamentos
- `/operations` — Operações realizadas
- `/assets` — Ativos emitidos na rede

**Documentação:** [Horizon API Reference](https://developers.stellar.org/api)

### Command-Line Interface

Interface administrativa para operação do nó.

**Principais comandos:**

- `stellar-core run` — Iniciar o nó
- `stellar-core info` — Informações do nó
- `stellar-core http-command` — Comandos via HTTP

### Peer-to-Peer (Overlay)

Comunicação entre nós via protocolo SCP para consenso e propagação.

### Database (PostgreSQL)

- **Armazenamento:** Ledger, histórico e metadados
- **Queries:** Consultas históricas e estado atual
- **Checkpoints:** Snapshots periódicos do ledger

### Monitoramento

- **Métricas nativas** — Logs e status do nó
- **Prometheus/Grafana** — Integração disponível
- **Dashboard SDF** — Monitoramento da rede Stellar

---

## 📈 Análise

### ✅ Pontos Fortes

- ✅ **Consenso rápido e eficiente** — SCP sem mineração
- ✅ **Baixíssimo consumo de energia** — Sustentável
- ✅ **Finalidade em segundos** — Ideal para pagamentos
- ✅ **Foco em interoperabilidade** — Cross-border e multi-moedas
- ✅ **Licença aberta** — Apache 2.0, código auditável
- ✅ **Alta confiabilidade** — Operações financeiras críticas
- ✅ **Custo por transação muito baixo** — Frações de centavo

### ⚠️ Pontos de Atenção

- ⚠️ **Menor descentralização** — Quoruns federados vs PoW/PoS
- ⚠️ **Não é EVM-compatible** — Menor flexibilidade para DApps complexos
- ⚠️ **Requer PostgreSQL** — Dependência adicional de infraestrutura
- ⚠️ **Integração via Horizon** — Camada extra necessária para APIs públicas
- ⚠️ **Menos adoção DeFi** — Foco em pagamentos, não em contratos complexos

### 🎯 Casos de Uso Ideais

- 💰 **Validadores da rede Stellar** — Mainnet e testnets
- 🏦 **Bancos e fintechs** — Emissão de stablecoins e ativos
- 🌍 **Pagamentos cross-border** — Remessas internacionais
- 💱 **Gateways de pagamento** — Conversão de moedas
- 🔍 **Infraestrutura de indexação** — Observabilidade via Horizon
- 📊 **Exchanges de ativos** — Trading de tokens Stellar

### 💡 Considerações Operacionais

**Necessário para operar validator:**
- Configuração adequada de PostgreSQL
- Monitoramento contínuo do nó
- Integração com Horizon para APIs públicas
- Definição de quorum slices confiáveis
- Backup regular do banco de dados
- Atualizações frequentes do software

---

## 📚 Referências

### Documentação Oficial

- [Stellar Core — GitHub](https://github.com/stellar/stellar-core)
- [Stellar Developers Docs](https://developers.stellar.org/docs)
- [Node Setup Guide](https://developers.stellar.org/docs/run-core-node)
- [Horizon API Reference](https://developers.stellar.org/api)

### Recursos Técnicos

- [Stellar Consensus Protocol (SCP) — Paper](https://www.stellar.org/papers/stellar-consensus-protocol.pdf)
- [Stellar Network Overview](https://www.stellar.org/developers)
- [Stellar Development Foundation](https://stellar.org/)

---
