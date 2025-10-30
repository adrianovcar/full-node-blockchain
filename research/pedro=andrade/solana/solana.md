# Solana Validator

## Visão Geral
Solana combina **PoS** com **Proof of History (PoH)** e execução paralela (**Sealevel**) para alta **performance** e **baixa latência**.

## Por que está entre os melhores
- Throughput muito alto (ordens de magnitude acima de L1s tradicionais).
- Latência de bloco sub-segundo em operação normal.
- Ecossistema forte em DeFi, jogos e aplicações interativas.

## Foco
Velocidade, baixa latência, alto throughput.

## Critérios Técnicos
- **Performance (TPS):** ~1.000–65.000+ (picos >100k em testes)  
- **Latência:** ~0,4 s/bloco  
- **Throughput:** Muito alto  
- **Consenso:** PoH + PoS  
- **Resiliência a ataques:** Alta, porém com trade-off de hardware elevado  
- **Descentralização:** Média (validador tende a operar em data centers)  
- **Facilidade de rodar:** Difícil (operacional exigente)

## Requisitos de Hardware (referência prática)
- CPU 24+ cores / 48+ threads  
- RAM 256–384 GB+ (ECC)  
- NVMe múltiplos de alta IOPS  
- Rede 10 Gbps

## Custos Operacionais
- **Energia:** alta  
- **Banda:** alta  
- **Armazenamento:** alto (alta taxa de dados)

## Como conquistou essa posição
- Arquitetura orientada à paralelização e ordenação temporal (PoH).
- Padrões mínimos claros para validadores; tooling de alta observabilidade.
- Comunidade e incentivos de staking.

## O que aprender para o nosso projeto
- **Performance exige padronização de hardware e SRE**.
- Definir classes de nós (ex.: validador, RPC, arquivo) para custos distintos.
- Telemetria/monitoramento em tempo real são essenciais.

## Ferramentas e DX
- Scripts e playbooks oficiais para validação/RPC.
- Métricas detalhadas, dashboards e alertas.

## Métricas Rápidas
- Throughput líder entre L1s; custo operacional elevado; bom para casos de uso intensivos.
