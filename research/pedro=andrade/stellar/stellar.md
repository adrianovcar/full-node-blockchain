# Stellar Core

## Visão Geral
Stellar utiliza o **SCP (Stellar Consensus Protocol)** — um BFT federado — voltado a **pagamentos**, **remessas** e **interoperabilidade financeira** com **baixa taxa** e **baixa latência**.

## Por que está entre os melhores
- Finalidade rápida com custos ínfimos por transação.
- Requisitos de hardware modestos; fácil de operar.
- Foco em integrações financeiras reais (âncoras, gateways).

## Foco
Pagamentos globais, remessas, liquidação barata e rápida.

## Critérios Técnicos
- **Performance (TPS):** ~160–2.000+ (dependendo da configuração)  
- **Latência:** ~3–5 s  
- **Throughput:** Médio/alto para pagamentos  
- **Consenso:** SCP (quóruns federados)  
- **Resiliência a ataques:** Alta (quóruns e confiança federada)  
- **Descentralização:** Moderada (depende de escolha de quóruns)  
- **Facilidade de rodar:** Alta

## Requisitos de Hardware (referência prática)
- CPU 8 cores  
- RAM 16 GB  
- SSD 100–500 GB  
- Banda: estável, moderada

## Custos Operacionais
- **Energia:** baixa  
- **Banda:** moderada  
- **Armazenamento:** moderado (com “history archive” opcional)

## Como conquistou essa posição
- Protocolo federado eficiente e confiável para pagamentos.
- Estratégia de parcerias e documentação clara para operadores.
- Arquitetura de **History Archive** para consultas e auditoria.

## O que aprender para o nosso projeto
- **Consensos BFT/federados** são adequados quando latência/custo importam mais que throughput extremo.
- Oferecer **nós de histórico** melhora experiência de integrações e compliance.
- Manter hardware acessível amplia participação da rede.

## Ferramentas e DX
- Stellar Core + Horizon (API) para servir aplicações.
- Guias de operação, health-checks e observabilidade.

## Métricas Rápidas
- Excelente para casos de uso de pagamentos, remessas e inclusão financeira.
