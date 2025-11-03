# Geth (Ethereum)

## Overview

**Nome da Blockchain:** Geth (Ethereum)

**Descrição:** O Geth permite que qualquer pessoa execute um nó completo ou leve na rede Ethereum. Um nó completo armazena uma cópia integral da blockchain, validando transações e blocos, o que contribui para a segurança e descentralização da rede.

**Propósito de uso:** O propósito do Geth (Go Ethereum) é funcionar como um nó Ethereum completo, permitindo que usuários e desenvolvedores interajam com a rede blockchain do Ethereum. Ele é a implementação mais popular e serve como a base para executar funções essenciais como gerenciar contas, realizar transações, minerar blocos e executar contratos inteligentes.

**Propósito da Ethereum:** O propósito principal da Ethereum é ser uma plataforma global e descentralizada para executar e verificar o código de aplicativos sem a necessidade de intermediários.

## Tipo de Consenso

**Antes de setembro de 2022:** A rede Ethereum usava o protocolo de consenso Proof of Work (PoW), onde os mineradores competiam para resolver um quebra-cabeça matemático para validar blocos.

**Após a fusão (The Merge):** A Ethereum mudou para o protocolo de consenso Proof of Stake (PoS), que é mais eficiente em termos energéticos. O algoritmo de consenso específico usado é o Gasper, que combina a finalidade do Casper com o algoritmo de escolha de bifurcação LMD-GHOST.

## Requisitos de Hardware / Mineração

Para rodar o Geth Ethereum (nó completo), os requisitos mínimos de hardware são: processador com múltiplos núcleos, 8 GB de RAM (16 GB ou mais recomendado) e um disco SSD com pelo menos 1 TB de espaço, preferencialmente 2 TB. Uma conexão de internet estável e rápida é essencial. Para um desempenho ideal, um SSD rápido e mais RAM são recomendados.

## Requisitos de Hardware / Nó Completo

Em meados de 2025, o tamanho da blockchain ultrapassou 3 TB, portanto, a maioria dos operadores de nós usa SSDs NVMe de 4 a 8 TB, sendo que um disco de 6 a 8 TB oferece vários anos de margem antes de precisar de uma atualização.

### Especificações Recomendadas para Desempenho Confiável

**CPU:** Um processador moderno com pelo menos 8 núcleos / 16 threads, idealmente em torno de 3,5 GHz por núcleo, para lidar com a validação de blocos durante picos de carga.

**RAM:** Embora 32 GB sejam funcionais, 64 GB proporcionam um desempenho mais fluido e melhor suporte para serviços adicionais.

**Armazenamento:** Recomenda-se um SSD NVMe de 4 a 8 TB para maior estabilidade e garantia de uso futuro.

**Rede:** Mínimo de 300–500 Mbps, com 1 Gbps preferencial, especialmente para MEV-Boost, endpoints RPC ou sincronizações rápidas.

## O que chamou atenção / Insights

- Em comparação ao BTC os requisitos de hardware para ETH são muito mais exigentes. Provavelmente por conta da rede ser como um grande servidor onde é possível realizar diversas operações e não apenas transacionar moedas.
- O Ethereum foi projetado para ser um ecossistema mais flexível, suportando contratos inteligentes e aplicações descentralizadas (dApps), o que o torna mais complexo que o Bitcoin.

### O que torna o Ethereum seguro?

**Penalidades (Slashing):** Em vez de depender de uma grande quantidade de poder computacional para proteger a rede, o PoS depende de sanções econômicas. Se um validador agir de forma desonesta ou negligente — por exemplo, atestando transações conflitantes ou assinando blocos duplos — o protocolo pode aplicar um slashing, ou seja, remover uma parte de seu ETH apostado como penalidade. Esse mecanismo cria um forte impedimento financeiro contra ataques.

**Ataque de 51%:** No PoW, um ataque de 51% exigiria que um invasor controlasse a maior parte da taxa de hash (poder de mineração) da rede. No PoS, um ataque similar exigiria que o invasor controlasse mais de 51% do ETH apostado, o que é um investimento financeiro enorme e impraticável. Além disso, a comunidade poderia reagir forçando uma bifurcação (fork) da cadeia para anular o ataque, o que resultaria em uma perda financeira massiva para o invasor.

### O que torna o Geth Ethereum Lento e com complexidade maior?

Ethereum permite a criação de contratos inteligentes e quanto maior a complexidade de um SmartContract maior é o custo de processamento para a rede ou seja, esses contratos podem ser complexos e exigir recursos computacionais significativos para serem processados.

### O que torna o Geth Ethereum custoso energeticamente?

**PoS (Proof of Stake):** Com a mudança para a Prova de Participação, a mineração foi substituída pela validação. Os validadores precisam apenas "apostar" ETH para participar do processo de consenso. Isso eliminou a necessidade de hardware especializado para mineração e reduziu o consumo de energia da rede Ethereum em aproximadamente 99,9%.

## Fontes

- https://www.cherryservers.com/blog/ethereum-node-requirements
- https://ethdocker.com/Usage/Hardware/
- https://eth2book.info/latest/part2/consensus/overview/
- https://coinspaid.com/knowledge-base/ethereums-proof-of-stake-hummer-vs-cybertruck/
- https://ethereum.org/pt-br/whitepaper/
- https://istoedinheiro.com.br/bitcoin-e-ethereum-entenda-as-diferencas-entre-as-duas-maiores-criptomoedas
- https://cnnbrasil.com.br/economia/financas/ethereum-reduz-uso-de-energia-em-quase-100-com-atualizacao-de-software/