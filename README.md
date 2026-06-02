# Sistema Multiagente para Auditoria de Qualidade de Software

> Projeto desenvolvido para a Residência Tecnológica do Porto Digital, utilizando uma arquitetura multiagente baseada em LLMs especializados para execução colaborativa de auditorias técnicas em sistemas de software.

---

# 📋 Visão Geral

O objetivo deste projeto foi construir uma equipe virtual composta por agentes especializados capazes de realizar auditorias completas em sistemas de software, simulando a atuação de profissionais reais de uma equipe de engenharia.

O sistema utiliza um modelo de coordenação centralizada, onde um agente planejador distribui tarefas para especialistas, um orquestrador consolida os resultados e cada especialista atua dentro de seu domínio de conhecimento.

O cenário utilizado para validação foi uma plataforma SaaS de gestão financeira com diversos problemas arquiteturais, operacionais, de qualidade e segurança.

---

# 🎯 Objetivos do Projeto

O sistema foi desenvolvido para:

* Realizar auditorias técnicas automatizadas.
* Simular discussões entre especialistas.
* Identificar riscos e gargalos.
* Produzir recomendações consolidadas.
* Demonstrar coordenação entre múltiplos agentes baseados em LLM.

---

# 🏗️ Arquitetura do Sistema

```text
Usuário
   │
   ▼
QualityPlannerAI
   │
   ▼
RequirementsReviewer
   │
   ▼
ArchitectureInspector
   │
   ▼
CodePracticesAdvisor
   │
   ▼
TestStrategist
   │
   ▼
DevOpsEngineer
   │
   ▼
SecurityAnalyst
   │
   ▼
MetricsReportingAgent
   │
   ▼
QualityOrchestratorAI
   │
   ▼
Resposta Final Consolidada
```

---

# 🤖 Equipe de Agentes

## 1. QualityPlannerAI

### Papel

Planejar a auditoria.

### Responsabilidades

* Resumir contexto.
* Identificar especialistas necessários.
* Definir sequência de execução.
* Distribuir objetivos para cada agente.
* Não realizar análise técnica.

### Personalidade

Coordenador técnico neutro.

### Influência nas decisões

Garantiu que cada agente recebesse apenas responsabilidades compatíveis com sua especialidade, evitando sobreposição de análises.

---

## 2. RequirementsReviewer

### Papel

Analista de requisitos.

### Responsabilidades

* Encontrar ambiguidades.
* Identificar requisitos ausentes.
* Verificar critérios não especificados.
* Apontar riscos funcionais.

### Personalidade

Analítico e criterioso.

### Influência nas decisões

Direcionou a equipe para problemas causados pela ausência de SLAs, requisitos de segurança e métricas de desempenho.

---

## 3. ArchitectureInspector

### Papel

Arquiteto de Software.

### Responsabilidades

* Avaliar arquitetura.
* Identificar acoplamento excessivo.
* Avaliar modularidade.
* Analisar escalabilidade.
* Avaliar viabilidade de evolução arquitetural.

### Personalidade

Estratégico e estrutural.

### Influência nas decisões

Evitou recomendações precipitadas de migração para microserviços e sugeriu modularização incremental.

---

## 4. CodePracticesAdvisor

### Papel

Especialista em qualidade de código.

### Responsabilidades

* Avaliar legibilidade.
* Avaliar manutenibilidade.
* Avaliar dívida técnica.
* Avaliar padrões de desenvolvimento.

### Personalidade

Pragmático.

### Influência nas decisões

Reforçou a necessidade de observabilidade antes de grandes refatorações.

---

## 5. TestStrategist

### Papel

Especialista em testes.

### Responsabilidades

* Avaliar cobertura.
* Identificar riscos de regressão.
* Definir prioridades de automação.
* Avaliar qualidade das validações.

### Personalidade

Conservador e orientado à confiabilidade.

### Influência nas decisões

Destacou que qualquer melhoria sem testes aumentaria o risco operacional.

---

## 6. DevOpsEngineer

### Papel

Especialista DevOps e SRE.

### Responsabilidades

* Avaliar deploy.
* Avaliar observabilidade.
* Avaliar monitoramento.
* Avaliar automação.
* Avaliar infraestrutura.

### Personalidade

Pragmático e operacional.

### Influência nas decisões

Conduziu a priorização de CI/CD, monitoramento e observabilidade.

---

## 7. SecurityAnalyst

### Papel

Especialista em segurança.

### Responsabilidades

* Avaliar vulnerabilidades.
* Avaliar autenticação.
* Avaliar superfícies de ataque.
* Avaliar riscos operacionais.

### Personalidade

Preventivo e cauteloso.

### Influência nas decisões

Elevou MFA e rate limiting para o topo da lista de prioridades.

---

## 8. MetricsReportingAgent

### Papel

Especialista em métricas.

### Responsabilidades

* Priorizar riscos.
* Avaliar impacto.
* Avaliar probabilidade.
* Definir indicadores.

### Personalidade

Orientado a dados.

### Influência nas decisões

Transformou opiniões técnicas em riscos priorizados para tomada de decisão.

---

## 9. QualityOrchestratorAI

### Papel

Orquestrador final.

### Responsabilidades

* Consolidar resultados.
* Identificar consensos.
* Identificar divergências.
* Criar plano final.
* Encerrar execução.

### Personalidade

Executivo e imparcial.

### Influência nas decisões

Produziu a recomendação consolidada final da equipe.

---

# 🧠 Modelo de Coordenação

Foi adotado o padrão:

## Sequential Workflow

Cada agente executa apenas uma vez e passa o resultado ao próximo.

```text
Planner
 ↓
Reviewer
 ↓
Architect
 ↓
Code Advisor
 ↓
Test Strategist
 ↓
DevOps
 ↓
Security
 ↓
Metrics
 ↓
Orchestrator
```

---

# 🔧 Tecnologias Utilizadas

## Framework Multiagente

* AutoGen AgentChat

## Linguagem

* Python 3.12+

## Provedor de IA

* OpenRouter

## Modelo Utilizado

### Qwen3-VL-8B

Características:

* Baixo custo computacional.
* Boa capacidade de raciocínio.
* Boa aderência a instruções.
* Respostas consistentes para agentes especializados.

Configuração utilizada:

```json
{
  "provider": "OpenRouter",
  "model": "qwen/qwen3-vl-8b",
  "temperature": 0.2,
  "max_tokens": 1200
}
```

---

# ⚙️ Configuração dos Agentes

## Estratégias Utilizadas

### Baixa temperatura

```text
temperature = 0.2
```

Objetivo:

* Reduzir alucinações.
* Aumentar consistência.
* Melhorar previsibilidade.

---

### Especialização rígida

Cada agente recebeu:

* Papel definido.
* Escopo limitado.
* Formato de saída obrigatório.
* Proibição de assumir funções de outros agentes.

---

### Encerramento controlado

O último agente foi configurado para finalizar sempre com:

```text
TERMINATE
```

Isso evitou loops infinitos.

---

### Limite de turnos

```python
max_turns = 9
```

Definido para:

* Evitar conversas infinitas.
* Controlar consumo de tokens.
* Garantir execução determinística.

---

# 📝 Prompt Inicial Utilizado

```text
Estamos desenvolvendo uma plataforma SaaS para gestão financeira de pequenas empresas.

Contexto atual:
Backend em Java 8 monolítico.
900 mil linhas de código.
Banco PostgreSQL único.
Deploy manual.
Cobertura de testes inferior a 10%.
Sem CI/CD.
Sem monitoramento centralizado.
Logs inconsistentes.
APIs sem rate limiting.
Autenticação apenas por usuário e senha.
Sem MFA.
Documentação desatualizada.
50 mil usuários ativos por mês.
Reclamações frequentes de lentidão.

Equipe:
4 desenvolvedores backend.
1 frontend.
1 QA.
1 DevOps.

Objetivo:
Realizar uma auditoria completa do sistema.

O resultado final deve apresentar:

- Principais riscos identificados.
- Divergências técnicas encontradas.
- Prioridades de curto prazo.
- Impacto esperado para o negócio.
- Recomendação consolidada da equipe.
```

---

# 📖 Roteiro das Interações

## Etapa 1

QualityPlannerAI:

* Resume o cenário.
* Seleciona especialistas.
* Define ordem de execução.

---

## Etapa 2

RequirementsReviewer:

* Analisa requisitos.
* Identifica ambiguidades.
* Identifica lacunas.

---

## Etapa 3

ArchitectureInspector:

* Analisa arquitetura.
* Avalia escalabilidade.
* Avalia modularização.

---

## Etapa 4

CodePracticesAdvisor:

* Analisa qualidade do código.
* Analisa manutenção.
* Analisa dívida técnica.

---

## Etapa 5

TestStrategist:

* Analisa testes.
* Analisa riscos de regressão.

---

## Etapa 6

DevOpsEngineer:

* Analisa deploy.
* Analisa monitoramento.
* Analisa automação.

---

## Etapa 7

SecurityAnalyst:

* Analisa vulnerabilidades.
* Analisa segurança operacional.

---

## Etapa 8

MetricsReportingAgent:

* Prioriza riscos.
* Avalia impactos.

---

## Etapa 9

QualityOrchestratorAI:

* Consolida resultados.
* Identifica consensos.
* Identifica divergências.
* Produz relatório final.
* Encerra execução.

---

# 📸 Evidências de Funcionamento

As evidências devem incluir:

## Prints da execução

* Planejamento inicial.
* Respostas dos especialistas.
* Consolidação final.

## Logs

* Histórico completo da conversa.
* Ordem de execução dos agentes.
* Encerramento com `TERMINATE`.

## Métricas

* Quantidade de turnos.
* Consumo de tokens.
* Tempo de execução.

---

# 🎓 Aprendizados Obtidos

## Como a personalidade influenciou as decisões?

Cada personalidade direcionou o foco das análises:

| Agente                | Influência                  |
| --------------------- | --------------------------- |
| RequirementsReviewer  | Requisitos e critérios      |
| ArchitectureInspector | Sustentabilidade estrutural |
| CodePracticesAdvisor  | Manutenção e qualidade      |
| TestStrategist        | Confiabilidade              |
| DevOpsEngineer        | Operação                    |
| SecurityAnalyst       | Proteção                    |
| MetricsReportingAgent | Priorização                 |
| QualityOrchestratorAI | Síntese                     |

---

## Houve conflitos entre agentes?

Poucos conflitos explícitos ocorreram.

Os principais potenciais conflitos foram:

### Arquitetura vs DevOps

Arquitetura:

> Modularizar primeiro.

DevOps:

> Ganhar visibilidade primeiro.

### Segurança vs Negócio

Segurança:

> MFA imediatamente.

Negócio:

> Menor impacto possível ao usuário.

### Testes vs Prazo

QA:

> Aumentar cobertura rapidamente.

Negócio:

> Entregar resultados em 6 meses.

---

## Como o orquestrador resolveria conflitos?

Utilizando:

1. Impacto no negócio.
2. Risco associado.
3. Custo de implementação.
4. Prazo disponível.

Priorizando ações de maior retorno e menor custo.

---

# ⚠️ Riscos de Má Configuração dos Agentes

## QualityPlannerAI

Risco:

* Planejamento incorreto.
* Especialistas errados.
* Fluxo quebrado.

---

## RequirementsReviewer

Risco:

* Requisitos inexistentes.
* Priorização equivocada.

---

## ArchitectureInspector

Risco:

* Recomendações inviáveis.
* Refatorações desnecessárias.

---

## CodePracticesAdvisor

Risco:

* Dívida técnica ignorada.
* Foco excessivo em estilo.

---

## TestStrategist

Risco:

* Cobertura insuficiente.
* Falta de validação.

---

## DevOpsEngineer

Risco:

* Automações inadequadas.
* Operação instável.

---

## SecurityAnalyst

Risco:

* Vulnerabilidades ignoradas.
* Falsa sensação de segurança.

---

## MetricsReportingAgent

Risco:

* Priorização incorreta.
* Decisões sem dados.

---

## QualityOrchestratorAI

Risco:

* Consolidação incorreta.
* Conclusões inconsistentes.

---

# 🚀 Melhorias Realizadas Durante o Projeto

Durante os testes foram identificados problemas de:

* Repetição excessiva.
* Vazamento de responsabilidades.
* Loops de conversa.
* Alucinações.

Foram implementadas as seguintes melhorias:

### Especialização rígida

Cada agente passou a responder apenas dentro do seu domínio.

### Limite de turnos

```python
max_turns = 9
```

### Encerramento obrigatório

```text
TERMINATE
```

### Remoção de linguagem emocional

Agentes passaram a responder de forma técnica e objetiva.

### Consolidação baseada apenas em evidências

O orquestrador passou a utilizar somente informações citadas pelos especialistas.

---

# 📊 Resultado Final

A equipe multiagente conseguiu:

✅ Identificar riscos críticos de segurança

✅ Identificar gargalos operacionais

✅ Priorizar melhorias de curto prazo

✅ Produzir recomendações consolidadas

✅ Demonstrar coordenação entre agentes especializados

✅ Simular uma auditoria técnica multidisciplinar

---

# 👥 Equipe

Projeto desenvolvido para a Residência Tecnológica do Porto Digital utilizando AutoGen e LLMs especializados em um ambiente multiagente coordenado.
Colaboradores: Maria Clara Trevizane Buonafina , João Vitor Rodrigues da Silva, Maria Eduarda Trevizane Buonafina, Luís Fernando Andrade da Silva 

---

> **Conclusão:** O uso de agentes especializados demonstrou ser uma abordagem eficiente para decompor problemas complexos, distribuir responsabilidades e produzir análises técnicas mais estruturadas do que uma única chamada a um modelo geral.
