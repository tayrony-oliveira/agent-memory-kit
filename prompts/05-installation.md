# Etapa 05 — Instalação e integrações

Implemente instalação local idempotente com `--workspace`, `--dry-run`, opção de não modificar AGENTS.md, e relatório de arquivos criados/alterados. Não sobrescreva skill customizada sem autorização; sinalize conflitos. Preserve newline/encoding e conteúdo existente. Use caminho explícito do kit, sem baixar scripts ou executar rede. Forneça uninstall apenas de arquivos gerenciados inalterados, com preview e autorização; nunca apagar memória real automaticamente.

Adicione regra `.ai/memory/` a mecanismo de ignore local apropriado por padrão (ex.: .git/info/exclude quando disponível, considerando worktrees); verifique com git check-ignore e alerte se arquivos já estiverem rastreados. Não remover arquivos rastreados automaticamente. Skill, templates e documentação podem ser versionados conforme política da empresa. Não enviar memória corporativa ao GitHub pessoal. Para ambientes sem git, documente proteção local e risco de publicação posterior.

Integrações: forneça modo manual universal e adaptadores opt-in para hosts com capacidades verificadas. Não inventar formato de configuração ou hooks. Caso documentação atual não esteja disponível, marcar integração como manual/não verificada. Se host oferece início/compactação/fim de sessão, documentar como acionar checkpoint/init, limites de permissões e como desativar. Hooks não podem gerar resumo sem acesso legítimo ao contexto. Não disparar agentes ou chamadas pagas silenciosamente.

Aceitação: instalação duas vezes sem duplicações, preservação de AGENTS.md, worktree isolado, dry-run sem alterações, ignore testado, desinstalação não destrutiva e instruções para nova aba.
