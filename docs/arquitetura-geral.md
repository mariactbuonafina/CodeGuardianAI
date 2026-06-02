# Arquitetura Geral

## Objetivo

Desenvolver um sistema multiagente baseado em LLMs capaz de realizar auditorias técnicas em sistemas de software.

O sistema simula uma equipe multidisciplinar composta por especialistas em requisitos, arquitetura, qualidade de código, testes, DevOps, segurança e métricas.

## Arquitetura Utilizada

Foi adotada uma arquitetura centralizada baseada em coordenação sequencial.

Os agentes não conversam livremente entre si.

O fluxo segue:

QualityPlannerAI
↓
RequirementsReviewer
↓
ArchitectureInspector
↓
CodePracticesAdvisor
↓
TestStrategist
↓
DevOpsEngineer
↓
SecurityAnalyst
↓
MetricsReportingAgent
↓
QualityOrchestratorAI

## Tecnologias

- Python 3.12
- AutoGen AgentChat
- OpenRouter
- Qwen3-VL-4B
- GitHub

## Estratégia de Coordenação

Foi utilizada uma execução sequencial.

Cada agente:

- recebe o contexto acumulado;
- responde apenas dentro de sua especialidade;
- não assume responsabilidades de outros agentes;
- encaminha a execução para o próximo agente.

O orquestrador final consolida os resultados.