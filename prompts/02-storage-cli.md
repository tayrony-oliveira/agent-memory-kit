# Etapa 02 — Persistência e CLI

Implemente `python3 -m agent_memory` com pacote instalável ou launcher local documentado. Comandos:
- `init --workspace PATH`: inicializar estrutura idempotentemente.
- `start --task ID [--session ID]`: criar/retomar sessão e emitir contexto inicial.
- `checkpoint --task ID --session ID --input FILE --expected-revision N`: receber Markdown estruturado validado; atualizar estado sem perder dados.
- `recall QUERY [--task ID] [--budget-chars N]`: recuperar trechos relevantes com caminhos e ranking determinístico.
- `status [--task ID]`: listar tarefas, revisão, branch e divergências.
- `validate`: detectar esquema inválido, links quebrados, metadados inconsistentes e arquivos suspeitos.
- `consolidate --input FILE [--dry-run]`: aplicar proposta explícita de consolidação validada; preservar decisões substituídas.

Permita `--json` para automação. Documente exit codes (0 sucesso, 2 entrada inválida, 3 conflito, 4 falha IO, 5 não encontrado), stdout para saída e stderr para erros. Não dependa de terminal interativo.

Use locks por tarefa e lock global para índice/consolidação, ordem fixa de aquisição, timeout explícito e liberação segura. Em macOS/Linux use flock ou mecanismo equivalente testado. Use optimistic concurrency com revision; conflito não sobrescreve, devolve revisão atual para reconciliação. Escreva temporário no mesmo diretório, flush/fsync e os.replace. Para operações multi-arquivo, defina ponto de commit e recuperação idempotente (journal ou snapshots imutáveis + ponteiro atômico); nunca alegue atomicidade de múltiplos replaces. Índice derivado pode ser reconstruído. Não seguir symlinks inseguros. Validar tamanho, IDs, encoding e schema antes de escrever. Aplicar permissões locais restritivas quando possível.

O CLI não resume conversas nem inventa dados; recebe conteúdo do agente. Inclua filtros conservadores de credenciais comuns, mas documente que não garantem ausência de segredos. Logs sem conteúdo sensível. Teste entradas inválidas, conflito, processo interrompido, UTF-8, workspace inexistente, traversal, symlink e repetição de init.
