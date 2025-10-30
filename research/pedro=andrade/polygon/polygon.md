# Polygon (Matic) Node — Guia de Pesquisa

## Visão Geral
Polygon PoS é uma cadeia compatível com **EVM** que atua como solução de **escalabilidade** para Ethereum, com **baixas taxas** e **maior velocidade**.

## Por que está entre os melhores
- Compatibilidade total com o ecossistema Ethereum.
- Latência menor e custos baixos por transação.
- Arquitetura modular (**Bor** execução + **Heimdall** consenso/checkpoints).

## Foco
Baixo custo, boa velocidade, compatibilidade EVM, interoperabilidade com Ethereum.

## Critérios Técnicos
- **Performance (TPS):** ~50–60 médio; picos ~400+  
- **Latência:** ~2 s/bloco  
- **Throughput:** Médio/alto para uso geral  
- **Consenso:** PoS (checkpointing na Ethereum)  
- **Resiliência a ataques:** Alta (herda segurança via checkpoints)  
- **Descentralização:** Média (conjunto de validadores menor)  
- **Facilidade de rodar:** Boa

## Requisitos de Hardware (referência prática)
- CPU 8+ cores  
- RAM 32 GB  
- SSD NVMe 2–4 TB  
- Banda: estável, média/alta

## Custos Operacionais
- **Energia:** baixa  
- **Banda:** média  
- **Armazenamento:** médio (cresce com uso)

## Como conquistou essa posição
- Compatibilidade EVM (baixa fricção de migração).
- Ferramentas e documentação de fácil adoção.
- Estratégia multichain e roadmap (zkEVM, agregação).

## O que aprender para o nosso projeto
- **Separação de camadas** melhora flexibilidade e manutenção.
- Compatibilidade com padrões existentes acelera adoção.
- Diferentes perfis de nó (full, sentry, archive) otimizam custo x performance.

## Ferramentas e DX
- Execução com Bor, consenso com Heimdall; tooling comum de Ethereum.
- Suporte amplo de provedores, SDKs, indexadores.

## Métricas Rápidas
- Boa relação custo/performance; ideal para dApps EVM que buscam escala.
