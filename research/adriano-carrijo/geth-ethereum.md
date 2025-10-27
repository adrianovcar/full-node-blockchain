# Geth (go-ethereum) – Rede Ethereum

## Overview
- **Nome da Blockchain**: Ethereum
- **Cliente/Nó**: Geth (go-ethereum) (https://geth.ethereum.org/docs)
- **Descrição**: Geth é uma implementação em Go do cliente Ethereum. Ele permite que um computador opere como um nó da rede Ethereum, processando transações, executando contratos inteligentes na EVM e sincronizando o estado da cadeia.
- **Propósito de uso**: Rodar um nó Geth permite interação direta e independente com a rede Ethereum, verificando dados da cadeia, atuando como peer full-node, além de permitir construir ou operar dApps, APIs e infraestruturas relacionadas ao ecossistema Ethereum.

## Tipo de Consenso
- **Mecanismo**: Proof-of-Stake (PoS) — desde o evento Ethereum Merge, a rede pública Ethereum opera com PoS.
- **Observações**: Embora Geth tenha compatibilidade histórica com PoW na era pré-Merge, em ambiente mainnet atual o modelo é PoS segundo a documentação oficial da Ethereum.

## Requisitos mínimos (hardware/nó completo)
- **CPU**:
    - Estimativa: Processador com 4+ núcleos (ou 2 núcleos com hyperthreading), preferencialmente com boa frequência (~3.5 GHz ou superior). [bacloud.com](https://www.bacloud.com/en/knowledgebase/203/ethereum-node-server-requirements-2025-updated.html?utm_source=chatgpt.com)
    - Fonte oficial da Geth não define número exato de núcleos/frequência. [go-ethereum](https://geth.ethereum.org/docs/getting-started/hardware-requirements?utm_source=chatgpt.com)
- **RAM (memória)**:
    - Recomenda-se pelo menos ~16 GB para nós completos. [go-ethereum](https://geth.ethereum.org/docs/getting-started/hardware-requirements?utm_source=chatgpt.com)
    - Estimativas mais robustas para 2025 sugerem 32 GB ou mais (em alguns casos 64 GB) dependendo de uso adicional. [Cherry Servers](https://www.cherryservers.com/blog/ethereum-node-requirements?utm_source=chatgpt.com)
- **Armazenamento (Storage)**:
    - Estimativa oficial (Geth docs): “> 650 GB de espaço em disco para um nó snap-sync completo” e “2 TB SSD recomendado” para full node + consenso. [go-ethereum](https://geth.ethereum.org/docs/getting-started/hardware-requirements?utm_source=chatgpt.com)
    - Estimativa de mercado para 2025: SSD NVMe entre 4-8 TB para full node, para archive node ~12 TB ou mais. [Cherry Servers](https://www.cherryservers.com/blog/ethereum-node-requirements?utm_source=chatgpt.com)
    - Observação: Estes valores dependem de modo de sincronização, estado do cliente, pruning, archive ou não.
- **Banda (Bandwidth)**:
    - Estimativa: conexão de internet estável com pelo menos ~25 Mb/s de download para funcionar razoavelmente. [go-ethereum](https://geth.ethereum.org/docs/getting-started/hardware-requirements?utm_source=chatgpt.com)
    - Estimativa mais exigente: 300-500 Mbps para nós com RPC ou serviços adicionais, ou até 1 Gbps para setups mais complexos. [Cherry Servers](https://www.cherryservers.com/blog/ethereum-node-requirements?utm_source=chatgpt.com)
- **Observação**: Como não há valores “mínimos oficiais” completamente definídos pela documentação da Geth para todos os parâmetros, essas estimativas devem ser apresentadas como **não-oficiais** e dependentes de configuração, cliente, caso de uso, sincronização e histórico da rede.

## Métricas não oficiais (estimativas)
- **TPS (Transactions Per Second)**:
    - Não foi encontrado um valor “oficial” documentado pela Geth ou pela rede Ethereum que fixe o TPS médio ou máximo.
- **Tempo de bloco**:
    - A documentação da Ethereum indica que blocos são gerados a cada “slot” de 12 segundos assumindo todos os validadores online. [quicknode.com](https://www.quicknode.com/guides/infrastructure/node-setup/ethereum-full-node-vs-archive-node?utm_source=chatgpt.com)
- **Número de nós**:
    - Não foi localizado um número oficial atualizado de nós completos executando Geth na rede pública.

## Fontes
- Geth Documentation – go-ethereum. https://geth.ethereum.org/docs 
- Getting Started with Geth. https://geth.ethereum.org/docs/getting-started
- “How to Install and Run a Geth Node” – QuickNode Guide. https://www.quicknode.com/guides/infrastructure/node-setup/how-to-install-and-run-a-geth-node

## Tutorial: Como rodar um nó Geth em máquina pessoal
### Pré-requisitos
1. Computador com sistema operacional Linux/macOS/Windows com boa conexão à Internet.
2. Instalar o binário ou construir o cliente Geth a partir da fonte.
3. Provisionar armazenamento em disco de grande capacidade (vários centenas de GB ou mais, dependendo se sincronização full/archive).
4. Garantir memória e CPU suficientes.
5. (Opcional) Configurar firewall/rotas para permitir peer-to-peer e RPC (se for exposto) — por padrão restrito ao local, se for uso próprio.

### Passos básicos
1. Baixe o cliente Geth, por exemplo via geth.ethereum.org ou por pacote. [go-ethereum](https://geth.ethereum.org/docs/getting-started?utm_source=chatgpt.com)
2. Inicialize diretório de dados, por exemplo:
   ```bash
   geth --datadir ~/.ethereum init <genesis.json>
3. Inicie sincronização da rede Ethereum (_ajuste parâmetros conforme documentação_):
   ```bash
    geth --syncmode “fast” --http --http.addr “0.0.0.0” --http.port 8545 --datadir ~/.ethereum
4. Acompanhe progresso via CLI ou logs. Uma vez sincronizado, o nó estará ativo como full node.
5. Para nós privados ou de teste, você pode customizar genesis.json, rede, peers permitidos, etc., conforme documentação de “private networks” ou “custom chain” em Geth.
6. Mantenha o nó atualizado com versões novas do Geth e monitore desempenho.

**Boas práticas**
- Use SSD para armazenamento de dados para melhor desempenho.
- Monitore logs de erros e conexão de peers.
- Restrinja endpoints RPC a endereços seguros se exposto à Internet.
- Em rede privada ou de teste, configure permissão de peers e segurança adicional.