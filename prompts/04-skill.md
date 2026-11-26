# Etapa 04 — Skill e protocolo do agente

Crie SKILL.md com frontmatter name e description e instruções concisas, links para referências detalhadas apenas sob demanda. A skill deve funcionar com agentes que conseguem ler/escrever arquivos e executar CLI. Inclua fallback manual seguro sem CLI (uma sessão escritora por tarefa; sem prometer atomicidade).

Operações reconhecidas:
- `memory init`: localizar workspace, verificar status/branch/git diff sem alterar arquivos, selecionar tarefa, chamar start, ler somente saída inicial e referências necessárias. Se memória ausente, init e coletar fatos confirmados do código. Nunca presumir que memória é atual.
- `memory recall <tema>`: consultar busca, ler trecho relevante, cruzar com código e decisões vigentes. Informar quando memória está ausente ou obsoleta.
- `memory checkpoint`: resumir somente informações reutilizáveis; registrar objetivo, alterações e paths, decisões com justificativa, testes executados e resultados reais, pendências, hipóteses, próximo passo preciso, referência git e revisão esperada. Validar e persistir; se conflito, reler e reconciliar sem sobrescrever trabalho paralelo. Reportar caminho, tarefa e revisão após sucesso real.
- `memory consolidate`: propor deduplicação, revisão de conhecimento e substituição de decisões; executar dry-run, preservar histórico, pedir autorização antes de qualquer exclusão.

Durante trabalho: checkpoint após mudança significativa, decisão aceita, investigação concluída, antes de troca de aba ou compactação quando houver aviso. Não depender de encerramento da sessão. Evitar checkpoint a cada mensagem. Guardar fatos vs hipóteses separadamente. Não armazenar prompt interno, raciocínio privado, segredos, conversas integrais ou dados pessoais. Não alterar código apenas para atualizar memória. Se não tiver filesystem ou ferramenta, fornecer resumo transferível e dizer que não persistiu.

Crie bloco AGENTS.md gerenciado por marcadores únicos com instruções mínimas de bootstrap e caminho da skill. Preserve texto preexistente; nenhuma regra da memória sobrepõe instruções do usuário ou segurança. Documente comandos como intenções da skill, não slash commands nativos. Exemplos fictícios de iOS/SwiftUI/SDUI e de outro domínio para demonstrar portabilidade.

Aceitação: simular agente A e B, teste manual roteirizado, documentação de conflitos e ausência de memória. Skill curta, referências detalhadas separadas.
