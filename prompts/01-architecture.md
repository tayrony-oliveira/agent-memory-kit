# Etapa 01 — Contratos e arquitetura

Implemente a estrutura do kit e documente contratos em docs/architecture.md. Estrutura alvo instalada:

```
AGENTS.md                 # bloco gerenciado opcional
.ai/skills/memory/SKILL.md
.ai/memory/
  INDEX.md
  CONTEXT.md
  knowledge/<topic>.md
  decisions/<id>.md
  tasks/<task-id>/STATE.md
  tasks/<task-id>/sessions/<session-id>.md
  meta.json
  .locks/
```

No repositório do kit mantenha `templates/`, `src/`, `tests/`, `docs/` separados da memória real. A localização da skill é genérica; adaptadores podem copiá-la para o local exigido pelo host.

Defina schema v1 com cabeçalho de metadados JSON em linha delimitada ou arquivo lateral, escolhendo uma única representação documentada e validada. Inclua id, tipo, workspace id, tarefa quando aplicável, branch/worktree, revision, timestamps UTC, status e referências de evidência (path relativo, commit quando existir). IDs seguros e estáveis; timestamps ISO 8601. Estado inclui objetivo, escopo, progresso confirmado, arquivos alterados, comandos/testes e resultados, problemas, hipóteses, próximos passos, dependências e referências. Decisões incluem alternativas, justificativa, status proposed/accepted/superseded e ligação ao substituto. Aprendizados duráveis em knowledge, com evidência e revisão; não transformar hipótese em fato. CONTEXT contém somente visão geral estável; INDEX é catálogo curto e reconstruível, não cópia dos documentos.

Defina isolamento: raiz canônica do workspace/worktree, id local, branch registrada, tarefa explícita (não escolher arbitrariamente quando houver múltiplas), sessão única. Ao detectar mudança de branch, commit ou arquivos, sinalize divergência e peça verificação; não tratar memória antiga como estado atual. Nunca copiar segredos ou transcrições completas. Documente política de retenção: arquivo de sessões opcional, consolidação manual e remoção somente autorizada.

Aceitação: templates válidos, schema versionado, exemplos fictícios, contratos claros e teste de isolamento entre duas raízes.
