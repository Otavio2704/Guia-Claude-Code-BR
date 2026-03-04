# Guia Completo do Claude Code (Beta)

![Alt text](images/claude-code-cheat-sheet.png)

> **Seu guia completo para dominar o Claude Code — do básico ao avançado em minutos!**

Depois de testar o Claude Code extensivamente, desenvolvi este guia abrangente que vai te levar do básico ao avançado sem perder tempo. Seja você completamente novo no Claude Code ou querendo dominar recursos avançados, este guia tem tudo que você precisa.

## Início Rápido

```bash
# Usuários Windows
wsl

# Instalar o Claude Code
npm install -g @anthropic-ai/claude-code

# Iniciar o REPL interativo
claude

# Verificar versão
claude --version
```

## 📚 Índice

- 🟢 **Nível 1: Comandos Básicos**
- 🟡 **Nível 2: Comandos Intermediários**
- 🟠 **Nível 3: Comandos Avançados**
- 🔴 **Nível 4: Comandos Expert**
- 🔵 **Nível 5: Usuário Avançado**
- 🟣 **Nível 6: Comandos Master**
- 🟤 **Nível 7: Automação de Fluxo de Trabalho**
- ⚫ **Nível 8: Integrações e Ecossistema**
- ⚪ **Nível 9: Performance e Otimização**
- 🔘 **Nível 10: Empresa e Produção**
- 🧠 **Arquivo CLAUDE.md — Memória Persistente**
- 🪝 **Hooks do Claude Code**
- 🌍 **Variáveis de Ambiente**
- 🤖 **Orquestração Multi-Agente**
- 🚀 **Integração com GitHub Actions**
- 🤝 **Contribuindo**
- 📄 **Licença**

### Páginas

- 🤖 **[Subagentes](subagents.md)** — Agentes de IA especializados para tarefas de desenvolvimento

---

## 🟢 Nível 1: Comandos Básicos

Comandos essenciais para começar

### Instalação e Primeiros Passos

```bash
# Instalar o Claude Code
curl -sL https://install.anthropic.com | sh

# Iniciar o REPL interativo
claude

# Iniciar com prompt inicial
claude "resuma este projeto"

# Verificar versão
claude --version

# Atualizar para a versão mais recente
claude update
```

### Navegação Básica

```bash
/help                     # Mostrar ajuda e comandos disponíveis
/exit                     # Sair do REPL
/clear                    # Limpar histórico de conversa
/config                   # Abrir painel de configuração
/doctor                   # Verificar a saúde da instalação do Claude Code
```

### Operações Básicas com Arquivos

```bash
# Modo print (SDK) — executar e sair
claude -p "explique esta função"

# Processar conteúdo via pipe
cat logs.txt | claude -p "explique"

# Continuar a conversa mais recente
claude -c

# Continuar via SDK
claude -c -p "Verifique erros de tipo"
```

### Gerenciamento de Sessão

```bash
# Retomar sessão pelo ID
claude -r "abc123" "Termine este PR"

# Retomar com flag
claude --resume abc123 "consulta"

# Continuar sessão
claude --continue
```

### Atalhos de Teclado

```bash
Ctrl+C                    # Cancelar operação atual
Ctrl+D                    # Sair do Claude Code
Tab                       # Auto-completar
Seta Cima/Baixo           # Navegar no histórico de comandos
```

---

## 🟡 Nível 2: Comandos Intermediários

Configuração e gerenciamento de modelos

### Configuração de Modelo

```bash
# Trocar modelos
claude --model sonnet                    # Usar modelo Sonnet
claude --model opus                      # Usar modelo Opus
claude --model claude-sonnet-4-20250514  # Usar versão específica do modelo
```

### Gerenciamento de Diretórios

```bash
# Adicionar diretórios de trabalho adicionais
claude --add-dir ../apps ../lib

# Validar caminhos de diretório
claude --add-dir /caminho/para/projeto
```

### Formatação de Saída

```bash
# Diferentes formatos de saída
claude -p "consulta" --output-format json
claude -p "consulta" --output-format text
claude -p "consulta" --output-format stream-json

# Formatação de entrada
claude -p --input-format stream-json
```

### Controle de Sessão

```bash
# Limitar turnos de conversa
claude -p --max-turns 3 "consulta"

# Log detalhado
claude --verbose

# Custo e duração da sessão
/cos                      # Mostrar custo e duração totais
```

---

## 🟠 Nível 3: Comandos Avançados

Gerenciamento de ferramentas e permissões

### Gerenciamento de Ferramentas

```bash
# Permitir ferramentas específicas sem confirmação
claude --allowedTools "Bash(git log:*)" "Bash(git diff:*)" "Write"

# Desabilitar ferramentas específicas
claude --disallowedTools "Bash(rm:*)" "Bash(sudo:*)"

# Solicitar permissão para ferramenta específica
claude -p --permission-prompt-tool mcp_auth_tool "consulta"

# Pular todas as confirmações de permissão (perigoso)
claude --dangerously-skip-permissions
```

### Comandos Slash — Gerenciamento de Sessão

```bash
/compact [instruções]     # Resumir conversa com instruções opcionais
/clear                    # Resetar histórico e contexto da conversa
/exit                     # Sair do REPL
/help                     # Mostrar comandos disponíveis
/config                   # Abrir painel de configuração
```

### Comandos Slash — Sistema

```bash
/doctor                   # Verificar saúde da instalação
/cos                      # Mostrar custo e duração da sessão atual
/ide                      # Gerenciar integrações com IDEs
```

---

## 🔴 Nível 4: Comandos Expert

MCP e integrações avançadas

### Model Context Protocol (MCP)

```bash
# Configurar servidores MCP
claude --mcp

# Gerenciamento de servidor MCP (via comandos slash)
/mcp                      # Acessar funcionalidade MCP
```

### Piping Avançado

```bash
# Operações de piping complexas
git log --oneline | claude -p "resuma esses commits"
cat error.log | claude -p "encontre a causa raiz"
ls -la | claude -p "explique esta estrutura de diretórios"
```

### Uso Programático

```bash
# Saída JSON para scripts
claude -p "analise o código" --output-format json

# Stream JSON para processamento em tempo real
claude -p "tarefa grande" --output-format stream-json

# Processamento em lote
claude -p --max-turns 1 "consulta rápida"
```

---

## 🔵 Nível 5: Usuário Avançado

Fluxos avançados e automação

### Comandos Slash Personalizados

```bash
# Criar comandos personalizados em .claude/commands/
# Exemplo: .claude/commands/debug.md
/debug                    # Executar comando de debug personalizado
/test                     # Executar comando de teste personalizado
/deploy                   # Executar comando de deploy personalizado
```

### Combinações Complexas de Ferramentas

```bash
# Permissões avançadas de ferramentas
claude --allowedTools "Bash(git:*)" "Write" "Read" \
       --disallowedTools "Bash(rm:*)" "Bash(sudo:*)"

# Acesso a múltiplos diretórios
claude --add-dir ../frontend ../backend ../shared
```

### Otimização de Performance

```bash
# Limitar contexto para melhor performance
claude -p --max-turns 5 "consulta focada"

# Limpar contexto frequentemente
/clear                    # Use entre tarefas para melhor performance

# Compactar conversas
/compact "manter apenas partes importantes"
```

---

## 🟣 Nível 6: Comandos Master

Automação expert e fluxos personalizados

### Configuração Avançada

```bash
# Configuração complexa de modelo e ferramentas
claude --model claude-sonnet-4-20250514 \
       --add-dir ../apps ../lib ../tools \
       --allowedTools "Bash(git:*)" "Write" "Read" \
       --verbose \
       --output-format json
```

### Scripts de Automação

```bash
# Interações programadas com Claude
#!/bin/bash
claude -p "analise o codebase" --output-format json > analysis.json
claude -p "gere testes" --max-turns 3 --output-format text > tests.txt
```

### Gerenciamento Avançado de Sessões

```bash
# Gerenciamento de IDs de sessão
SESSION_ID=$(claude -p "iniciar análise" --output-format json | jq -r '.session_id')
claude -r "$SESSION_ID" "continue a análise"
```

### Fluxos Complexos

```bash
# Automação em múltiplas etapas
claude -p "analise a estrutura do projeto" | \
claude -p "sugira melhorias" | \
claude -p "crie plano de implementação"
```

---

## 🟤 Nível 7: Automação de Fluxo de Trabalho

Padrões avançados de automação e processos em múltiplas etapas

### Fluxos Automatizados de Revisão de Código

```bash
# Processo automatizado de revisão de PR
#!/bin/bash
git diff HEAD~1 | claude -p "revise este PR para problemas de segurança" > security_review.md
git diff HEAD~1 | claude -p "verifique problemas de performance" > performance_review.md
git diff HEAD~1 | claude -p "sugira melhorias" > improvements.md
```

### Integração com CI/CD

```bash
# Integração com pipeline CI/CD
claude -p "analise cobertura de testes" --output-format json | jq '.coverage_percentage'
claude -p "gere notas de versão dos commits" --max-turns 2 > RELEASE_NOTES.md
```

### Fluxos de Processamento em Lote

```bash
# Processar múltiplos arquivos
find . -name "*.js" -exec claude -p "analise este arquivo para bugs: {}" \; > bug_report.txt

# Geração automatizada de documentação
for file in src/*.py; do
    claude -p "gere docstring para $file" --output-format text >> docs.md
done
```

---

## ⚫ Nível 8: Integração e Ecossistema

Integrações com IDE, fluxos Git e conexões com ferramentas de terceiros

### Comandos de Integração com IDE

```bash
# Integração com VS Code
/ide vscode                # Configurar integração com VS Code
/ide configure             # Configurar integrações de IDE

# Comandos personalizados de IDE
claude --ide-mode "explique o código selecionado"
claude --ide-mode "refatore esta função"
```

### Integração com Fluxo Git

```bash
# Integração com git hooks
claude -p "crie pre-commit hook para qualidade de código" > .git/hooks/pre-commit

# Operações Git avançadas
git log --oneline -10 | claude -p "crie changelog desses commits"
git diff --name-only | claude -p "explique o que mudou neste commit"
```

### Conexões com Ferramentas de Terceiros

```bash
# Integração com banco de dados
mysql -e "SHOW TABLES" | claude -p "analise estrutura do banco de dados"

# Integração com Docker
docker ps | claude -p "analise os containers em execução"
docker logs nome_container | claude -p "encontre erros nos logs"
```

---

## ⚪ Nível 9: Performance e Otimização

Ajuste avançado de performance, gerenciamento de recursos e dicas de eficiência

### Gerenciamento de Memória e Recursos

```bash
# Otimizar uso de memória
claude -p --max-turns 1 "análise rápida"      # Turno único para eficiência

# Monitoramento de recursos
/cos                       # Verificar custos da sessão atual
/doctor                    # Diagnósticos de performance
```

### Cache e Otimização

```bash
# Reutilização eficiente de sessão
claude -c "continue a análise anterior"         # Reutilizar contexto existente

# Processamento paralelo
claude -p "tarefa 1" & claude -p "tarefa 2" & wait  # Execução paralela
```

### Processamento em Grande Escala

```bash
# Lidar com codebases grandes de forma eficiente
claude --add-dir . "analise o projeto inteiro"
claude -p "processar grande dataset" --output-format stream-json | head -100
```

---

## 🔘 Nível 10: Empresa e Produção

Configurações prontas para produção, fluxos de equipe e recursos enterprise

### Colaboração em Equipe

```bash
# Configurações compartilhadas de equipe
claude --config-file team-config.json "análise padronizada"

# Compartilhamento de sessão em equipe
claude -r "team-session-id" "continue a discussão da equipe"
```

### Configuração de Ambiente de Produção

```bash
# Configuração pronta para produção
claude --dangerously-skip-permissions \
       --output-format json \
       --max-turns 10 \
       "análise de produção"
```

### Segurança Enterprise

```bash
# Operações focadas em segurança
claude --disallowedTools "Bash(rm:*)" "Bash(sudo:*)" "Bash(chmod:*)" \
       "revisão segura de código"
```

---

## 🧠 Arquivo CLAUDE.md — Memória Persistente

O arquivo `CLAUDE.md` é o sistema de **memória persistente** do Claude Code. Ele é lido automaticamente no início de cada sessão, permitindo que você defina instruções, contexto e convenções permanentes para o projeto.

### Localização e Hierarquia

```
~/CLAUDE.md                  # Instruções globais do usuário (~/.claude/CLAUDE.md)
projeto/CLAUDE.md            # Instruções do projeto (mais alta prioridade)
projeto/subpasta/CLAUDE.md   # Instruções de subdiretório
```

### Exemplo de CLAUDE.md para um Projeto

```markdown
# Instruções do Projeto

## Stack Tecnológica
- Backend: Node.js + Express + TypeScript
- Banco de dados: PostgreSQL com Prisma ORM
- Frontend: React + Vite + TailwindCSS

## Convenções de Código
- Use async/await, nunca callbacks
- Nomes de variáveis em camelCase, arquivos em kebab-case
- Sempre adicione tipos TypeScript explícitos
- Testes com Jest — cobertura mínima de 80%

## Comandos Importantes
- `npm run dev` — iniciar servidor de desenvolvimento
- `npm run test` — executar testes
- `npm run build` — build de produção
- `npm run db:migrate` — executar migrações do banco

## Regras de Negócio
- Nunca deletar registros diretamente; use soft delete (campo `deletedAt`)
- Autenticação via JWT com refresh tokens
- Todas as rotas de API devem ter autenticação exceto /health e /auth
```

### Comandos para Gerenciar Memória

```bash
# Abrir ou criar o CLAUDE.md do projeto
claude "abra o CLAUDE.md e adicione as convenções de código do projeto"

# Adicionar instrução à memória
claude "adicione ao CLAUDE.md: sempre usar pnpm ao invés de npm"

# Ver memória atual
claude "mostre o conteúdo do CLAUDE.md"
```

### Boas Práticas para CLAUDE.md

- Mantenha instruções **concisas e objetivas**
- Liste comandos de build, teste e deploy do projeto
- Documente padrões de arquitetura e decisões técnicas
- Inclua regras de negócio críticas para evitar erros
- Atualize sempre que convenções mudarem

---

## 🪝 Hooks do Claude Code

Hooks permitem executar **scripts personalizados** antes e depois das ações do Claude, dando controle total sobre o fluxo de trabalho.

### Tipos de Hooks

| Hook | Quando Executa |
|------|---------------|
| `PreToolUse` | Antes do Claude usar qualquer ferramenta |
| `PostToolUse` | Após o Claude usar uma ferramenta |
| `Notification` | Quando o Claude envia uma notificação |
| `Stop` | Quando o Claude termina de responder |

### Configuração de Hooks

Os hooks são configurados no arquivo `settings.json` do Claude Code:

```bash
# Localização do arquivo de configurações
~/.claude/settings.json          # Configurações globais
projeto/.claude/settings.json    # Configurações do projeto
```

### Exemplo de Configuração de Hooks

```json
{
  "hooks": {
    "PreToolUse": [
      {
        "matcher": "Bash",
        "hooks": [
          {
            "type": "command",
            "command": "echo 'Executando comando Bash: ' && cat"
          }
        ]
      }
    ],
    "PostToolUse": [
      {
        "matcher": "Write",
        "hooks": [
          {
            "type": "command",
            "command": "npx prettier --write"
          }
        ]
      }
    ]
  }
}
```

### Casos de Uso de Hooks

```bash
# Formatar arquivo automaticamente após escrita
# PostToolUse com matcher "Write" → executar prettier/eslint --fix

# Bloquear comandos perigosos
# PreToolUse com matcher "Bash" → verificar se o comando contém "rm -rf"

# Notificar via Telegram/Slack quando tarefa terminar
# Stop hook → curl para webhook

# Rodar testes após modificar arquivos
# PostToolUse com matcher "Write" → npm test

# Log de auditoria de todas as ações
# PreToolUse + PostToolUse → salvar em arquivo de log
```

### Hook de Formatação Automática

```json
{
  "hooks": {
    "PostToolUse": [
      {
        "matcher": "Write|Edit",
        "hooks": [
          {
            "type": "command",
            "command": "file=$(cat) && [[ \"$file\" == *.ts || \"$file\" == *.tsx ]] && npx prettier --write \"$file\" || true"
          }
        ]
      }
    ]
  }
}
```

---

## 🌍 Variáveis de Ambiente

Configure o comportamento do Claude Code através de variáveis de ambiente.

### Variáveis Essenciais

```bash
# Chave de API da Anthropic
export ANTHROPIC_API_KEY="sk-ant-..."

# Modelo padrão
export CLAUDE_MODEL="claude-sonnet-4-20250514"

# Nível de log
export CLAUDE_LOG_LEVEL="debug"   # debug | info | warn | error

# Diretório de configuração personalizado
export CLAUDE_CONFIG_DIR="~/.config/claude"
```

### Configuração de Proxy (Ambientes Corporativos)

```bash
# Proxy HTTP/HTTPS
export HTTP_PROXY="http://proxy.empresa.com:8080"
export HTTPS_PROXY="http://proxy.empresa.com:8080"
export NO_PROXY="localhost,127.0.0.1,.empresa.com"

# Para ambientes com SSL corporativo
export NODE_EXTRA_CA_CERTS="/caminho/para/cert-corporativo.pem"
```

### Variáveis para Automação

```bash
# Desabilitar confirmações interativas (para CI/CD)
export CLAUDE_SKIP_PERMISSIONS="true"

# Timeout de operações (em segundos)
export CLAUDE_TIMEOUT="120"

# Saída não-colorida para logs
export NO_COLOR="1"
export FORCE_COLOR="0"
```

### Integração com Serviços de Nuvem

```bash
# AWS Bedrock (alternativa à API direta)
export ANTHROPIC_API_URL="https://bedrock-runtime.us-east-1.amazonaws.com"

# Azure (modelos hospedados no Azure)
export ANTHROPIC_API_URL="https://sua-instancia.openai.azure.com"
export AZURE_API_KEY="sua-chave-azure"
```

---

## 🤖 Orquestração Multi-Agente

O Claude Code suporta orquestração de múltiplos agentes, permitindo que um agente principal coordene subagentes especializados para tarefas complexas.

### Como Funciona

```
Agente Orquestrador (Claude Principal)
├── Subagente 1: Análise de código
├── Subagente 2: Geração de testes
├── Subagente 3: Documentação
└── Subagente 4: Revisão de segurança
```

### Invocação de Subagentes via Task Tool

```bash
# O Claude pode usar a ferramenta Task para iniciar subagentes
claude "analise este projeto completo:
  1. Use um subagente para revisar segurança
  2. Use outro para verificar performance
  3. Use outro para atualizar documentação
  4. Consolide os resultados em um relatório"
```

### Padrão de Orquestração Paralela

```bash
# Script de orquestração com múltiplos agentes em paralelo
#!/bin/bash

# Iniciar análises em paralelo
claude -p "revise segurança do diretório src/" --output-format json > security.json &
PID1=$!

claude -p "analise performance do diretório src/" --output-format json > perf.json &
PID2=$!

claude -p "verifique cobertura de testes" --output-format json > coverage.json &
PID3=$!

# Aguardar todos terminarem
wait $PID1 $PID2 $PID3

# Consolidar resultados
claude -p "consolide estes relatórios em um sumário executivo: 
  $(cat security.json) 
  $(cat perf.json) 
  $(cat coverage.json)" > relatorio_final.md
```

### Padrão Orquestrador → Especialista

```bash
# Agente orquestrador decomposição de tarefa
claude "você é o orquestrador. Para cada arquivo .py em src/:
  - Lance um subagente especialista em Python para refatorar
  - Lance um subagente de testes para criar unit tests
  - Lance um subagente de documentação para atualizar docstrings
  Use a ferramenta Task para cada subagente"
```

### Configuração de Subagentes Personalizados

Crie arquivos em `.claude/agents/` para definir subagentes:

```markdown
<!-- .claude/agents/security-reviewer.md -->
---
name: security-reviewer
description: Especialista em revisão de segurança. Use para análise de vulnerabilidades.
model: claude-opus-4-5
---

Você é um especialista em segurança cibernética focado em:
- OWASP Top 10
- Análise de dependências (CVEs)
- Secrets expostos no código
- Configurações inseguras

Retorne um JSON estruturado com severidade e recomendações.
```

---

## 🚀 Integração com GitHub Actions

Automatize o Claude Code em seus pipelines de CI/CD.

### Workflow Básico de Revisão de PR

```yaml
# .github/workflows/claude-review.yml
name: Claude Code Review

on:
  pull_request:
    types: [opened, synchronize]

jobs:
  code-review:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
        with:
          fetch-depth: 0

      - name: Setup Node.js
        uses: actions/setup-node@v4
        with:
          node-version: '20'

      - name: Install Claude Code
        run: npm install -g @anthropic-ai/claude-code

      - name: Review PR with Claude
        env:
          ANTHROPIC_API_KEY: ${{ secrets.ANTHROPIC_API_KEY }}
        run: |
          git diff origin/main...HEAD > pr_diff.txt
          cat pr_diff.txt | claude -p "
            Revise este PR e forneça:
            1. Vulnerabilidades de segurança
            2. Problemas de performance
            3. Sugestões de melhoria
            Formato: Markdown com severidade (🔴 Crítico, 🟡 Aviso, 🟢 Sugestão)
          " --output-format text > review.md

      - name: Post Review Comment
        uses: actions/github-script@v7
        with:
          script: |
            const fs = require('fs');
            const review = fs.readFileSync('review.md', 'utf8');
            github.rest.issues.createComment({
              issue_number: context.issue.number,
              owner: context.repo.owner,
              repo: context.repo.repo,
              body: `## 🤖 Revisão do Claude Code\n\n${review}`
            });
```

### Workflow de Geração Automática de Testes

```yaml
# .github/workflows/claude-tests.yml
name: Auto-Generate Tests

on:
  push:
    paths:
      - 'src/**/*.ts'
      - 'src/**/*.py'

jobs:
  generate-tests:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - name: Install Claude Code
        run: npm install -g @anthropic-ai/claude-code

      - name: Generate Tests for Changed Files
        env:
          ANTHROPIC_API_KEY: ${{ secrets.ANTHROPIC_API_KEY }}
        run: |
          # Pegar arquivos modificados
          CHANGED=$(git diff --name-only HEAD~1 HEAD | grep -E '\.(ts|py)$')
          
          for file in $CHANGED; do
            echo "Gerando testes para $file..."
            claude -p "Gere testes unitários completos para: $(cat $file)" \
              --output-format text > "tests/$(basename $file .ts).test.ts"
          done

      - name: Create Pull Request with Tests
        uses: peter-evans/create-pull-request@v6
        with:
          title: "test: testes gerados automaticamente pelo Claude"
          commit-message: "test: adicionar testes gerados pelo Claude Code"
          branch: "claude/auto-tests"
```

### Workflow de Documentação Automática

```yaml
# .github/workflows/claude-docs.yml
name: Auto-Documentation

on:
  push:
    branches: [main]

jobs:
  update-docs:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - name: Install Claude Code
        run: npm install -g @anthropic-ai/claude-code

      - name: Update README
        env:
          ANTHROPIC_API_KEY: ${{ secrets.ANTHROPIC_API_KEY }}
        run: |
          claude -p "
            Analise o projeto e atualize o README.md para refletir:
            1. Estrutura atual do projeto
            2. Como instalar e executar
            3. API pública e exemplos de uso
            Mantenha o estilo existente do README.
          " --output-format text

      - name: Commit docs
        run: |
          git config --local user.email "claude-bot@github.com"
          git config --local user.name "Claude Code Bot"
          git add README.md
          git diff --staged --quiet || git commit -m "docs: atualizar documentação via Claude Code"
          git push
```

---

## Tabelas de Referência de Comandos

### Comandos CLI

| Comando | Descrição | Exemplo |
|---------|-----------|---------|
| `claude` | Iniciar REPL interativo | `claude` |
| `claude "consulta"` | Iniciar REPL com prompt | `claude "explique este projeto"` |
| `claude -p "consulta"` | Modo print, executar e sair | `claude -p "explique função"` |
| `claude -c` | Continuar conversa recente | `claude -c` |
| `claude -r "id" "consulta"` | Retomar sessão pelo ID | `claude -r "abc123" "terminar PR"` |
| `claude update` | Atualizar para a versão mais recente | `claude update` |
| `claude mcp` | Configurar servidores MCP | `claude mcp` |

### Flags CLI

| Flag | Descrição | Exemplo |
|------|-----------|---------|
| `--model` | Especificar modelo | `--model sonnet` |
| `--add-dir` | Adicionar diretórios de trabalho | `--add-dir ../apps ../lib` |
| `--allowedTools` | Permitir ferramentas sem confirmação | `--allowedTools "Bash(git:*)"` |
| `--disallowedTools` | Desabilitar ferramentas específicas | `--disallowedTools "Bash(rm:*)"` |
| `--output-format` | Definir formato de saída | `--output-format json` |
| `--input-format` | Definir formato de entrada | `--input-format stream-json` |
| `--max-turns` | Limitar turnos de conversa | `--max-turns 3` |
| `--verbose` | Habilitar log detalhado | `--verbose` |
| `--continue` | Continuar sessão | `--continue` |
| `--resume` | Retomar sessão | `--resume abc123` |
| `--dangerously-skip-permissions` | Pular todas as confirmações de permissão | `--dangerously-skip-permissions` |

### Comandos Slash

| Comando | Descrição |
|---------|-----------|
| `/help` | Mostrar ajuda e comandos disponíveis |
| `/exit` | Sair do REPL |
| `/clear` | Limpar histórico de conversa |
| `/config` | Abrir painel de configuração |
| `/doctor` | Verificar saúde da instalação |
| `/cos` | Mostrar custo e duração |
| `/ide` | Gerenciar integrações com IDE |
| `/compact [instruções]` | Resumir conversa |
| `/mcp` | Acessar funcionalidade MCP |

### Atalhos de Teclado

| Atalho | Ação |
|--------|------|
| `Ctrl+C` | Cancelar operação atual |
| `Ctrl+D` | Sair do Claude Code |
| `Tab` | Auto-completar |
| `Seta Cima/Baixo` | Navegar no histórico de comandos |

---

## Boas Práticas

### Dicas de Performance

- Use `/clear` frequentemente entre tarefas
- Limite contexto com `--max-turns`
- Use `/compact` para conversas longas
- Especifique ferramentas exatas com `--allowedTools`

### Dicas de Segurança

- Evite `--dangerously-skip-permissions`
- Use `--disallowedTools` para comandos perigosos
- Revise permissões de ferramentas regularmente
- Mantenha o Claude Code atualizado

### Dicas de Fluxo de Trabalho

- Crie comandos slash personalizados em `.claude/commands/`
- Use `--output-format json` para automação
- Encadeie comandos para fluxos complexos
- Use IDs de sessão para tarefas de longa duração
- Mantenha o `CLAUDE.md` atualizado com convenções do projeto
- Configure hooks para automação de formatação e testes

---

## Boas Práticas por Nível

### Iniciante (Níveis 1-3)

- Comece com comandos básicos e avance gradualmente
- Use `/help` frequentemente para descobrir novos recursos
- Pratique com consultas simples antes das complexas
- Mantenha sessões focadas com `/clear` entre tarefas

### Intermediário (Níveis 4-6)

- Domine permissões de ferramentas para segurança
- Use saída JSON para scripts de automação
- Aprenda MCP para integrações avançadas
- Crie comandos slash personalizados para tarefas repetidas

### Avançado (Níveis 7-10)

- Implemente fluxos automatizados para tarefas repetitivas
- Use recursos enterprise para colaboração em equipe
- Monitore performance e otimize uso de recursos
- Siga boas práticas de segurança em produção
- Configure CLAUDE.md para cada projeto
- Use hooks para automatizar qualidade de código
- Implemente orquestração multi-agente para tarefas complexas

---

## Dicas e Truques Pro

### Dicas de Eficiência

- Use `Ctrl+C` para cancelar operações longas
- Combine múltiplas flags para configurações complexas
- Use piping para processamento de dados em múltiplas etapas
- Crie templates de CLAUDE.md reutilizáveis para tipos de projeto

### Dicas Pro de Segurança

- Sempre use `--disallowedTools` para comandos perigosos
- Habilite log de auditoria via hooks em ambientes de produção
- Revise permissões de ferramentas regularmente
- Nunca commite a `ANTHROPIC_API_KEY` no código

### Dicas Pro de Fluxo de Trabalho

- Crie templates para padrões comuns de automação
- Use IDs de sessão para tarefas colaborativas longas
- Implemente tratamento de erros adequado em scripts de automação
- Documente fluxos personalizados no CLAUDE.md para compartilhamento com equipe

---

## Solução de Problemas Comuns

### Problemas de Instalação

```bash
# Verificar instalação
claude --version
claude /doctor

# Reinstalar se necessário
npm uninstall -g @anthropic-ai/claude-code
npm install -g @anthropic-ai/claude-code
```

### Problemas de Performance

```bash
# Limpar contexto para melhor performance
/clear

# Limitar tamanho do contexto
claude -p --max-turns 3 "consulta focada"

# Usar modo compacto
/compact "manter apenas o essencial"
```

### Problemas de Permissão

```bash
# Configurar permissões específicas
claude --allowedTools "Bash(git:*)" --disallowedTools "Bash(rm:*)"
```

### Problemas de Conectividade (Rede Corporativa)

```bash
# Configurar proxy
export HTTPS_PROXY="http://proxy.empresa.com:8080"
export NODE_EXTRA_CA_CERTS="/caminho/para/cert.pem"
claude --version  # Testar conexão
```

---

## 🤝 Contribuindo

Contribuições são bem-vindas! Consulte a documentação do Claude Code para diretrizes.

### Formas de Contribuir

- 🐛 Reportar bugs ou problemas
- 📝 Melhorar a documentação
- ✨ Adicionar novos exemplos de comandos
- 🔧 Testar comandos e relatar resultados

## 📄 Licença

Este guia é fornecido sob a licença MIT.

## ⭐ Apoio

Se este guia te ajudou, compartilhe com outros desenvolvedores!

- ⭐ Dê uma estrela no repositório GitHub
- 📢 Compartilhe com outros desenvolvedores
- 💬 Deixe seu feedback nos comentários
- 🔄 Siga para atualizações

## Recursos e Aprendizado Adicional

Para mais recursos sobre Claude Code, visite a documentação oficial da Anthropic:

- [Documentação Oficial do Claude Code](https://docs.anthropic.com/en/docs/claude-code)
- [Repositório GitHub do Claude Code](https://github.com/anthropic-ai/claude-code)
- [Documentação da API da Anthropic](https://docs.anthropic.com)
- [Documentação MCP](https://docs.anthropic.com/en/docs/build-with-claude/mcp)

**Última atualização**: Março de 2026
