# Near Protocol

## Overview

- **Nome da Blockchain**: [NEAR Protocol](https://near.org)
- **Descrição**: O **NEARcore** (atualmente **nearcore** / **neard**) é a implementação oficial de nó completo (“full node”) da rede NEAR, desenvolvida pela **NEAR Foundation** e pela comunidade open-source.
Ele é responsável por validar blocos, participar do consenso Proof-of-Stake (PoS), armazenar o estado completo da blockchain e propagar transações na rede **Nightshade** — o mecanismo de sharding da NEAR. [NEAR Docs](https://docs.near.org)
- **Propósito de uso**: Rodar um nó NEAR permite atuar como **validador**, **nó RPC (leitura pública)** ou **nó de arquivo (archive node)**. Isso reforça a descentralização, oferece APIs para dApps e melhora a resiliência da rede.

## Tipo de Consenso
- **Mecanismo**: Nightshade + Proof-of-Stake (PoS)
- **Descrição da Técnica**: O NEAR utiliza um modelo de sharding dinâmico (Nightshade), onde cada shard processa parte das transações em paralelo, mas todos os validadores participam do consenso global.
  O consenso baseia-se em uma combinação de:
  - **Thresholded Proof-of-Stake**: seleção aleatória ponderada por stake.
  - **Doomslug**: protocolo de produção de blocos rápido que fornece **finalidade quase imediata (1 segundo)**.
  - **[Nightshade Sharding](https://near.org/papers/nightshade/)**: distribuição de carga entre shards, garantindo escalabilidade horizontal.
- **Observações**: O modelo NEAR oferece **baixa latência (~1s)** e **alta taxa de transações**, mantendo compatibilidade com EVM via Aurora e interoperabilidade via **Rainbow Bridge**.

## Requisitos mínimos (hardware/nó completo)
Segundo documentação oficial: [NEAR Node Validator Requirements](https://docs.near.org/develop/node/validator/hardware)
- **CPU**: 4 núcleos modernos (mínimo), recomendado 8 núcleos (x86_64).
- **RAM (memória)**: 8 GB (mínimo), recomendado 16 GB.
- **Armazenamento (Storage)**:
    - **Validator / RPC Node**: 500 GB SSD (mínimo)
    - **Archive Node** (guarda todo histórico): 2 TB SSD NVMe recomendado.
    - **Observação**: HDD não é suportado.
- **Banda (Bandwidth)**: conexão estável de pelo menos 100 Mbps.
- **Sistema Operacional**: Linux (Ubuntu 22.04 LTS recomendado).
- **Dependências**: 
    - ```curl```, ```git```, ```clang```, ```make```, ```pkg-config```, ```libssl-dev```, ```rustup``` (para compilar do código-fonte).
    - **Porta TCP 24567** aberta para peers.

### Resumo requisitos mínimos
| Recursos  | Mínimo        | Recomendado             |
|-----------|---------------|-------------------------|
| CPU       | 4 núcleos     | 8 núcleos modernos      |
| RAM       | 8 GB          | 16 GB                   |
| Storage   | 500 GB SSD    | 2 TB SSD NVMe (archive) |
| Bandwidth | 100 Mbps      | ≥ 200 Mbps (estável)    | 
| OS        | Ubuntu 20.04+ | Ubuntu 22.04+           |

## Métricas oficiais
- **TPS (Transactions Per Second)**: estimado em **~1000 TPS** (dependendo do número de shards ativos).
- **Tempo de bloco / finalidade**: ~1 segundo (com Doomslug), ~1 a 2 segundos (finalidade prática).
- **Finalidade da rede**: plataforma de **contratos inteligentes escalável e compatível com EVM**, voltada a aplicações Web3, jogos e finanças descentralizadas.
- **Número de nós**: centenas de validadores e milhares de nós RPC/arquivo na mainnet (número exato varia por época de epoch).

## Fontes
- [NEAR Documentation](https://docs.near.org)
- [Validator Setup Guide](https://docs.near.org/develop/node/validator/validator)
- [Nightshade Whitepaper](https://near.org/papers/nightshade/)
- [NEARcore GitHub](https://github.com/near/nearcore)
- [Explorer – Mainnet Metrics](https://explorer.near.org/)

## Tutorial: Como rodar um nó NEAR em máquina pessoal

### Pré-requisitos
1. Sistema operacional: Ubuntu 22.04 LTS (64-bit).
2. Recursos mínimos: 4 CPU, 8 GB RAM, SSD de 500 GB, conexão estável e pública.
3. Permissões: acesso root/sudo.

### Passos
1. Instalar dependências
```bash
sudo apt update
sudo apt install -y curl git build-essential clang pkg-config libssl-dev
```

2. Instalar Rust
```bash
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
source $HOME/.cargo/env
rustup target add wasm32-unknown-unknown
```

3. Clonar e compilar o NEARcore
```bash
git clone https://github.com/near/nearcore.git
cd nearcore
make release
```

4. Iniciar o nó
```bash
./target/release/neard init --chain-id mainnet
```

Isso cria o diretório padrão ```~/.near``` com os arquivos de configuração e chave.

5. Baixar o snapshot da blockchain
```bash
cd ~/.near
curl -O https://near-protocol-public.s3-accelerate.amazonaws.com/mainnet/genesis.json
curl -O https://near-protocol-public.s3-accelerate.amazonaws.com/mainnet/config.json
```

6. Executar o nó
```bash
./target/release/neard run
```

7. (Opcional) Configurar como validador
- Gere chave de validador:
```bash
near generate-key <nome_validador>
```
- Configure ```validator_key.json``` em ```~/.near```.
- Deposite ```≥ 67 000 NEAR``` em staking (valor variável conforme época).

Registre o nó via CLI ou [wallet.near.org](wallet.near.org)

8. Manutenção
- Mantenha o nó sincronizado e atualizado:
```bash
git pull origin master
make release
sudo systemctl restart neard
```
- Monitore logs:
```bash
journalctl -u neard -f
```
- Execute 24/7 para garantir participação no consenso e recompensas.

### Observações / Boas práticas
- Use **SSD NVMe** para desempenho ideal.
- Mantenha **porta 24567** aberta e configure **firewall**.
- Monitore métricas via Prometheus (```http://localhost:3030/metrics```).
- Se for validador, evite interrupções longas (penalidade de slashing).
- Utilize VPSs de baixa latência, como AWS, GCP ou DigitalOcean.
