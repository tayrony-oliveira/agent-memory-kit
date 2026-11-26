# Agent Memory Kit

Memória persistente, local e seletiva para agentes de desenvolvimento de software.

O objetivo é permitir que novas sessões de IA retomem o trabalho com contexto suficiente, sem precisar carregar todo o histórico de conversas. O conhecimento pertence ao workspace, não à sessão ou ao modelo.

> **Status:** especificação técnica pronta para implementação. Este repositório contém os prompts de desenvolvimento, não uma CLI ou Skill já executável.

## Getting Started

### 1. Clonar o repositório

```bash
git clone https://github.com/tayrony-oliveira/agent-memory-kit.git
cd agent-memory-kit
```

### 2. Iniciar o desenvolvimento

Abra o diretório clonado em um agente de programação com acesso ao filesystem e ao terminal. Envie o seguinte prompt:

```text
Leia integralmente o README.md e todos os arquivos do diretório prompts/.
Use prompts/00-master.md como especificação principal.
Execute as etapas 01 a 06 sequencialmente, implementando os requisitos,
executando os testes e registrando evidências em IMPLEMENTATION.md.
Não entregue apenas pseudocódigo. Preserve alterações existentes e
documente bloqueios, limitações e pendências reais.
```

### 3. Acompanhar a implementação

| Etapa | Especificação |
| --- | --- |
| 00 | [Prompt mestre](prompts/00-master.md) |
| 01 | [Arquitetura e contratos](prompts/01-architecture.md) |
| 02 | [Persistência e CLI](prompts/02-storage-cli.md) |
| 03 | [Recuperação seletiva](prompts/03-retrieval.md) |
| 04 | [Memory Skill](prompts/04-skill.md) |
| 05 | [Instalação e integrações](prompts/05-installation.md) |
| 06 | [Testes e release](prompts/06-testing-release.md) |

O agente deverá criar e atualizar `IMPLEMENTATION.md` com o progresso, decisões, critérios de aceitação e resultados reais dos testes.

## Arquitetura proposta

```text
AI Agent
    |
Memory Skill
    |
Memory CLI (Python 3.11+, standard library)
    |
Persistent Workspace Storage
    |-- Project Context
    |-- Decisions and Knowledge
    |-- Task State
    +-- Session Checkpoints
```

A Skill orienta o comportamento do agente. A CLI valida e persiste dados de forma determinística. O armazenamento local mantém o conhecimento entre sessões.

O MVP não depende de APIs externas, embeddings, RAG, MCP ou banco de dados. A recuperação utiliza busca lexical e um orçamento configurável de contexto.

## Instalação e uso da Memory Skill

Após a implementação e validação das etapas, siga as instruções de instalação que o agente deverá documentar conforme o [prompt 05](prompts/05-installation.md). A instalação deverá preservar configurações existentes e manter a memória real fora do Git por padrão.

Fluxo de uso previsto:

| Operação | Finalidade |
| --- | --- |
| `memory init` | Inicializar a sessão e recuperar o estado da tarefa. |
| `memory recall <tema>` | Consultar conhecimento relevante sob demanda. |
| `memory checkpoint` | Persistir progresso, decisões, testes e próximo passo. |
| `memory consolidate` | Consolidar conhecimento e revisar informações obsoletas. |

Essas operações são intenções interpretadas pela Skill, não comandos nativos universais. A automação depende das capacidades verificadas do agente utilizado.

Antes de trocar de aba, execute um checkpoint. Na nova sessão, inicialize a memória no mesmo workspace e selecione a tarefa correspondente.

## Roadmap

- [x] Arquitetura e especificação técnica.
- [x] Prompts de desenvolvimento e critérios de aceitação.
- [ ] Implementação da persistência e CLI.
- [ ] Recuperação seletiva de contexto.
- [ ] Implementação da Memory Skill.
- [ ] Instalador e integrações.
- [ ] Testes automatizados e documentação de uso.
- [ ] Release inicial v0.1.0.

## Segurança e privacidade

Este repositório público destina-se exclusivamente ao framework genérico. Não publique memória real de trabalho, código corporativo, dados pessoais ou credenciais aqui. Utilize somente workspaces e ferramentas autorizados pela organização.

O código-fonte é a referência para fatos verificáveis; memórias podem ficar desatualizadas e devem ser conferidas. A compatibilidade com agentes e a economia efetiva de tokens deverão ser avaliadas após a implementação.

---

**Stateless Agents. Stateful Workspace. Persistent Knowledge.**
