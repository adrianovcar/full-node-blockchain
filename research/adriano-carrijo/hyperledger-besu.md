# Hyperledger Besu (como rede privada)

## Overview
- **Nome da Blockchain**: Hyperledger Besu
- **Cliente/Nó**: Hyperledger Besu ([https://besu.hyperledger.org](https://besu.hyperledger.org))  [besu.hyperledger.org](https://besu.hyperledger.org/ )
- **Descrição**: Besu é um cliente Ethereum open-source, implementado em Java sob licença Apache 2.0, que suporta tanto redes públicas como privadas. Na configuração de rede privada, ele permite criar um ambiente isolado (não conectado ao mainnet ou testnets públicos), com consenso modular, permissionamento e controle de participantes.  [besu.hyperledger.org](https://besu.hyperledger.org/private-networks )
- **Propósito de uso**: Utilizado para redes blockchain de nível empresarial (consortium/permissioned) onde é necessário controle de acesso, alta performance e compatibilidade com EVM (máquina virtual Ethereum).

## Tipo de Consenso
- Mecanismos suportados para rede privada: PoA (Proof-of-Authority) variantes como IBFT 2.0 e QBFT. ([referência](https://besu.hyperledger.org/private-networks))
- Observação: É possível também configurar-se com PoW (menos comum, “deprecated” para privado) segundo a documentação. ([referência](https://besu.hyperledger.org/private-networks))

## Requisitos mínimos (hardware/nó completo para rede privada)
*Atenção: A documentação oficial não especifica diratamente os valores abaixo, portanto, considera-se uma estimativa baseada em pesquisas.*
- **CPU**: Hardware moderno (mínimo 2-4 núcleos recomendados para desempenho razoável) — estimativa aproximada.
- **RAM (memória)**: Estimado ~4 GB para um nó leve em rede privada de teste. (Não há número oficial)
- **Armazenamento (Storage)**: Depende de configuração (sync completo, histórico, pruning). Em guia externo estima-se que para sincronização completa pode requerer 750 GB ou mais de disco. ([referência](https://www.quicknode.com/guides/infrastructure/node-setup/how-to-run-a-hyperledger-besu-node))
- **Banda (Bandwidth)**: Depende de volume de transações e peers da rede privada; não há dado oficial público. Recomenda-se conexão de rede estável, baixa latência entre validadores.
- **Sistema Operacional**: Qualquer ambiente suportado com Java 11+; Besu requer Java 11 ou superior. ([referência](https://www.quicknode.com/guides/infrastructure/node-setup/how-to-run-a-hyperledger-besu-node))

## Métricas oficiais
- **TPS (Transactions Per Second)**: Não encontrei um valor oficial na documentação para rede privada Besu. Em estudo de desempenho, observou-se que o parâmetro “block time” e “tamanho de bloco” são fatores críticos.  ([ResearchGate](https://www.researchgate.net/publication/363753578_Performance_Analysis_of_Hyperledger_Besu_in_Private_Blockchain))
- **Tempo de bloco**: Para IBFT 2.0, o campo `blockperiodseconds` define o tempo mínimo entre blocos. Por exemplo, a documentação mostra que com `blockperiodseconds = 5` s era observado ~5 segundos por bloco. ([referência](https://besu.hyperledger.org/private-networks/how-to/configure/consensus/ibft))
- **Finalidade (purpose of the network)**: O propósito da rede Besu privada é permitir a construção de uma blockchain permissionada, corporativa, compatível com o ecossistema Ethereum, garantindo controle sobre participantes, privacidade de transações, e alta performance para cenários empresariais.
- **Número de nós**: Não há número oficial fixo de nós para redes privadas Besu — varia de acordo com projeto. Exemplos de tutorial mostram 4 validadores para garantir tolerância a falhas BFT (≥ 4) para IBFT 2.0. ([referência](https://besu.hyperledger.org/private-networks/tutorials/ibft))

## Fontes
- Private networks – Besu documentation. [https://besu.hyperledger.org/private-networks](https://besu.hyperledger.org/private-networks)
- Create a private network using IBFT 2.0 – Besu tutorial. [https://besu.hyperledger.org/private-networks/tutorials/ibft](https://besu.hyperledger.org/private-networks/tutorials/ibft)
- QuickNode guide: How to run a Hyperledger Besu node. [https://www.quicknode.com/guides/infrastructure/node-setup/how-to-run-a-hyperledger-besu-node](https://www.quicknode.com/guides/infrastructure/node-setup/how-to-run-a-hyperledger-besu-node)

## Tutorial: Como rodar uma rede privada Besu na máquina pessoal
### Pré-requisitos
- Instale Java 11 ou superior.
- Baixe o binário do Besu ou use distribuição oficial.
- Prepare diretório para dados da rede (ex: `data/`).
- Configure um arquivo `genesis.json` para o seu consenso escolhido (ex: IBFT 2.0) com parâmetros como `blockperiodseconds`, `epochlength`, `requesttimeoutseconds`.  [besu.hyperledger.org](https://besu.hyperledger.org/private-networks/tutorials/ibft )
- (Opcional) Configure lista de validadores e permissionamento (node permissioning/account permissioning) se desejar uma rede corporativa.  [besu.hyperledger.org](https://besu.hyperledger.org/private-networks/concepts/permissioning )
- Crie diretórios para cada nó, por exemplo:
   ```bash
   mkdir –p PrivateNet/Node-1/data  
   mkdir –p PrivateNet/Node-2/data  