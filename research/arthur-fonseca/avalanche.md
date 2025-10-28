# Avalanche Node (rede Avalanche)

## Overview

- **Nome da Blockchain**: [Avalanche](avax.network)
- **Descrição**: O **AvalancheGo** é a implementação oficial de nó completo (“full node”) da rede Avalanche, escrita em Go e mantida pela Ava Labs. Ele participa diretamente do consenso, valida transações e blocos nas sub-redes (subnets), podendo atuar como validador da Primary Network (X-Chain, P-Chain e C-Chain) ou de subnets personalizadas. [docs.avax.network](docs.avax.network)
- **Propósito de uso**: Executar um nó AvalancheGo permite participar da rede Avalanche como validador ou nó de leitura, reforçando a descentralização, ajudando na propagação de blocos e validando transações de forma independente.

## Tipo de Consenso
- **Mecanismo**: Avalanche Consensus Protocol — uma família de protocolos baseados em repeated subsampled voting (amostragem repetida estocástica).
- **Descrição da Técnica**: O consenso Avalanche é uma variação de Proof-of-Stake (PoS) otimizada, que não depende de líderes nem requer mineração intensiva. Em vez disso, os nós consultam amostras aleatórias de outros validadores e repetem esse processo até que a rede alcance convergência probabilística extremamente alta sobre o estado correto. [Avalanche Whitepaper](https://avax.network/whitepapers/)
- **Observações**: O modelo combina segurança e alta escalabilidade — atingindo consenso em menos de 2 segundos em média, sem sacrificar a descentralização.

## Requisitos mínimos (hardware/nó completo)
Segundo documentação oficial: [Avalanche Node Requirement](https://docs.avax.network/nodes/run/node-manual-setup/)
- **CPU**: 8 núcleos (recomendado); mínimo 4 núcleos modernos (x86_64 ou ARM64)
- **RAM (memória)**: Mínimo 16 GB (recomendado)
- **Armazenamento (Storage)**:
    - Mínimo: 500 GB SSD NVMe (recomendado)
    - Blockchain completa das subnets principais pode ultrapassar 300 GB (dependendo da atividade na C-Chain e P-Chain).
- **Banda (Bandwidth)**: Download: ~150 GB/mês e Upload: ~200 GB/mês (pode variar conforme participação em subnets e volume de blocos)
- **Sistema Operacional**: Linux (Ubuntu 22.04+ recomendado), macOS, Windows (menos comum).
- **Dependências**: Go >= 1.20, systemd (para execução como serviço), portas abertas (9651 e 9650).

### Resumo requisitos mínimos
| Recursos  | Mínimo         | Recomendado                     |
|-----------|----------------|---------------------------------|
| CPU       | 4 núcleos      | 8 núcleos modernos              |
| RAM       | 8 GB           | 16 GB                           |
| Storage   | 300–500 GB SSD | 1 TB SSD NVMe                   |
| Bandwidth | 150–200 GB/mês | 300 GB/mês (upload + download)  | 
| OS        | Ubuntu 20.04+  | Ubuntu 22.04+                   |

## Métricas oficiais
- **TPS (Transactions Per Second)**: A rede Avalanche pode processar milhares de TPS na C-Chain e múltiplas subnets otimizadas.
- **Tempo de bloco / finalidade**: A rede busca finalização rápida, com blocos sendo aceitos em poucos segundos.
- **Finalidade da rede**: Plataforma de contratos inteligentes e sub redes interoperáveis com alta escalabilidade e baixo tempo de latência.
- **Número de nós**: A rede principal conta com centenas a milhares de nós ativos, entre validadores e não-validadores.  
  (Não há um número exato publicado formalmente para todos os nós completos públicos.)

## Fontes
- [Avalanche Docs – Nodes Overview](https://docs.avax.network/nodes/)
- [Avalanche Whitepaper](https://avax.network/whitepapers/)
- [AvalancheGo GitHub](https://github.com/ava-labs/avalanchego)
- [Run an Avalanche Node (Manual Setup)](https://docs.avax.network/nodes/run/node-manual-setup/)
- [Avalanche Metrics Dashboard](https://avascan.info/)
- [Subnets Documentation](https://docs.avax.network/subnets/)

## Tutorial: Como rodar um nó AvalancheGo em máquina pessoal
Recomenda-se usar Linux ou uma VM com recursos dedicados para evitar comprometer o ambiente principal.

### Pré-requisitos
1. Sistema operacional: Ubuntu 22.04 LTS (64-bit).
2. Recursos mínimos: 4 CPU, 8 GB RAM, SSD de 500 GB, conexão estável e pública (porta 9651 TCP aberta).
3. Permissões: acesso root/sudo.

### Passos
1. Instalar dependências
```bash
sudo apt update && sudo apt install -y curl unzip systemd
```

2. Baixar AvalancheGo (binário oficial)
```bash
curl -L https://github.com/ava-labs/avalanchego/releases/latest/download/avalanchego-linux-amd64.tar.gz -o avalanchego.tar.gz
tar -xvf avalanchego.tar.gz
sudo mv avalanchego /usr/local/bin/
```

3. Criar diretório de dados
```bash
sudo mkdir -p /var/lib/avalanchego
sudo useradd -r -s /bin/false avalanche
sudo chown -R avalanche:avalanche /var/lib/avalanchego
```

4. Criar serviço systemd

Arquivo ```/etc/systemd/system/avalanchego.service```:

```
[Unit]
Description=Avalanche Node
After=network.target

[Service]
User=avalanche
ExecStart=/usr/local/bin/avalanchego \
  --db-dir=/var/lib/avalanchego \
  --http-host=0.0.0.0
Restart=on-failure
LimitNOFILE=65536

[Install]
WantedBy=multi-user.target
```

Ative e inicie:

```bash
sudo systemctl daemon-reload
sudo systemctl enable avalanchego
sudo systemctl start avalanchego
```

5. Verificar sincronização
```bash
sudo journalctl -u avalanchego -f
```
ou via API:
```bash
curl -X POST --data '{"jsonrpc":"2.0","id":1,"method":"info.getNodeID"}' -H 'content-type:application/json;' 127.0.0.1:9650/ext/info
```

6. Opcional) Tornar-se validador
- Gere uma **staking key** e deposite **≥ 2000 AVAX** na P-Chain.
- Registre seu nó como validador via carteira Avalanche ([Avalanche Wallet](https://wallet.avax.network/)) ou CLI
- Configure seu **staking start time, end time e reward address**.

7. Manutenção:
- Atualize regularmente o AvalancheGo:
```bash
sudo systemctl stop avalanchego
curl -L https://github.com/ava-labs/avalanchego/releases/latest/download/avalanchego-linux-amd64.tar.gz -o avalanchego.tar.gz
tar -xvf avalanchego.tar.gz
sudo mv avalanchego /usr/local/bin/
sudo systemctl start avalanchego
```
- Monitore logs e uso de espaço.
- Execute 24/7 para estabilidade da rede e, se for validador, garantir recompensas.


### Observações / Boas práticas
- Use **SSD NVMe** — o desempenho de I/O é crítico para sincronização.
- Mantenha **porta 9651** aberta (para peers).
- Configure **firewall e autenticação RPC** se exposto à internet.
- Para uso corporativo, utilize **monitoramento com Prometheus** (exposto em ```/ext/metrics```).
- Se rodar em cloud (AWS, Azure, GCP), prefira instâncias otimizadas para disco e rede (ex: ```t3.large```, ```n2-standard-4```).
