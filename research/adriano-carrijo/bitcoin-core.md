# Bitcoin Core (rede Bitcoin)

## Overview
- **Nome da Blockchain**: Bitcoin - [bitcoin.org](https://bitcoin.org/en/bitcoin-core/)
- **Descrição**: O Bitcoin Core implementa um nó completo (“full node”) da rede Bitcoin — isto é, ele baixa e valida todos os blocos e transações desde o bloco genesis, conforme o modelo de “thick client” descrito no guia técnico. ([developer.bitcoin.org](https://developer.bitcoin.org/devguide/operating_modes.html))
- **Propósito de uso**: Rodar um nó completo ajuda a reforçar a descentralização da rede, permite validação independente e contribui como peer para outros nós.

## Tipo de Consenso
- **Mecanismo**: Proof-of-Work (PoW) — a rede Bitcoin exige que mineradores resolvam um puzzle (hashing) para encontrar blocos válidos. ([bitcoin.org](https://bitcoin.org/en/faq))
- **Observações**: O guia técnico destaca que esse modelo assegura que os nós completos podem validar todo o histórico da cadeia de blocos. ([developer.bitcoin.org](https://developer.bitcoin.org/devguide/operating_modes.html))

## Requisitos mínimos (hardware/nó completo)
Segundo documentação oficial e guias complementares:
- **CPU**: Não há especificação oficial detalhada de número de núcleos ou frequência mínima — apenas “desktop/laptop hardware” recente. ([bitcoin.org](https://bitcoin.org/en/full-node))
- **RAM (memória)**: Mínimo recomendado ~ 1 GB para instalação padrão. ([bitcoin.org](https://bitcoin.org/en/bitcoin-core/features/requirements))
- **Armazenamento (Storage)**:
    - A página de requisitos indica “Disk space 350 GB” como recomendação para instalação padrão. ([bitcoin.org](https://bitcoin.org/en/bitcoin-core/features/requirements))
    - Outra fonte (não oficial) indica que a blockchain já está em ~340 GB e recomendam ~1 TB livre para “future proofing”. (não oficial)
- **Banda (Bandwidth)**: Download ~500 MB/dia (~15 GB/mês) e Upload ~5 GB/dia (~150 GB/mês) para o uso recomendado da Bitcoin Core. ([bitcoin.org](https://bitcoin.org/en/bitcoin-core/features/requirements))
- **Sistema Operacional**: Windows 7/8.x/10, macOS, Linux. ([bitcoin.org](https://bitcoin.org/en/bitcoin-core/features/requirements))
- **Observação**: Há modos “pruned” (podados) que exigem menos armazenamento — mas então o nó não fornece todo histórico para outros nós. (discussão em fóruns)

### Resumo requisitos mínimos
- CPU: hardware moderno de desktop/laptop (nenhuma especificação oficial de núcleos/frequência dada)
- RAM: ~ 1 GB
- Storage: ~ 350 GB (mínimo recomendado para uso padrão)
- Bandwidth: ~ 500 MB/dia de download e ~ 5 GB/dia de upload (ou cerca de 15 GB/mês / 150 GB/mês)

## Métricas oficiais
- **TPS (Transactions Per Second)**: A rede Bitcoin normalmente processa cerca de 3 a 7 transações por segundo, de acordo com estimativas externas. Não encontrei um dado “oficial” da documentação Bitcoin.org que anuncie TPS máxima ou média com precisão.
- **Tempo de bloco**: A rede Bitcoin mira ~10 minutos entre blocos. ([bitcoin.org](https://bitcoin.org/en/faq))
- **Finalidade (purpose of the network)**: O objetivo principal da rede Bitcoin é permitir a transferência de valor ponto-a-ponto, sem intermediários, operando como uma reserva de valor e meio de pagamento global entre pares.
- **Número de nós**: Não foi localizado na documentação oficial um número atualizado preciso de quantos nós completos existem atualmente na rede Bitcoin.

## Fontes
- “Running A Full Node” – Bitcoin.org. ([bitcoin.org](https://bitcoin.org/en/full-node))
- Developer Guide / Reference – Bitcoin.org. ([developer.bitcoin.org](https://developer.bitcoin.org/devguide/))
- Bitcoin Whitepaper – Satoshi Nakamoto. ([bitcoin.org](https://bitcoin.org/bitcoin.pdf))
- Estimativas de TPS etc. – TokenView / CryptoHead (externo, não oficial).

## Tutorial: Como rodar um nó da Bitcoin Core em máquina pessoal
Recomenda-se usar Linux ou uma VM com recursos dedicados para evitar comprometer o ambiente principal.

### Pré-requisitos
1. Sistema operacional: Linux (por exemplo Ubuntu 22.04 LTS) ou macOS ou Windows (com hardware razoável).
2. Disponibilizar no mínimo ~1 GB de RAM livre, ~350 GB de armazenamento livre (SSD preferencial) e conexão de internet estável com boa banda de upload/download.
3. Download do Bitcoin Core (versão mais recente) a partir de site oficial: https://bitcoin.org/en/download ([bitcoin.org](https://bitcoin.org/en/download))
4. (Opcional) Se porta de entrada for aberta para que o nó aceite conexões de outros peers (aumenta contribuição para rede): abrir porta TCP 8333 no seu roteador/firewall. ([bitcoin.org](https://bitcoin.org/en/full-node))

### Passos
1. Baixe e instale o Bitcoin Core.
2. Inicie o cliente: se for modo GUI, execute `bitcoin-qt`; para modo servidor/daemon, execute `bitcoind`. ([developer.bitcoin.org](https://developer.bitcoin.org/examples/intro.html))
3. Na primeira execução, o software iniciará o download da blockchain inteira (o “initial block download” – IBD). Isso pode demorar horas ou dias, dependendo da velocidade de internet e do hardware. (fonte externa)
4. Certifique-se de que o software está configurado para armazenar os dados em um diretório apropriado com espaço suficiente.
5. Verifique se o software está aceitando conexões de entrada (se desejado) e se está sincronizando com a rede. Por exemplo, usando `bitcoin-cli getblockcount` para ver quantos blocos já foram baixados e comparando com altura da blockchain pública.
6. Opcional: configurar modo prune (podado) se quiser economizar espaço: definir no `bitcoin.conf` a opção `prune=<size-in-MB>` (por exemplo `prune=550`) para usar menos armazenamento, mas lembre que o nó então não proverá todo histórico para outros peers.
7. Manutenção: Deixe o nó rodando idealmente 24/7 para contribuir com a rede; monitore uso de banda e armazenamento; mantenha o software atualizado regularmente.

### Observações / Boas práticas
- Use SSD (unidade de estado sólido) para melhores tempos de leitura/escrita durante sincronização.
- Certifique-se de que o local de armazenamento tem desempenho de leitura/escrita rápido (>100 MB/s preferencial).
- Em ambientes domésticos, limitação de upload pode influenciar; se possível use plano de internet sem limites de upload ou monitore para não ultrapassar.
- Segurança: se usar a carteira interna da Bitcoin Core, trate as chaves privadas com cuidado; ou ainda, rode o nó apenas para validação/persistência e use carteira separada. ([bitcoin.org](https://bitcoin.org/en/full-node))

---