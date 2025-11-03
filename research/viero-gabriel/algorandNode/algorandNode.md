# Algorand Node

## Overview

**Nome da Blockchain:** Algorand

**Documentação oficial:** "Install a node - Algorand Developer Portal"

**Descrição:** A rede Algorand é pioneira no mecanismo de consenso Pure Proof-of-Stake (PPoS). Diferentemente de outras abordagens de proof-of-stake onde um usuário deve fazer stake (essencialmente, bloquear) seus tokens, no Algorand o usuário mantém o controle de seus Algo o tempo todo, já que os tokens permanecem na carteira do usuário enquanto garantem a segurança da rede como parte do consenso.

**Propósito de uso:** Um nó é uma instância de software que ajuda a validar transações e manter a blockchain Algorand. Os nós trabalham juntos para criar um ambiente descentralizado e seguro. Enquanto os relay nodes atuam como pontes de comunicação e exigem aprovação para operar, os consensus nodes (participation nodes) são abertos a qualquer pessoa e são responsáveis por participar do processo de consenso Pure Proof-of-Stake.

**Propósito da Algorand:** Algorand foi projetado para resolver o trilema da blockchain - alcançar escala, segurança e descentralização simultaneamente. Algorand é completamente aberto e sem permissão. Qualquer pessoa, em qualquer lugar do mundo, que possua Algos pode participar do consenso.

**Foco:** Velocidade, finalidade instantânea, baixo custo de transação, sustentabilidade energética, e descentralização verdadeira.

## Tipo de Consenso

**Mecanismo:** Pure Proof-of-Stake (PPoS) - utilizando criptografia sofisticada, incluindo Funções Aleatórias Verificáveis (VRF) e seleção criptográfica, o PPoS garante justiça, previne conluio e mantém alta segurança. A rede pode tolerar atores maliciosos e evitar forks e double-spending, desde que uma supermaioria do stake (mais de 2/3) seja mantida por participantes honestos.

Algorand alcança escalabilidade elegendo um novo block proposer e um novo comitê validador para cada bloco, em menos de 3 segundos. Tanto o block proposer quanto os membros do comitê são selecionados aleatoriamente de forma privada, probabilística e não-interativa, de todas as contas que se registraram para participar no consenso.

**Diferencial do PPoS:**
- O stake no Algorand não é bloqueado nem delegado, o que é um diferencial chave do PPoS em relação ao bonded proof of stake (BPoS) e delegated proof of stake (DPoS).
- Usuários são escolhidos para comitês baseados no número de algos em suas contas. Comitês são compostos por contas selecionadas pseudoaleatoriamente com poder de voto dependente de seu stake online. É como se cada token recebesse uma execução do VRF.
- Primeiro, democratiza o acesso à participação na rede exigindo apenas 1 ALGO como stake mínimo para servir como relay ou participation node.

## Requisitos de Hardware / Nó Participation

### Requisitos Mínimos para MainNet

Devido ao maior TPS na MainNet, para executar com sucesso um nó Algorand MainNet, o seguinte hardware é necessário: 8GB de RAM (Alguns operadores de nós usam com sucesso 4GB, mas requer gerenciamento adicional de memória e pode ainda ficar para trás durante atividade de rede extremamente alta), um SSD que não seja muito lento: HDD e cartões SD são muito lentos para um nó MainNet e provavelmente impedirão a sincronização do nó.

### Requisitos Recomendados para Participation Nodes

Especificação de sistema recomendada para participation nodes:
- **CPU:** 8 vCPU
- **RAM:** 16 GB
- **Armazenamento:** 100 GB NVMe SSD
- **Rede:** Conexão de internet de baixa latência (idealmente 1 Gbps), com largura de banda de pelo menos 100 Mbps

### Requisitos para diferentes tipos de uso

Para configuração básica/teste: CPU 4-8 cores, RAM 16 GB, SSD com pelo menos 250GB de espaço livre, conexão de internet estável com velocidade mínima de upload de 100 Mbps.

Para operação robusta: CPU 4+ cores (alguns operadores usam até 14 cores), RAM 8GB mínimo (48GB para desempenho otimizado), SSD NVMe para sincronizações rápidas de blocos.

### Requisitos de Armazenamento

Por padrão, nós non-relay armazenam apenas um número limitado de blocos (aproximadamente até os últimos 1000 blocos) localmente. Blocos mais antigos são descartados da cópia local do ledger. Isso reduz o requisito de espaço em disco do nó.

Para operação em modo arquival: Em setembro de 2023, um nó MainNet non-archival usa cerca de 20GB de armazenamento, enquanto um nó arquival requer aproximadamente 2TB de armazenamento.

**Nota:** A seleção criptográfica, no centro do consenso Algorand, é implementada através de VRFs de tal forma que o VRF é calculado uma vez, independentemente da quantidade de Algo em stake: a eleição do block proposer ou comitê é, portanto, escalável e leve, com requisitos mínimos de hardware comparado a outros mecanismos de consenso.

## Performance e Características Técnicas

### Throughput e Velocidade

No Algorand, blocos são produzidos a cada 2,85 segundos e podem conter até 25.000 transações, o que resulta em um throughput de mais de 10.000 transações por segundo (10.000 TPS).

Algorand não tem forking, então as transações são finais assim que são confirmadas em um bloco. Um throughput de 10.000 TPS então realmente significa 10.000 transações finalizadas por segundo.

Atualmente, Algorand está adicionando blocos à cadeia aproximadamente a cada 3 segundos, o que pode ser considerado como o tempo de finalidade para uma transação no Algorand.

### Taxas de Transação

A taxa mínima para uma transação é de apenas 1.000 microAlgos ou 0,001 Algos. O custo dessas taxas e saldos mínimos é muito baixo, frações de um centavo na maioria dos casos. Não há conceito de gas fees no Algorand.

### Segurança e Staking

Sem risco de slashing: Algos em stake não estão sujeitos a slashing (ou seja: confiscar os tokens de um staker como penalidade por comportamento que poderia causar dano à rede). Em vez disso, no Algorand, nós ineficazes são simplesmente removidos algoritmicamente do consenso, perdem recompensas e enfrentam custos menores para voltar à rede.

Sem período de bloqueio: No Algorand, validadores independentes mantêm controle de seus Algo o tempo todo. Tokens em stake permanecem em sua carteira enquanto protegem a rede como parte do consenso.

Segurança: No Algorand, as operações de consenso rodando no nó nunca expõem a chave da carteira. O consenso Algorand desacopla as chaves usadas para propor e votar em blocos das chaves principais de gasto que controlam os Algo.

### Requisitos para Recompensas

Qualquer pessoa com apenas 1 Algo pode participar do consenso e ajudar a manter a rede segura. No entanto, para ser elegível para recompensas de staking, uma conta deve comprometer um mínimo de 30.000 Algo ao consenso. Usuários com menos de 30.000 Algo podem fazer sua parte para proteger a rede e ser recompensados participando de staking pools ou utilizando outros serviços de delegação.

## O que chamou atenção / Insights

### Eficiência Energética

O mecanismo de consenso Pure Proof-of-Stake (PPoS) estilo loteria do Algorand é projetado para consumir menos energia do que mecanismos de consenso proof-of-stake (PoS). Através do uso de uma Função Aleatória Verificável (VRF) leve para selecionar um validador para cada bloco, o Algorand requer apenas que um bloco seja gerado para confirmar uma transação.

Esse método leve para alcançar consenso significa que os validadores do Algorand não precisam competir constantemente e, portanto, calcular para criação de blocos. Executar um nó Algorand é mais eficiente do que outras blockchains PoS, o que se traduz em menor consumo de energia em toda a rede.

De acordo com o Crypto Carbon Ratings Institute (CCRI), a pegada de CO2 anualizada da mainnet Algorand é de 265 tCO2, o que é aproximadamente 7x menor do que as emissões anualizadas associadas ao Ethereum PoS e 300.000x menor do que o Bitcoin.

### Descentralização e Acessibilidade

A rede Algorand permite que validadores participem com máquinas de baixo poder e não requer uma conexão de internet ultra-rápida. Hospedar apenas sua conta que tem menos de 0,005% do total de stake online pode ser feito com segurança em um PC doméstico. Os riscos de quedas de energia ou de rede são mitigados pela rede.

O protocolo detecta nós offline e remove seu stake, garantindo que o risco de paralisação não esteja crescendo.

### Segurança contra DDoS

Do ponto de vista da segurança, Algorand evita a fraqueza de validadores delegados, já que um grupo fixo de validadores, conhecido com antecedência, poderia facilmente se tornar alvo de ataques de negação de serviço distribuída (DDoS). O modelo "speak-once" do Algorand garante duas proteções em relação a ataques DDoS: primeiro, nenhum atacante malicioso pode saber qual nó deve ser alvo de um DDoS com antecedência, e segundo, uma vez que o nó tenha falado, seu papel no consenso já está cumprido, então não haveria ganho em atingi-lo com um DDoS.

### Escalabilidade

O PPoS permite que o Algorand processe um grande volume de transações sem comprometer velocidade ou segurança quando a rede está ocupada. Como o PPoS depende de aleatoriedade, elimina a necessidade de computação complexa e competição entre validadores, permitindo que a rede mantenha consistentemente o processamento rápido de transações sem uma sobrecarga computacional pesada.

### Desafios Operacionais

Executar um nó no Algorand requer algum conhecimento técnico, hardware dedicado e um compromisso de manter o uptime do nó e acompanhar as atualizações de software.

Para executar uma máquina na nuvem com os requisitos de sistema recomendados, o custo atual é de aproximadamente $15-20 por mês, dependendo do provedor.

## Por que escolher este nó

- **Alta Performance com Baixos Requisitos:** PPoS é escalável e leve, com requisitos mínimos de hardware comparado a outros mecanismos de consenso. Ideal para quem busca participar do consenso sem investimento massivo em infraestrutura.

- **Sustentabilidade:** Ao contrário dos sistemas PoW tradicionais que dependem de mineradores competindo para resolver quebra-cabeças criptográficos, o mecanismo PPoS do Algorand opera de forma diferente. Ele seleciona validadores aleatoriamente com base em seu stake na rede, reduzindo significativamente o gasto de energia.

- **Segurança sem Slashing:** Sem risco de slashing - Algos em stake não estão sujeitos a confisco como penalidade. Menor risco operacional comparado a outras redes PoS.

- **Finalidade Instantânea:** Todas as transações no Algorand são conduzidas com finalidade instantânea, e a rede pode processar milhares de transações por segundo, com alta velocidade de throughput que não vem à custa da descentralização da rede.

- **Controle Total dos Tokens:** O stake no Algorand não é bloqueado nem delegado. Você mantém controle total de seus Algos enquanto participa do consenso.

- **Descentralização Real:** Permitir que qualquer pessoa faça stake de Algo amplia o pool de validadores potenciais e contribui para o nível de descentralização. Com uma baixa barreira de entrada para fazer stake de Algo para apoiar a rede, combinado com um mecanismo de consenso PPoS que incorpora aleatoriedade, um sistema é criado onde o poder é distribuído.

- **Acessibilidade:** Hospedar apenas sua conta que tem menos de 0,005% do total de stake online pode ser feito com segurança em um PC doméstico. Ideal para participantes individuais.

- **Custos Operacionais Baixos:** Executar um nó no Algorand é extremamente barato. Você só precisa de um computador com pelo menos 8vCPU, 16GB de RAM, um SSD rápido, e uma conexão de internet de baixa latência com largura de banda de pelo menos 100 Mbps e idealmente 1 Gbps.

## Fontes

- https://developer.algorand.org/docs/run-a-node/setup/install/
- https://developer.algorand.org/docs/run-a-node/setup/types/
- https://developer.algorand.org/docs/get-details/algorand_consensus/
- https://developer.algorand.org/docs/get-started/basics/why_algorand/
- https://algorand.co/technology/pure-proof-of-stake
- https://algorand.co/technology/sustainability
- https://algorand.com/technology/pure-proof-of-stake
- https://algorand.com/resources/blog/proof-of-stake-vs-pure-proof-of-stake-consensus/
- https://algorandtechnologies.com/news/proof-of-stake-vs-pure-proof-of-stake-consensus/
- https://www.bitrue.com/blog/how-to-run-an-algo-node-algorand-guide
- https://algorand.co/blog/how-to-run-a-node-on-algorand-for-staking-rewards-a-step-by-step-guide
- https://www.gemx.app/running-an-algorand-validator-node-the-ultimate-setup-optimization-monitoring-guide/
- https://www.bydfi.com/en/questions/what-are-the-requirements-to-run-an-algorand-validator-node
- https://algorand.foundation/algorand-protocol/network/
- https://forum.algorand.co/t/hardware-requirements-for-nodes/8368
- https://support.perawallet.app/en/article/introduction-to-staking-neixva/
- https://medium.com/nodely/algorand-incentives-pre-guide-f242d1f681d4
- https://coinmarketcap.com/academy/glossary/pure-proof-of-stake-ppos
- https://cryptoresearch.report/crypto-research/what-is-pure-proof-of-stake/
- https://blockchainmagazine.com/technology/how-algorands-pure-proof-of-stake-consensus-mechanism-is-leading-the-green-blockchain-revolution/
- https://chainspect.app/chain/algorand
- https://community.algorand.org/blog/algorand-what-to-expect-in-2021/
- https://coincodex.com/article/14198/layer-1-performance-comparing-6-leading-blockchains/
- https://www.gemini.com/cryptopedia/what-is-algorand-cryptocurrency-blockchain
- https://www.algorand.com/resources/blog/role-of-transaction-finality-speed-in-nft-minting/
- https://www.algorand.foundation/news/jump-into-web3-with-algorand