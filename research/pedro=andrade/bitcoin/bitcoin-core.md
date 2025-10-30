# Bitcoin Core — Guia de Pesquisa

## Visão Geral
Bitcoin Core é o cliente de referência da rede Bitcoin. Prioriza **segurança**, **descentralização** e **simplicidade**, com arquitetura UTXO e consenso **PoW (SHA-256)**.

## Por que está entre os melhores
- Histórico mais longo e robusto do setor.
- Alto grau de descentralização e facilidade de rodar.
- Código amplamente auditado, mudanças conservadoras.

## Foco
Segurança, imutabilidade, resistência a censura, operação acessível para qualquer pessoa.

## Critérios Técnicos
- **Performance (TPS):** ~3–7 TPS  
- **Latência:** ~10 min/bloco  
- **Throughput:** Baixo (por design, favorecendo segurança)  
- **Consenso:** PoW (SHA-256)  
- **Resiliência a ataques:** Muito alta (51% economicamente difícil)  
- **Descentralização:** Muito alta (muitos nós, distribuição global)  
- **Facilidade de rodar:** Alta

## Requisitos de Hardware (referência prática)
- CPU 4+ cores  
- RAM 4–8 GB  
- Armazenamento SSD ~700 GB+ (cresce com o tempo)  
- Banda: estável, sem exigências extremas  
- Energia: moderada (nó ≠ minerador)

## Custos Operacionais
- **Energia:** moderada  
- **Banda:** moderada  
- **Armazenamento:** crescente (histórico completo)

## Como conquistou essa posição
- Primeira blockchain funcional (2009), escolhas conservadoras e auditáveis.
- Comunidade global forte, documentação simples.
- Regras estáveis — previsibilidade para operadores.

## O que aprender para o nosso projeto
- **Simplicidade + segurança** primeiro.
- Incentivar requisitos acessíveis para aumentar a base de operadores.
- Documentação clara e estável para reduzir fricção.

## Ferramentas e DX
- Instalação via pacotes oficiais e compilação.
- RPC/CLI maduros, ampla compatibilidade com carteiras/infra.

## Métricas Rápidas
- TPS baixo por design; latência alta por bloco; confiabilidade máxima para “valor”.
