# 🤖 Sistema Multiagente para Auditoria de Qualidade de Software

## 📌 Sobre o Projeto

Este projeto implementa um sistema multiagente para realização de auditorias técnicas em sistemas de software utilizando Inteligência Artificial.

A solução foi desenvolvida com uma arquitetura baseada em especialistas, onde cada agente possui uma responsabilidade específica dentro do processo de análise. As avaliações individuais são posteriormente consolidadas por um agente orquestrador responsável por produzir uma recomendação final.

O objetivo é simular uma equipe multidisciplinar de engenharia de software composta por especialistas em arquitetura, requisitos, qualidade, testes, DevOps, segurança e métricas.

---

# 🎯 Objetivos

O sistema foi projetado para:

* Realizar auditorias técnicas automatizadas.
* Identificar riscos de arquitetura, segurança e operação.
* Detectar lacunas de requisitos.
* Avaliar qualidade do código e estratégia de testes.
* Priorizar problemas por impacto e criticidade.
* Consolidar recomendações de múltiplos especialistas.
* Demonstrar coordenação entre agentes de IA.

---

# 🏗️ Arquitetura do Sistema

```text
Usuário
   │
   ▼
QualityPlannerAI
   │
   ▼
┌─────────────────────────────┐
│ RequirementsReviewer        │
│ ArchitectureInspector       │
│ CodePracticesAdvisor        │
│ TestStrategist              │
│ DevOpsEngineer              │
│ SecurityAnalyst             │
│ MetricsReportingAgent       │
└─────────────────────────────┘
   │
   ▼
QualityOrchestratorAI
   │
   ▼
TERMINATE
```

---

# 👥 Agentes Especialistas

## QualityPlannerAI

Responsável por:

* Resumir o contexto recebido.
* Definir o plano de auditoria.
* Distribuir responsabilidades para os especialistas.
* Iniciar o processo de análise.

---

## RequirementsReviewer

Responsável por:

* Identificar ambiguidades.
* Detectar requisitos ausentes.
* Avaliar cenários não tratados.
* Identificar riscos funcionais.

---

## ArchitectureInspector

Responsável por:

* Avaliar arquitetura atual.
* Analisar modularidade e escalabilidade.
* Identificar riscos estruturais.
* Avaliar impactos futuros da arquitetura.

---

## CodePracticesAdvisor

Responsável por:

* Avaliar manutenção e legibilidade.
* Identificar dívida técnica.
* Avaliar padronização de código.
* Identificar riscos de evolução.

---

## TestStrategist

Responsável por:

* Avaliar cobertura de testes.
* Identificar riscos de regressão.
* Avaliar confiabilidade do sistema.
* Detectar cenários sem validação.

---

## DevOpsEngineer

Responsável por:

* Avaliar deploy e operação.
* Avaliar observabilidade.
* Avaliar automação e CI/CD.
* Identificar fragilidades operacionais.

---

## SecurityAnalyst

Responsável por:

* Identificar vulnerabilidades.
* Avaliar superfícies de ataque.
* Analisar impactos de segurança.
* Priorizar ações de mitigação.

---

## MetricsReportingAgent

Responsável por:

* Avaliar métricas existentes.
* Identificar métricas ausentes.
* Priorizar riscos.
* Avaliar impacto para o negócio.

---

## QualityOrchestratorAI

Responsável por:

* Consolidar análises dos especialistas.
* Identificar consensos.
* Identificar divergências técnicas.
* Priorizar ações recomendadas.
* Produzir a conclusão final da auditoria.

---

# 🔄 Fluxo de Execução

## Etapa 1

O usuário fornece um cenário contendo informações sobre o sistema a ser auditado.

---

## Etapa 2

O **QualityPlannerAI**:

* Resume o cenário.
* Organiza a auditoria.
* Aciona os especialistas.

---

## Etapa 3

Os especialistas realizam suas análises individuais:

1. RequirementsReviewer
2. ArchitectureInspector
3. CodePracticesAdvisor
4. TestStrategist
5. DevOpsEngineer
6. SecurityAnalyst
7. MetricsReportingAgent

---

## Etapa 4

O **QualityOrchestratorAI** consolida os resultados e produz:

* Principais riscos identificados.
* Pontos de consenso.
* Divergências técnicas.
* Priorização sugerida.
* Impacto para o negócio.
* Recomendação consolidada.

---

## Etapa 5

O sistema encerra a conversa utilizando:

```text
TERMINATE
```

---

# 📥 Cenário de Teste Utilizado

```text
Plataforma SaaS de gestão financeira para pequenas empresas.

Backend:
- Java 8 monolítico
- 900 mil linhas de código

Infraestrutura:
- PostgreSQL único
- Deploy manual
- Sem CI/CD
- Sem monitoramento centralizado

Qualidade:
- Cobertura de testes inferior a 10%
- Logs inconsistentes
- Documentação desatualizada

Segurança:
- APIs sem rate limiting
- Autenticação apenas por usuário e senha
- Ausência de MFA

Operação:
- 50 mil usuários ativos por mês
- Reclamações frequentes de lentidão em horários de pico

Restrições:
- Orçamento limitado
- Prazo de 6 meses para resultados
```

---

# 📚 Engenharia de Prompts

Durante o desenvolvimento foram realizados diversos refinamentos nos prompts para melhorar a coordenação entre os agentes.

Principais melhorias implementadas:

* Separação rígida de responsabilidades.
* Redução de respostas redundantes.
* Eliminação de análises fora da especialidade.
* Padronização da estrutura das respostas.
* Controle explícito de encerramento.
* Redução de alucinações e inferências indevidas.

---

# ⚠️ Principais Problemas Encontrados

## 1. Especialistas extrapolando responsabilidades

Exemplo:

* SecurityAnalyst analisando arquitetura.
* DevOpsEngineer sugerindo mudanças de negócio.
* ArchitectureInspector propondo soluções sem evidências suficientes.

### Solução

Refinamento dos system messages com limites claros de atuação.

---

## 2. Respostas redundantes

Diversos agentes repetiam exatamente os mesmos riscos.

### Solução

Definição explícita do escopo de cada especialista.

---

## 3. Falsos consensos

O QualityOrchestratorAI inicialmente tratava opiniões isoladas como consenso da equipe.

### Solução

Regras específicas para:

* Diferenciar consenso de opinião individual.
* Registrar divergências reais.
* Consolidar apenas informações presentes nas análises.

---

## 4. Conversas que não terminavam

O grupo continuava gerando mensagens após a conclusão.

### Solução

Implementação obrigatória da palavra:

```text
TERMINATE
```

como condição de encerramento da auditoria.

---

# 🧠 Curiosidades e Aprendizados

## Como a personalidade dos agentes influenciou as decisões?

Cada agente foi configurado para agir como um especialista de uma área específica.

Isso fez com que:

* O SecurityAnalyst priorizasse segurança.
* O DevOpsEngineer priorizasse observabilidade.
* O TestStrategist priorizasse testes e regressão.
* O ArchitectureInspector focasse sustentabilidade técnica.
* O MetricsReportingAgent priorizasse impacto e criticidade.

O resultado final foi uma análise mais rica e multidisciplinar.

---

## Houve conflitos entre agentes?

Sim.

### Exemplo

**ArchitectureInspector**

* Defendia modularização futura do sistema.

**DevOpsEngineer**

* Defendia observabilidade antes de qualquer refatoração.

### Resolução

O QualityOrchestratorAI consolidou a recomendação priorizando observabilidade antes de mudanças arquiteturais.

---

## Quais os riscos de prompts mal configurados?

| Agente                | Possível Problema                      |
| --------------------- | -------------------------------------- |
| QualityPlannerAI      | Distribuir tarefas incorretamente      |
| RequirementsReviewer  | Inventar requisitos inexistentes       |
| ArchitectureInspector | Recomendar microserviços sem evidência |
| CodePracticesAdvisor  | Assumir problemas não observados       |
| TestStrategist        | Definir metas irrealistas              |
| DevOpsEngineer        | Ignorar restrições operacionais        |
| SecurityAnalyst       | Inventar vulnerabilidades              |
| MetricsReportingAgent | Tratar estimativas como fatos          |
| QualityOrchestratorAI | Criar consensos inexistentes           |

---

## Melhorias Implementadas

* Refinamento iterativo dos prompts.
* Melhor separação de responsabilidades.
* Padronização da saída dos agentes.
* Controle de término da conversa.
* Redução de alucinações.
* Melhor consolidação de consensos e divergências.

---

# 📸 Evidências de Funcionamento

As evidências da execução do sistema encontram-se na pasta:

```text
/evidencias
```

Contendo:

* Planejamento da auditoria.
* Análises dos especialistas.
* Consolidação final.
* Encerramento da execução.

---

# 🚀 Tecnologias Utilizadas

* Python
* AutoGen AgentChat
* LLMs locais (Qwen / Gemma / Nemotron)
* GitHub
* Markdown

---

# 📄 Conclusão

O projeto demonstrou que sistemas multiagentes podem reproduzir, de forma organizada, um processo de auditoria técnica semelhante ao realizado por equipes multidisciplinares reais.

Além da auditoria em si, o principal aprendizado foi a importância da engenharia de prompts e da coordenação adequada entre agentes especializados, evitando sobreposição de responsabilidades, conclusões inconsistentes e decisões baseadas em informações não verificadas.
