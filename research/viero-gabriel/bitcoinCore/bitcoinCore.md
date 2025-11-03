# Bitcoin Core

## Overview

**Nome da Blockchain:** Bitcoin

**Descrição:** O Bitcoin Core baixa uma cópia completa da blockchain e seu tamanho varia desse número. Um dos pontos fortes do Bitcoin Core é que ele oferece altos níveis de segurança, privacidade e estabilidade.

**Propósito de uso:** Rodar um nó completo ajuda a reforçar a descentralização da rede, permite validação independente e contribui como peer para outros nós.

**Propósito do Bitcoin:** De acordo com o whitepaper (livro branco) do Bitcoin, seu propósito é ser um "Sistema de Dinheiro Eletrônico Ponto a Ponto" (A Peer-to-Peer Electronic Cash System). A ideia é permitir que pagamentos online sejam enviados diretamente de uma parte para outra, sem a necessidade de uma instituição financeira confiável como intermediária.

## Tipo de Consenso

**Mecanismo:** Proof-of-Work (PoW) — a rede Bitcoin exige que mineradores resolvam um puzzle (hashing) para encontrar blocos válidos. Além disso existem nós classificados como nós honestos:

Os mineradores resolvem problemas matemáticos complexos (baseados em hashcash) para encontrar um novo bloco válido. A recompensa por encontrar o bloco incentiva o comportamento honesto. Novas transações são transmitidas para todos os nós, que as incluem em um bloco. O consenso é alcançado quando um minerador encontra uma prova de trabalho para o bloco e a rede o aceita, construindo a próxima cadeia.

## Requisitos de Hardware / Mineração

**Mineradores ASIC:** Para competir na mineração de Bitcoin atualmente, é preciso usar um hardware especializado chamado Circuito Integrado de Aplicação Específica (ASIC), projetado exclusivamente para resolver o algoritmo criptográfico do Bitcoin. Dispositivos de mineração como computadores com GPUs (placas de vídeo) ou CPUs (processadores) são ineficientes e não conseguem competir com os ASICs.

## Requisitos de Hardware / Nó Completo

### Requisitos Mínimos

- **Sistema operacional:** Windows / Mac / Linux
- **CPU:** Basicamente qualquer coisa, desde um Raspberry Pi até um Core i7
- **RAM:** 2 GB+
- **Espaço em disco:** 7 GB+
- **Conexão de Internet:** 0,4 Mbps+ Banda Larga
- **Cota de download:** 20 GB+ por mês
- **Cota de upload:** 200 GB+ por mês

No entanto, para ter uma boa experiência, o mais importante é garantir que você use um SSD (2,5″ ou M.2) de 1 TB ou mais e também ter RAM suficiente, de preferência 8 GB ou mais.

**OBS:** Em relação ao espaço em disco, o valor de 7 GB é para nós que rodam em "Modo Podado" (também chamados de nós leves) e não é realmente a melhor experiência, pois você perde muitos dos benefícios de segurança e privacidade, mesmo que ajude a reduzir o armazenamento. A blockchain inteira tem atualmente pouco mais de 700 GB e cresce em torno de 50 GB por ano.

### Resumo Requisitos Mínimos

- **CPU:** Não especificado
- **RAM:** +2GB (Recomendado mínimo de 8GB pela comunidade)
- **STORAGE:** 1 TB SSD (Recomendado)
- **BANDWIDTH:** O ideal é ter uma conexão de internet sem limite de dados ou com um limite de upload muito alto, pois o consumo mensal pode ser substancial, especialmente durante a sincronização inicial.

## O que chamou atenção / Insights

Escrito originalmente em C++ com protocolo PoW o Bitcoin Core possui uma robustez enorme e entrega muito bem segurança e descentralização, porém seu tempo entre blocos chega a ser 10 minutos, o que atrasa o consenso da rede. A rede Bitcoin Core também possui "Nós Podados" que em português muito simples, eu chamaria de adaptações (gambiarras), para tentar encontrar uma maior eficiência energética e de desempenho.

### O que torna o Bitcoin seguro?

Sua verificação pela rede de nós honestos incentivados com recompensas por seu comportamento.

### O que torna o Bitcoin Core Lento?

Tempo de bloco, Processamento de transações, Uso de recursos são consequência de um protocolo que exige a resolução de um problema matemático que a cada ciclo torna-se mais complexo, também é resultado de uma rede com muitas transações escritas, ou seja, possui muitos dados a serem validados.

### O que torna o Bitcoin Core custoso energeticamente?

A necessidade de manter o protocolo seguro e descentralizado acaba afetando o desempenho e a eficiência energética. Quando convertido para trabalho de máquina o cálculo exigido para "mineração" de um novo bloco, exige dos recursos de hardware um desempenho que consome muita energia e é trabalhoso para ser executado. Além disso existe o consenso entre a rede que consome tempo, largura de banda para enviar e receber dados. O consenso e a segurança criada.

## Fontes

- https://bitcoin.org/
- https://academy.bit2me.com/pt/monedero-bitcoin-core/
- https://bitcoin.org/files/bitcoin-paper/bitcoin_pt_br.pdf
- https://corescientific.com/resources/blog/how-to-choose-the-best-equipment-for-maximum-efficiency/
- https://coinbureau.com/guides/how-to-run-a-bitcoin-node/