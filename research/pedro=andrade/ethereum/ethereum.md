# Geth (Ethereum)
## Visão Geral
Geth (Go-Ethereum) é o cliente mais usado da **Ethereum**. Após o Merge, a rede utiliza **PoS** e mantém a **EVM** como máquina de execução de contratos inteligentes.

## Por que está entre os melhores
- Ecossistema de smart contracts mais maduro.
- Cliente estável e amplamente adotado, com diversidade de clientes (Erigon, Nethermind).
- Grande base de desenvolvedores e tooling.

## Foco
Contratos inteligentes, compatibilidade EVM, ecossistema DeFi/NFT/infra.

## Critérios Técnicos
- **Performance (TPS):** ~15–30 TPS (camada base)  
- **Latência:** ~12–15 s/bloco  
- **Throughput:** Médio  
- **Consenso:** PoS (staking)  
- **Resiliência a ataques:** Alta (slashing, economic security)  
- **Descentralização:** Alta (diversidade de clientes e operadores)  
- **Facilidade de rodar:** Boa (exige mais recursos que Bitcoin)

## Requisitos de Hardware (referência prática)
- CPU 8+ cores  
- RAM 32–64 GB  
- SSD NVMe 4–8 TB (nó de arquivo demanda bem mais)  
- Banda: 300–500 Mbps recomendado

## Custos Operacionais
- **Energia:** baixa (PoS)  
- **Banda:** média/alta conforme carga  
- **Armazenamento:** elevado e crescente (estado/arquivo)

## Como conquistou essa posição
- Design EVM e foco em programabilidade.
- Forte comunidade, documentação e ferramentas de monitoramento.
- Roadmap contínuo de escalabilidade (L2, melhorias de execução).

## O que aprender para o nosso projeto
- **Modos de nó** (full x archive) para perfis distintos de uso.
- **DX forte** (documentação, métricas, logs) impulsiona adoção.
- Planejar crescimento do estado e opções de pruning/snapshots.

## Ferramentas e DX
- CLI consolidada, JSON-RPC padrão de mercado, ferramentas de tracing e profiling.
- Integração com L2s e provedores de RPC.

## Métricas Rápidas
- Finalidade via PoS; throughput base modesto; escala via L2.
