# Agent Memory Kit — especificação para implementação

Pacote de prompts para construir uma memória de trabalho persistente, local, portátil e seletiva para agentes de programação. Não é uma implementação executável: execute os prompts no agente com acesso ao workspace.

## Como utilizar
1. Abra um workspace vazio para desenvolver o kit, ou um projeto autorizado para instalá-lo. Preserve alterações existentes.
2. Forneça `prompts/00-master.md` ao agente e dê acesso aos demais arquivos deste pacote.
3. Execute as etapas 01 a 06 na ordem, ou delegue todas pelo prompt mestre. Cada etapa deve produzir código/arquivos reais e testes; não apenas sugestões.
4. Após instalar no projeto, use `memory init` em uma nova aba e `memory checkpoint` antes de trocar de sessão. Os nomes são intenções interpretadas pela skill, não comandos nativos.

## Resultado esperado
Skill reutilizável, armazenamento Markdown por projeto e tarefa, CLI Python 3 (biblioteca padrão), busca lexical, checkpoints atômicos, validação, instalação não destrutiva e documentação. Sem dependência de API, embeddings, MCP ou serviço externo. A IA redige a memória; o CLI gerencia persistência determinística. Não há promessa de execução automática sem hooks do host.

## Publicar este pacote
Em um terminal autenticado com GitHub CLI (`gh auth login`), dentro desta pasta:

```sh
git init -b main
git add README.md prompts
git commit -m 'docs: specify persistent agent memory kit'
gh repo create agent-memory-kit --private --source=. --remote=origin --push
```

Se o nome já existir, escolha outro. Não publique memória real de trabalho, código empresarial ou segredos no GitHub pessoal.
