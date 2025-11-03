# Stellar Core Validator

## Overview

**Nome da Blockchain:** Stellar

**Documentação oficial:** "Prerequisites – Stellar Core"

**Descrição:** A rede Stellar foca em remessas/pagamentos globais, interoperabilidade financeira, taxas baixas, e alta velocidade de consenso (≈ 3-5 segundos conforme documentação de consenso). O software "Stellar Core" é usado para rodar nós validadores que participam da manutenção da rede.

**Propósito de uso:** Rodar um nó validador Stellar ajuda a: (i) garantir a segurança e resiliência da rede, (ii) suportar remessas, emissão de ativos e interoperabilidade, (iii) participar de uma rede de pagamento global com baixas taxas.

**Foco:** Remessas/pagamentos globais, interoperabilidade financeira, baixas taxas, alta velocidade (≈ 5 segundos ou menos).

## Tipo de Consenso

**Mecanismo:** A rede Stellar usa o Stellar Consensus Protocol (SCP), baseado em Federated Byzantine Agreement (FBA) — não usa PoW ou PoS tradicionais.

Os validadores definem suas "quorum slices", participam do consenso via FBA e ajudam a manter a rede rápida e eficiente.

## Requisitos de Hardware / Nó Validador

### Requisitos Aproximados para Nó de Validação

**CPU:** 8 vCPU (ex: 8× Intel Xeon @3.4 GHz) – conforme documento oficial.

**RAM:** 16 GB – conforme documento oficial (nota: para carga leve; caso maior demanda, aumentar).

**Armazenamento:** 100 GB NVMe SSD para nó básico; para operação de longo prazo ou histórico completo, recomenda pelo menos 1 TB.

**Rede / largura de banda:** O documento oficial exige que portas TCP para entrada/saída estejam abertas (ex: default peer port 11625) — não especifica largura de banda mínima recomendada em termos de Gbit/s.

**Observação:** A rede Stellar foi projetada para operar com hardware relativamente modesto, de modo a permitir ampla participação.

### Especificações Detalhadas por Fonte

- **Stellar Developers (Oficial):** CPU: 8× Intel Xeon @3.4 GHz; RAM: 16 GB; Disk: 100 GB NVMe SSD
- **BlockMeadow:** Recomenda mínimo 1 TB de armazenamento para ledger de longo prazo
- **Stellar Stack Exchange:** Uso de SSD recomendado, largura de banda de rede não quantificada

## O que chamou atenção / Insights

- O mecanismo de consenso SCP permite latência muito baixa e custos operacionais menores se comparado a redes que exigem PoW ou ultra-alto throughput.
- A configuração de hardware pode ser menos extrema que redes como Solana — o que pode facilitar participação — porém se o nó for utilizado em ambientes de alta carga ou histórica, ainda pode demandar mais.
- Para projetos que visam "pagamentos/interoperabilidade/baixas taxas", a Stellar se encaixa muito bem.

## Por que escolher este nó

- Se o foco for remessas globais, integração de ativos digitais, interoperabilidade financeira, rapidez (≈ 5 s) e operação com custos moderados.
- Operar um nó Stellar é uma forma de contribuir para uma rede orientada a pagamentos, com hardware menos "extremo" comparado a ultra-throughput.
- Boa escolha para infraestrutura orientada a fintech/ativos/transferências em escala global.

## Fontes

- https://developers.stellar.org/docs/validators/admin-guide/prerequisites
- https://developers.stellar.org/docs/learn/fundamentals/stellar-consensus-protocol
- https://www.blockmeadow.com/how-to-deploy-a-stellar-node/
- https://stellar.stackexchange.com/questions/253/how-much-bandwidth-does-a-running-validator-use?utm_source=chatgpt.com