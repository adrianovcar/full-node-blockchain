# Stellar Core

## Overview
- **Nome da Blockchain**: Stellar
- **Cliente/Nó**: Stellar Core, em conjunto com outros componentes como Horizon, conforme a documentação oficial (https://developers.stellar.org/docs)
- **Descrição**: Stellar é uma blockchain pública destinada a facilitar transferências financeiras rápidas e de baixo custo entre pares ou entre instituições, com foco em inclusão financeira global.
- **Propósito de uso**: Permitir que tanto pessoas quanto instituições emitam, transacionem e movimentem ativos financeiros de forma global, integrada a sistemas financeiros existentes, com eficiência, baixos custos e latência reduzida.

## Tipo de Consenso
- **Mecanismo**: Federated Byzantine Agreement (FBA) / Stellar Consensus Protocol (SCP) — um modelo de consenso federado onde os nós escolhem “slices” de confiança e participam da validação com base nessa estrutura.
- **Observações**: Este modelo evita mineração ou staking tradicional, mas exige um desenho cuidadoso dos slices/quóruns para preservar segurança e descentralização.

## Requisitos mínimos (hardware/nó completo)
- **CPU**:
    - Estimativa oficial para “Core Validator Node”: 8 × Intel Xeon vCPUs @ 3.4 GHz. (https://developers.stellar.org/docs/validators/admin-guide/prerequisites)
    - Para nós menores ou em modo de teste, estimativas sugerem configurações mais leves.
- **RAM (memória)**:
    - Valor referido na documentação: 16 GB para Core Validator Node. (https://developers.stellar.org/docs/validators/admin-guide/prerequisites)
- **Armazenamento (Storage)**:
    - Documentação aponta: ~ 100 GB NVMe SSD para “30-day retention window” para Core Validator Node. (https://developers.stellar.org/docs/validators/admin-guide/prerequisites)
    - Para nós de histórico maior ou produção extensa, estimativas de mercado sugerem 1 TB ou mais.
- **Banda (Bandwidth)**:
    - A documentação não detalha largura de banda mínima exata para todos os tipos de nó. Deve-se garantir conexão de rede estável e adequada para manter o ledger sincronizado.
- **Observação**: Parte dos valores são oficiais; outros são estimativas e variam conforme o papel do nó (validator, watcher, archive) e o tamanho da rede.

## Métricas oficiais (com estimativas externas)
- **TPS (Transactions Per Second)**:
    - Estimativa da comunidade: ~ 130 a ~ 186 TPS (valores observados em 1 h pela plataforma Chainspect). (Fonte: Chainspect)
    - Importante: não há valor fixo “oficial” publicado no docs da Stellar com média ou máximo garantido.
- **Tempo de bloco / ledger**:
    - Estimativas diversas afirmam que o tempo de confirmação típico (“ledger close time”) da rede Stellar é de aproximadamente 3-5 segundos. (Fonte: Stellar StackExchange)
    - Outra fonte lista ~ 5,62 s como valor observado para “block time”.
- **Número de nós**:
    - Estimativa externa (Chainspect) aponta cerca de 82 validadores ativos registrados para Stellar.

## Fontes
- Prerequisites – Stellar Docs. https://developers.stellar.org/docs/validators/admin-guide/prerequisites
- Validators – Stellar Docs. https://developers.stellar.org/docs/validators
- Hardware estimates/market – Scortik blog. https://scortik.com/how-to-run-a-core-node-part-1-installation-and-configuration/
- Horizon prerequisites – Stellar Docs. https://developers.stellar.org/docs/data/apis/horizon/admin-guide/prerequisites

## Tutorial: Como rodar um nó Stellar em máquina pessoal
### Pré-requisitos
1. Computador com sistema operacional Linux/Unix moderno, 64-bit, com os requisitos aproximados listados acima.
2. Instalar o software **Stellar Core**, configurar PostgreSQL (ou similar) conforme guia de administração de nós na documentação oficial.
3. Provisionar hardware conforme estimativas (CPU, RAM, armazenamento) ou, para ambiente de teste, aceitar hardware menor.
4. Ter conectividade de rede estável com peers públicos da Stellar e, se aplicável, configurar histórico/arquivos de ledger (archive) se desejar nós com retenção completa.

### Passos básicos
1. Baixe e instale Stellar Core: consulte “Configuration & Admin Guide” nos docs oficiais.
2. Crie/edite o arquivo de configuração `stellar-core.cfg` com parâmetros como `NODE_IS_VALIDATOR`, `NODE_SEED`, `QUORUM_SET`, etc. (documentação disponível em Stellar).
3. Inicialize o nó e conecte-se à rede da Stellar; aguarde sincronização do ledger com peers.
4. Monitore logs, supervisione estatísticas de peers, saúde da base de dados e uso de recursos.
5. Para operação de produção: implemente backups, armazenamento de histórico, alta disponibilidade, redundância, e mantenha-se atualizado com versões e patches.

### Observações / Boas práticas
- Mesmo para nós pessoais ou de teste, manter uptime, segurança e monitoramento é importante para operação saudável.
- O papel do nó (validator, watcher, archive) determina quantos recursos serão exigidos; nós completos ou de produção requerem hardware mais robusto.
- Consulte sempre a documentação oficial da Stellar para a versão mais atual, guias operacionais e requisitos de segurança.