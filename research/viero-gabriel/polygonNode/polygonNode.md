# Polygon (Matic) Node

## Overview

**Nome da Blockchain:** Polygon (PoS)

**Documentação oficial:** "Node system requirements"

**Descrição:** A rede Polygon é uma solução de escalabilidade para Ethereum, compatível com EVM, com taxas mais baixas e velocidade elevada em comparação com redes de camada 1. Executar um nó full/validador ajuda a dar suporte à rede.

**Propósito de uso:** Rodar um nó na Polygon (por exemplo full node ou validador) permite contribuir para a rede, fazer parte da infraestrutura que atende dApps, prover endpoints, ou atuar como validador para staking e recompensas.

**Foco:** Low-cost, alta velocidade, compatibilidade com Ethereum (EVM) — ideal para casos onde se quer escalabilidade em vez de rede "massiva ordem de bloqueio".

## Tipo de Consenso

**Mecanismo:** A rede Polygon PoS opera com validação baseada em Proof of Stake (PoS) — qualquer participante que rode nó validador (sentry + validator) pode participar.

Assim, os nós validadores participam no consenso, bloco/validação no ecossistema Polygon.

## Requisitos de Hardware / Nó Completo / Validador

### Requisitos Aproximados para Nó de Produção

**CPU:** ~8-16 cores (alguns requisitos apontam 16-core para recomendação).

**RAM:** ~32-64 GB ou mais.

**Armazenamento:** ~2.5 TB SSD mínimo, recomendado ~5 TB ou mais.

**Rede:** Conexão de no mínimo 1 Gbit/s para operação eficiente.

**Nota:** Menor custo que Solana, mais "acessível", mas ainda requer boa infraestrutura.

### Especificações Detalhadas por Fonte

- **Cherry Servers:** RAM mínima 32 GB, CPU 8-core; recomendado RAM 64 GB, CPU 16-core; storage 2.5 TB SSD mínimo; Largura de banda 1 Gbit/s.
- **BlockMeadow:** Requisitos mínimos: RAM 32 GB, CPU 8-core, Storage 2.5 TB SSD; Recomendados: RAM 64 GB, CPU 16-core, Storage 5 TB SSD; Largura de banda 1 Gbit/s.
- **NodeShift (zkNode):** CPU 4 core, RAM 16 GB para instalação básica/zkNode.

## O que chamou atenção / Insights

- A Polygon oferece uma boa combinação de escalabilidade e compatibilidade (com EVM) — bem adequado para projetos que querem rodar dApps ou nós com menos barreira de entrada comparado a redes ultra-alta performance.
- Mesmo assim, para ambientes de produção e full-nodes que suportem alto tráfego, os requisitos de hardware ainda são relativamente robustos.
- Se o objetivo for infraestrutura de suporte a dApps/infraestrutura layer 2, rodar nó Polygon pode ser "custo moderado" comparado a redes de throughput massivo.

## Por que escolher este nó

- Quando o foco for escalabilidade com custos moderados, compatibilidade com Ethereum, e você deseja atuar como infraestrutura (full node ou validador) numa rede bem adotada.
- Boa escolha se não for necessário "ultra-baixa latência / ultra-alto throughput" mas sim um equilíbrio entre velocidade, custo e compatibilidade.

## Fontes

- https://docs.polygon.technology/pos/how-to/prerequisites/
- https://docs.polygon.technology/pos/get-started/becoming-a-validator/
- https://www.cherryservers.com/blog/how-to-run-a-polygon-node
- https://www.blockmeadow.com/how-to-deploy-a-polygon-node-on-linux/
- https://docs.polygon.technology/zkEVM/get-started/setup-nodes/deploy-zkevm/prerequisites/