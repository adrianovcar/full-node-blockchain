# Solana

## Overview
- **Nome da Blockchain**: Solana
- **Cliente/Nó**: Cliente oficial da Solana (ver documentação em https://solana.com/docs)
- **Descrição**: Solana é uma blockchain de alto desempenho projetada para suportar aplicações descentralizadas com alta taxa de transações e latência baixa. Utiliza o mecanismo de consenso baseado em Proof of History (PoH) combinado com Proof of Stake (PoS).
- **Propósito de uso**: Permitir execução de dApps, DeFi, NFTs e outros serviços de alto volume de transações com custos baixos e desempenho elevado.

## Tipo de Consenso
- **Mecanismo**: PoS + PoH — a PoH fornece uma “linha do tempo” criptográfica para ordenar eventos, facilitando alto desempenho, enquanto PoS é o mecanismo de validação/participação.
- **Observações**: A documentação oficial da Solana indica que vemos “Recommended hardware requirements and SOL required to operate a validator”. ([Solana Docs – Running a validator](https://solana.com/docs/running-validator))

## Requisitos mínimos (hardware/nó completo)
*Estes valores são estimativas e não necessariamente todos oficiais.*
- **CPU**:
    - Estimativa: ~12 núcleos / 24 threads com clock ~2.8 GHz ou superior para nós básicos. ([Helius blog – Solana nodes primer](https://www.helius.dev/blog/solana-nodes-a-primer-on-solana-rpcs-validators-and-rpc-providers/))
    - Estimativa mais robusta para produção: ~24-32 núcleos ou mais. ([Cherry Servers – How to become a Solana validator](https://www.cherryservers.com/blog/how-to-become-a-solana-validator))
- **RAM (memória)**:
    - Estimativa: ~128 GB ou mais para nós típicos. ([Helius blog](https://www.helius.dev/blog/solana-nodes-a-primer-on-solana-rpcs-validators-and-rpc-providers/))
    - Produção pesada: ~256 GB ou mais, até 512 GB+ dependendo da carga. ([BaCloud – Solana validator server requirements 2025 updated](https://www.bacloud.com/en/knowledgebase/199/solana-validator-server-requirements---2025-updated.html))
- **Armazenamento (Storage)**:
    - Estimativa: NVMe SSD rápido com múltiplos TB. Por exemplo: ledger + contas + sistema separadas. ([GetBlock guide – Solana full node requirements](https://getblock.io/blog/solana-full-node-complete-guide/))
    - Exemplos: 1-2 TB para ledger e contas em setups menores, muito mais em setups de indexação completa. ([GetBlock guide](https://getblock.io/blog/solana-full-node-complete-guide/))
- **Banda (Bandwidth)**:
    - Estimativa: Conexão de rede muito rápida — mínimo ~1 Gbps ou mais simétrico para operações decentes. ([BaCloud guide](https://www.bacloud.com/en/knowledgebase/199/solana-validator-server-requirements---2025-updated.html))
    - Produção: 10 Gbps ou mais recomendado para nós de validação de alto nível. ([Helius blog](https://www.helius.dev/blog/solana-nodes-a-primer-on-solana-rpcs-validators-and-rpc-providers/))
- **Observação**: A documentação oficial menciona “System Requirements / Recommended hardware requirements” para nós validadores. ([Solana Docs](https://solana.com/docs/running-validator)) Como os valores não são totalmente padronizados, devem ser usados como referência aproximada.

## Métricas (oficiais e não oficiais)
- **TPS (Transactions Per Second)**:
    - A rede Solana declara alta capacidade de throughput; por exemplo uma fonte indica “up to 50.000 TPS” no site oficial de validadores. ([Solana – Validators page](https://solana.com/validators))
    - Em guias de terceiros estimativas superiores para ambientes ideais (ex: dezenas de milhares de TPS).
- **Tempo de bloco**
    - A documentação não dá um “tempo de bloco padrão” claramente exposto; blocos ou “slots” na Solana são criados com latência muito baixa. Fontes externas indicam fração de segundo (~0,4 s) para alguns ambientes.
- **Número de nós**:
    - A página oficial de validadores informa “1000+ independent validators” ativamente suportando a rede. ([Solana – Validators page](https://solana.com/validators)) Mas não foi encontrada documentação que fixe um número exato de nós completos/validadores globalmente para todos os modos.

## Fontes
- Solana Documentation – Running a validator & recommended hardware. https://solana.com/docs
- Validators Page – Solana Foundation. https://solana.com/validators
- Helius blog – A primer on Solana RPCs, Validators, and RPC providers. https://www.helius.dev/blog/solana-nodes-a-primer-on-solana-rpcs-validators-and-rpc-providers/
- Cherry Servers – How to become a Solana validator: requirements and steps. https://www.cherryservers.com/blog/how-to-become-a-solana-validator
- BaCloud – Solana validator server requirements 2025 updated. https://www.bacloud.com/en/knowledgebase/199/solana-validator-server-requirements---2025-updated.html
- GetBlock – Solana full node: complete guide. https://getblock.io/blog/solana-full-node-complete-guide/

## Tutorial: Como rodar um nó Solana em máquina pessoal
### Pré-requisitos
1. Sistema operacional Linux (preferencialmente) com hardware dedicado — para produção ou teste dependendo da escala.
2. Baixar e instalar o cliente oficial da Solana conforme guia “Running a validator” na documentação oficial.
3. Providenciar hardware conforme estimativas acima (CPU multicore, RAM grande, armazenamento NVMe rápido, rede de alta velocidade).
4. Configurar rede, firewall, sincronização do ledger, participação no cluster ou mainnet-beta.

### Passos básicos
1. Configure o ambiente: instale dependências, prepare diretórios de dados (ledger, contas, etc).
2. Inicie o nó conforme documentação oficial, por exemplo usando o comando `solana-validator` (ou cliente atual), configurando `--ledger`, `--accounts`, definindo peers, bloco génesis, etc.
3. Aguarde sincronização do ledger e participe no cluster.
4. Verifique status do nó: conexões de peers, participação em consenso, desempenho, logs de erros.
5. Em ambiente de produção, habilite monitoramento, backups, tuning de sistema de arquivos, rede, índices para RPC se necessário.

### Observações / Boas práticas
- Rodar um nó Solana em produção (validador ou RPC de alto nível) exige hardware e rede robustos — a estimativa de custo operacional e investimento é considerável.
- Em ambiente pessoal ou de laboratório, pode-se usar configurações reduzidas para fins de teste ou DevNet.
- Consulte sempre a documentação oficial da Solana para versão do cliente, parâmetros de configuração, requisitos atualizados e alertas de segurança.