# Rede BNB Chain

## Overview
- **Nome da Blockchain**: BNB Smart Chain (BSC)
- **Cliente/Nó**: Cliente de referência baseado em geth (fork do Go-Ethereum) e outros componentes do ecossistema BNB Chain. (https://docs.bnbchain.org/bnb-smart-chain/developers/node_operators/full_node/)
- **Descrição**: BNB Smart Chain é uma blockchain compatível com EVM, projetada para permitir contratos inteligentes, DeFi e aplicações em escala, com taxas relativamente baixas e tempos de bloco rápidos.
- **Propósito de uso**: Oferecer uma camada de execução para aplicações descentralizadas (dApps), com compatibilidade EVM, ampla liquidez e integração, visando uso massificado, especialmente em contexto de ecossistema ligado à Binance.

## Tipo de Consenso
- **Mecanismo**: Proof of Staked Authority (PoSA) — uma combinação de validação por stake/autoridade, onde um conjunto de validadores (por exemplo 45 ativos) participam na produção de blocos. (https://docs.bnbchain.org/bnb-smart-chain/validator/overview/)
- **Observações**: Como mecanismo híbrido, privilegia performance e EVM-compatibilidade. Há trade-offs em descentralização em comparação com redes puras de PoS ou PoW.

## Requisitos mínimos (hardware/nó completo)
*Valores retirados da documentação oficial ou fontes confiáveis externas.*
- **CPU**: Mínimo **16 núcleos físicos** para nós “Full Node” de produção. (https://docs.bnbchain.org/bnb-smart-chain/developers/node_operators/node_best_practices/)
- **RAM (memória)**: Para full node, “at least 64 GB RAM” é recomendado. (https://docs.bnbchain.org/bnb-smart-chain/developers/node_operators/node_best_practices/)
- **Armazenamento (Storage)**: SSD de pelo menos **3 TB** para full node padrão. Para modo “Archive Node”, SSD de 10 TB ou mais são sugeridos. (https://docs.bnbchain.org/bnb-smart-chain/developers/node_operators/node_best_practices/)
- **Banda (Bandwidth)**: Conexão de internet estável com pelo menos **5 MB/s** de download mínimo para operação aceitável. (https://docs.bnbchain.org/bnb-smart-chain/developers/node_operators/node_best_practices/)
- **Observação**: Estas especificações destinam-se a nós completos de produção. Nós menores ou de teste podem operar com hardware inferior, mas desempenho, sincronização e latência serão afetados.

## Métricas
- **TPS (Transactions Per Second)**:
    - Estimativa externa para BNB Chain mostra ~ 268 transações por segundo em média. (Fonte: Chainspect) (https://chainspect.app/chain/bnb-chain)
    - Também é reportado um “Max TPS (100 blocks)” de ~2.545 tps. (Fonte: Chainspect)
- **Tempo de bloco**:
    - Estimativa real-mundo para BNB Chain: ~ 0,75 segundos entre blocos. (Fonte: YCharts) (https://ycharts.com/indicators/binance_smart_chain_average_block_time)
- **Número de nós**:
    - Segundo documentação de validadores: “45 active validators” são mencionados para o consenso. (https://docs.bnbchain.org/bnb-smart-chain/validator/overview/)
    - Contudo, o número total de nós completos (full nodes, archive nodes) conectados à rede não está claramente especificado.

## Fontes
- Documentação oficial – Full Node e práticas de nós. https://docs.bnbchain.org/bnb-smart-chain/developers/node_operators/full_node/
- Documentação oficial – Node Best Practices. https://docs.bnbchain.org/bnb-smart-chain/developers/node_operators/node_best_practices/
- Documentação oficial – Validator Overview. https://docs.bnbchain.org/bnb-smart-chain/validator/overview/
- Métricas externas – Chainspect (BNB Chain). https://chainspect.app/chain/bnb-chain
- Métricas externas – YCharts (average block time). https://ycharts.com/indicators/binance_smart_chain_average_block_time

## Tutorial: Como rodar um nó BNB Smart Chain em máquina pessoal
### Pré-requisitos
1. Sistema operacional Linux, macOS ou Windows suportado; hardware com as especificações acima ou adequadas ao seu uso (teste vs produção).
2. Baixar o binário `geth` para BNB Smart Chain a partir do repositório oficial. (https://docs.bnbchain.org/bnb-smart-chain/developers/node_operators/full_node/)
3. Configurar diretório de dados (`--datadir`), configurar `config.toml` ou usar snapshot para sincronização inicial, conforme guia oficial.
4. Provisionar armazenamento, memória, CPU e rede conforme estimativas para evitar gargalos.

### Passos básicos
1. Baixe o binário `geth`:
    ```bash
    wget $(curl -s https://api.github.com/repos/bnb-chain/bsc/releases/latest | grep browser_ | grep geth_linux | cut -d\" -f4)
    mv geth_linux geth
    chmod +x geth
    ```  
   (https://docs.bnbchain.org/bnb-smart-chain/developers/node_operators/full_node/)
2. Baixe o `genesis.json` e `config.toml` para mainnet:
    ```bash
    wget $(curl -s https://api.github.com/repos/bnb-chain/bsc/releases/latest | grep browser_ | grep mainnet | cut -d\" -f4)
    unzip mainnet.zip
    ```  
   (https://docs.bnbchain.org/bnb-smart-chain/developers/node_operators/full_node/)
3. Inicie o nó com os parâmetros adequados:
    ```bash
    ./geth --config ./config.toml --datadir ./node_data --syncmode full --http --http.addr 0.0.0.0 --http.port 8545
    ```  
   (Baseado nas instruções da documentação)
4. Aguarde sincronização inicial (“initial block download” ou uso de snapshot recomendado), verifique logs, conectividade peers, status de sincronização.
5. Para produção, monitore métricas como “Block Import Time Alert” (ex: > 3 s) ou “RPC latency” (>100 ms) conforme guia de práticas. (https://docs.bnbchain.org/bnb-smart-chain/developers/node_operators/node_best_practices/)

### Observações / Boas práticas
- Use SSD ou NVMe de boa performance, com latência de leitura < 1 ms se possível. (https://docs.bnbchain.org/bnb-smart-chain/developers/node_operators/node_maintenance/)
- Realize backups regulares do diretório de dados e chaves, especialmente se for nó de validação.
- Mantenha software atualizado com versões de `bsc`/`geth` compatíveis com BNB Chain.
- Em uso de produção, considere uso de “sentry nodes” (nós de frente) e separação de função entre full node + validator node.
- Se for configurar modo “Archive Node”, esteja preparado para armazenamento muito grande (por exemplo 4 TB+). (https://docs.bnbchain.org/bnb-smart-chain/developers/node_operators/archive_node/)

---