# global-azure-es-2026

Repositório da palestra **Build Multi-Agent Workflow Using Microsoft Foundry** apresentada no **Global Azure ES 2026**.

## Visão Geral

Este repositório demonstra como construir um **workflow multi-agente** no [Microsoft Foundry](https://ai.azure.com) para planejamento de viagens. O fluxo orquestra três agentes especializados que trabalham em conjunto para buscar passagens aéreas, hospedagem e gerar um plano de viagem completo para o usuário.

## Arquitetura

![Arquitetura Multi-Agent-Viagens](https://mermaid.ink/img/Zmxvd2NoYXJ0IFREClUoW1VzdWFyaW9dKSAtLT4gV0YKc3ViZ3JhcGggV0ZbV29ya2Zsb3cgTXVsdGktQWdlbnQtVmlhZ2Vuc10KZGlyZWN0aW9uIFRCCkExW0FnZW50ZSBQYXNzYWdlbnMgQWVyZWFzIC0gU2t5c2Nhbm5lcl0gJiBBMltBZ2VudGUgSG9zcGVkYWdlbSAtIEJvb2tpbmcuY29tXSAtLT4gQTNbQWdlbnRlIFBsYW5vIGRlIFZpYWdlbnNdCmVuZApXRiAtLT4gUXt7QXByb3ZhZG8_fX0KUSAtLT58U2ltfCBGSU0oW0NvbmNsdWlkb10pClEgLS0-fE5hb3wgV0Y)

> Fonte: [docs/diagrams/arquitetura.mmd](docs/diagrams/arquitetura.mmd)

## Estrutura do Repositório

![Estrutura do Repositório](https://mermaid.ink/img/Z3JhcGggTFIKUk9PVFtnbG9iYWwtYXp1cmUtZXMtMjAyNl0KUk9PVCAtLT4gQUdbYWdlbnRzL10KUk9PVCAtLT4gV0Zbd29ya2Zsb3dzL10KUk9PVCAtLT4gUFJbUHJlc2VudGF0aW9uL10KUk9PVCAtLT4gUk1bUkVBRE1FLm1kXQpBRyAtLT4gQUcxW2FnZW50ZS1wYXNzYWdlbnMtYWVyZWFzLnlhbWxdCkFHIC0tPiBBRzJbYWdlbnRlLWhvc3BlZGFnZW0ueWFtbF0KQUcgLS0-IEFHM1thZ2VudGUtcGxhbm8tdmlhZ2Vucy55YW1sXQpXRiAtLT4gV0YxW011bHRpLUFnZW50LVZpYWdlbnMueWFtbF0KUFIgLS0-IFBSMVtCdWlsZCBNdWx0aS1BZ2VudCBXb3JrZmxvdyBVc2luZyBNaWNyb3NvZnQgRm91bmRyeS5wZGZd)

> Fonte: [docs/diagrams/estrutura.mmd](docs/diagrams/estrutura.mmd)

## Agentes

### `agente-passagens-aereas`
Extrai informações de voo do pedido do usuário e simula uma busca no [Skyscanner](https://www.skyscanner.com.br/). Retorna origem, destino, datas, preço estimado, companhia aérea e duração.

### `agente-hospedagem`
Extrai informações de hospedagem do pedido do usuário e simula uma busca no [Booking.com](https://www.booking.com/). Retorna nome do hotel, tipo, preço estimado, avaliação e localização.

### `agente-plano-de-viagens`
Recebe os resultados dos dois agentes anteriores e gera um plano de viagem completo em formato Markdown, apresentável no chat do usuário.

## Workflow

O workflow `Multi-Agent-Viagens` orquestra os três agentes com o seguinte fluxo:

1. Captura a mensagem do usuário
2. Invoca **paralelamente** os agentes de passagens aéreas e hospedagem
3. Consolida os resultados e invoca o agente de plano de viagens
4. Apresenta o plano ao usuário para aprovação
5. Se **não aprovado**, retorna ao passo 2 com o feedback para refinamento

## Pré-requisitos

- Conta no [Microsoft Azure](https://azure.microsoft.com/)
- Acesso ao [Microsoft Foundry (Azure AI Foundry)](https://ai.azure.com/)
- Projeto criado no Azure AI Foundry com os agentes e o workflow implantados

## Como Usar

1. Importe os arquivos da pasta `agents/` no seu projeto do Azure AI Foundry
2. Importe o arquivo `workflows/Multi-Agent-Viagens.yaml`
3. Inicie uma conversa com o workflow e descreva sua viagem desejada

**Exemplo de entrada:**
```
Quero viajar de São Paulo para Lisboa, saindo dia 10/06/2026 e voltando dia 20/06/2026.
```

## Apresentação

O slide deck da palestra está disponível em [`Presentation/Build Multi-Agent Workflow Using Microsoft Foundry.pdf`](Presentation/Build%20Multi-Agent%20Workflow%20Using%20Microsoft%20Foundry.pdf).

## Recursos

- [Azure AI Foundry – Documentação](https://learn.microsoft.com/azure/ai-foundry/)
- [Multi-Agent Workflows no Foundry](https://learn.microsoft.com/azure/ai-foundry/agents/)

