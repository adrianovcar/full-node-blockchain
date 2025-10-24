# Kaspa (rusty-kaspa) — Ficha Técnica

> Full Node BlockDAG de alta performance para a rede Kaspa

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

**rusty-kaspa (kaspad)** — Implementação de referência em Rust do full node Kaspa.

### Blockchain

**Kaspa (KAS)** — Layer-1 pública que implementa o protocolo GHOSTDAG (BlockDAG) com segurança Proof-of-Work (PoW).

Projetada para alta taxa de produção de blocos preservando segurança e descentralização.

### Repositório Oficial

- **GitHub:** [kaspanet/rusty-kaspa](https://github.com/kaspanet/rusty-kaspa)
- **Licença:** ISC (permissiva para uso comercial e acadêmico)

---

## 🔧 Especificações Técnicas

### Linguagem de Programação

**Rust** — Implementação de referência recomendada, substituindo a versão anterior em Go.

O projeto inclui:
- Daemon do nó (kaspad)
- Bibliotecas auxiliares
- RPC e gRPC
- Ferramentas de indexação
- Dockerfiles e documentação de build

### Mecanismo de Consenso

**GHOSTDAG** — Variante de consenso PoW para BlockDAG

**Diferente do Bitcoin tradicional:**
- Em vez de descartar blocos concorrentes (forks), organiza blocos em um DAG
- Define ordem via peso das sub-estruturas
- Mantém segurança PoW mas permite blocos paralelos
- Throughput maior com menor desperdício de trabalho
- Latência de confirmação reduzida

**Papel do Nó:**
- Valida provas de trabalho
- Reconstrói e mantém o DAG
- Computa ordens topológicas
- Responde a queries RPC/gRPC

### Descrição Geral

O rusty-kaspa é a implementação em Rust do nó completo Kaspa. Oferece:

- ✅ Participação na rede P2P
- ✅ Download e propagação de blocos DAG
- ✅ Validação de blocos e aplicação de regras do protocolo (KIPs)
- ✅ Mineração (quando configurado)
- ✅ APIs gRPC/JSON-RPC para wallets, exchanges e exploradores
- ✅ Imagens Docker e scripts de build multi-arquitetura

---

## 💻 Requisitos de Hardware

### Recomendações Práticas

**Para Mainnet Kaspa:**

| Componente | Especificação |
|------------|---------------|
| **⚙️ CPU** | 4-12 núcleos (8+ para mineração/alta carga) |
| **🧠 Memória RAM** | 8-32 GB (16 GB recomendado para nós públicos) |
| **💾 Armazenamento** | NVMe SSD ≥ 500 GB (monitorar crescimento) |
| **🌐 Rede** | Conexão estável com boa banda |
| **🛠️ Build Toolchain** | Rust/cargo, Protobuf, LLVM/clang |

### Sistema Operacional

- **Suporte:** Linux, Windows, macOS
- **Recomendado:** Linux para produção
- **Docker:** Imagens multi-arquitetura disponíveis

### Considerações Importantes

> ⚠️ **Crítico:** Após Crescendo Hardfork, blockrate aumentou de 1 BPS para 10 BPS

**Impactos:**
- **Alto I/O** → NVMe essencial para acompanhar DAG
- **Crescimento acelerado** → Planejamento de storage necessário
- **Indexadores** → Maior carga de processamento e armazenamento

### Crescimento do Ledger

- **Crescimento:** Acelerado após Crescendo (10 BPS)
- **DAG e índices:** Crescem continuamente
- **Storage:** Começar com ≥ 500 GB, monitorar ativamente
- **Snapshots:** Scripts disponíveis no repositório

### Tempo de Sincronização

- **Variável:** Depende de hardware, banda e estado da rede
- **Otimização:** Docker e snapshots aceleram sync inicial
- **Estimativa:** Horas a dias (com hardware adequado)

---

## 📊 Performance e Métricas

### Métricas da Rede

| Métrica | Valor |
|---------|-------|
| **⏱️ Blockrate (pré-Crescendo)** | 1 BPS |
| **⚡ Blockrate (pós-Crescendo)** | 10 BPS (desde 05/05/2025) |
| **📦 TPS** | Variável (aumentado com blockrate) |
| **✔️ Finalidade** | Probabilística PoW (mais rápida que cadeias lineares) |
| **🔗 Estrutura** | BlockDAG (blocos paralelos) |

### Sobre as Métricas

**Crescendo Hardfork (05 Maio 2025):**
- Alterou blockrate de 1 BPS para 10 BPS
- Introduziu diversos KIPs (Kaspa Improvement Proposals)
- Impacto direto em throughput e requisitos de infraestrutura

**Throughput:**
- TPS variável dependendo do tamanho médio de transações
- Blockrate elevado aumenta capacidade efetiva da rede
- Modelo DAG permite processamento paralelo

**Finalidade:**
- Confirmações mais rápidas que cadeias lineares PoW
- Finalidade probabilística similar ao Bitcoin
- Múltiplos blocos integrados na ordem do DAG

**Escalabilidade:**
- BlockDAG permite crescimento horizontal
- Menor desperdício de trabalho de mineração
- Latência de confirmação reduzida

---

## 🔌 APIs e Interfaces

### gRPC (Principal Interface)

Interface moderna e eficiente para integrações.

**Principais usos:**

- Wallets e exchanges
- Indexadores e exploradores
- Consultas de blocos e transações
- Subscrições de eventos em tempo real

**Documentação:** Disponível no repositório rusty-kaspa

### JSON-RPC

Interface HTTP para compatibilidade com ferramentas tradicionais.

**Endpoints comuns:**

- Consultar blocos
- Enviar transações
- Verificar saldo
- Obter informações da rede

### P2P Network

Comunicação entre nós para propagação de blocos DAG e mempool.

### Prometheus Metrics

- **Métricas nativas** — Telemetria e monitoramento
- **Endpoints expostos** — Integração com Prometheus/Grafana
- **Observabilidade** — Performance e saúde do nó

### Docker & Build Tools

- **Multi-arch images** — Suporte para diferentes arquiteturas
- **Scripts de build** — Automação de compilação e deploy
- **Snapshots** — Sincronização acelerada

---

## 📈 Análise

### ✅ Pontos Fortes

- ✅ **Implementação Rust moderna** — Performance e segurança de memória
- ✅ **BlockDAG (GHOSTDAG)** — Alta taxa de blocos sem desperdício
- ✅ **Confirmações rápidas** — Latência reduzida vs cadeias lineares
- ✅ **Ferramentas modernas** — gRPC, Docker multi-arch, métricas
- ✅ **PoW seguro** — Mantém descentralização e resistência
- ✅ **Crescendo Hardfork** — 10 BPS aumenta throughput significativamente
- ✅ **Código aberto** — Licença ISC permissiva

### ⚠️ Pontos de Atenção

- ⚠️ **Ecossistema em crescimento** — Menos maduro que Bitcoin/Ethereum
- ⚠️ **Alto crescimento de storage** — 10 BPS exige planejamento
- ⚠️ **Requisitos de I/O elevados** — NVMe essencial
- ⚠️ **Integrações de terceiros** — Algumas ferramentas ainda em desenvolvimento
- ⚠️ **Monitoramento constante** — Crescimento do DAG requer atenção
- ⚠️ **Complexidade do DAG** — Diferente de blockchains lineares tradicionais

### 🎯 Casos de Uso Ideais

- ⛏️ **Mineradores PoW** — Participar da segurança da rede
- 💱 **Exchanges e wallets** — Indexação e validação de transações
- 🔍 **Indexadores e exploradores** — Histórico e análise de blocos
- 🧪 **Pesquisa e desenvolvimento** — Estudar BlockDAG e KIPs(Kaspa Improvement Proposals)
- 📊 **Analytics** — Consumir gRPC para métricas e gráficos
- 🏗️ **Infraestrutura RPC** — Servir aplicações e serviços

### 💡 Considerações Operacionais

**Necessário para operar nó:**
- Build toolchain configurado (Rust, Protobuf, LLVM)
- Monitoramento ativo de disco e I/O
- Ajustes pós-Crescendo (10 BPS)
- Backup e snapshots regulares
- Planejamento de expansão de storage
- Integração com ferramentas de observabilidade

**Atenção ao Crescendo Hardfork:**
- Blockrate 10x maior (1→10 BPS)
- Impacto em indexadores e armazenamento
- Ajustar recursos conforme notas de release
- Testar em testnet antes de produção

---

## 📚 Referências

### Documentação Oficial

- [Kaspa Official Site](https://kaspa.org/)
- [rusty-kaspa — GitHub](https://github.com/kaspanet/rusty-kaspa)
- [rusty-kaspa — README & Build Instructions](https://github.com/kaspanet/rusty-kaspa/blob/master/README.md)

### Recursos Técnicos

- [GHOSTDAG Protocol](https://eprint.iacr.org/2018/104.pdf)
- [Crescendo Hardfork Notes](https://github.com/kaspanet/rusty-kaspa/releases)
- [KIPs — Kaspa Improvement Proposals](https://github.com/kaspanet/kips)

---
