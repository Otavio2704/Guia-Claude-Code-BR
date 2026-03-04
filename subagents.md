# Subagentes do Claude Code

> **Um guia completo para agentes especializados no Claude Code — maximize sua produtividade com assistência de IA direcionada**

O Claude Code conta com subagentes especializados poderosos, projetados para lidar com tipos específicos de tarefas de desenvolvimento. Cada subagente é otimizado para fluxos de trabalho particulares e vem com ferramentas e domínios de conhecimento especializados.

## 📋 Índice

- [Visão Geral](#visão-geral)
- [Subagentes Disponíveis](#subagentes-disponíveis)
- [Referência Rápida](#referência-rápida)
- [Boas Práticas](#boas-práticas)
- [Fluxos de Integração](#fluxos-de-integração)

## Visão Geral

Os subagentes no Claude Code fornecem expertise especializada para diferentes aspectos do desenvolvimento de software. Em vez de usar um agente de propósito geral para todas as tarefas, você pode aproveitar esses agentes focados para obter melhores resultados em casos de uso específicos.

### Principais Benefícios

- **Conhecimento Especializado**: Cada agente possui expertise específica do domínio
- **Ferramentas Otimizadas**: Agentes têm acesso às ferramentas mais relevantes para sua especialidade
- **Melhor Contexto**: Agentes focados mantêm contexto relevante ao seu domínio
- **Resultados Mais Rápidos**: Agentes especializados podem trabalhar com mais eficiência em sua área

## Subagentes Disponíveis

### Especialistas em Desenvolvimento

#### [Desenvolvedor Frontend](subagents/frontend-developer.md)
Especializado na construção, modificação e depuração de componentes frontend, elementos de UI, estilização e lógica de interface do usuário.

#### [Desenvolvedor Backend](subagents/backend-developer.md)
Expert em desenvolvimento server-side, APIs, bancos de dados e arquitetura de sistemas.

#### [Desenvolvedor de APIs](subagents/api-developer.md)
Focado em design, implementação, documentação e integração de APIs.

#### [Desenvolvedor Mobile](subagents/mobile-developer.md)
Especializado em desenvolvimento de aplicativos móveis para plataformas iOS e Android.

### Especialistas em Linguagens

#### [Desenvolvedor Python](subagents/python-developer.md)
Expert em desenvolvimento Python, frameworks e ferramentas do ecossistema.

#### [Desenvolvedor JavaScript](subagents/javascript-developer.md)
Especializado em desenvolvimento JavaScript, Node.js e aplicações baseadas em navegador.

#### [Desenvolvedor TypeScript](subagents/typescript-developer.md)
Expert em desenvolvimento TypeScript, sistemas de tipos e padrões modernos de JavaScript.

#### [Desenvolvedor PHP](subagents/php-developer.md)
Especializado em desenvolvimento PHP, frameworks e desenvolvimento de aplicações web.

#### [Desenvolvedor WordPress](subagents/wordpress-developer.md)
Expert em desenvolvimento WordPress, temas, plugins e customização.

#### [Desenvolvedor iOS](subagents/ios-developer.md)
Especializado em desenvolvimento de aplicações iOS usando Swift e Objective-C.

### Banco de Dados e Arquitetura

#### [Designer de Banco de Dados](subagents/database-designer.md)
Expert em design de banco de dados, otimização e modelagem de dados.

### Qualidade e Manutenção de Código

#### [Revisor de Código](subagents/code-reviewer.md)
Especializado em revisão de código, avaliação de qualidade e aplicação de boas práticas.

#### [Depurador de Código](subagents/code-debugger.md)
Expert em depuração, troubleshooting e resolução de problemas.

#### [Documentador de Código](subagents/code-documenter.md)
Especializado na criação de documentação abrangente para codebases.

#### [Refatorador de Código](subagents/code-refactor.md)
Expert em refatoração, otimização e reestruturação de código.

#### [Auditor de Segurança de Código](subagents/code-security-auditor.md)
Especializado em análise de segurança, avaliação de vulnerabilidades e práticas de codificação segura.

#### [Aplicador de Padrões de Código](subagents/code-standards-enforcer.md)
Expert em padrões de codificação, guias de estilo e aplicação de consistência no código.

## Referência Rápida

### Quando Usar Cada Subagente

| Tipo de Tarefa | Subagente Recomendado | Exemplo de Uso |
|---------------|----------------------|----------------|
| Construir componentes de UI | Especialista Frontend | "Crie uma barra de navegação responsiva" |
| Revisão de qualidade de código | Revisor de Código | "Revise este código para produção" |
| Escrever documentação | Documentador de Código | "Documente este módulo de autenticação" |
| Pesquisa complexa | Propósito Geral | "Encontre todos os endpoints de API no codebase" |
| Automação em múltiplas etapas | Propósito Geral | "Configure pipeline CI/CD com testes" |

### Padrões de Invocação de Subagentes

```bash
# Usando a ferramenta Task para invocar subagentes
/task description="Construir componente de perfil de usuário" subagent_type="frontend-developer"
/task description="Revisar qualidade do código" subagent_type="code-reviewer"
/task description="Criar documentação de API" subagent_type="code-documenter"
/task description="Pesquisar schema do banco de dados" subagent_type="database-designer"
```

## Boas Práticas

### Escolhendo o Subagente Correto

1. **Combine Tarefa com Expertise**: Escolha o subagente cuja especialidade se alinha com sua tarefa
2. **Considere os Requisitos de Ferramentas**: Alguns subagentes têm acesso limitado a ferramentas por design
3. **Pense no Contexto**: Agentes especializados mantêm melhor contexto focado
4. **Use Propósito Geral para Tarefas Complexas**: Quando as tarefas abrangem múltiplos domínios, use o agente de propósito geral

### Uso Eficaz de Subagentes

1. **Seja Específico**: Forneça descrições de tarefas claras e detalhadas
2. **Defina Expectativas Claras**: Especifique o que você quer que o subagente entregue
3. **Forneça Contexto**: Inclua informações de contexto relevantes
4. **Encadeie Subagentes**: Use múltiplos subagentes em sequência para fluxos complexos

### Padrões Comuns

```bash
# Fluxo de Desenvolvimento Frontend
1. Desenvolvedor Frontend: Construir componente
2. Revisor de Código: Revisar para produção
3. Documentador de Código: Criar documentação do componente

# Fluxo de Revisão de Código
1. Revisor de Código: Verificação inicial de qualidade
2. Auditor de Segurança: Análise de vulnerabilidades
3. Documentador de Código: Atualizar documentação

# Pesquisa e Implementação
1. Propósito Geral: Pesquisa e planejamento
2. Agente Especializado: Implementação
3. Revisor de Código: Revisão final
```

## Fluxos de Integração

### Fluxos Multi-Agente

O Claude Code permite encadear subagentes para fluxos de trabalho complexos:

1. **Processamento Sequencial**: Use agentes um após o outro
2. **Processamento Paralelo**: Execute múltiplos agentes simultaneamente
3. **Lógica Condicional**: Escolha agentes com base nos requisitos da tarefa

### Exemplos de Fluxos

#### Desenvolvimento Completo de Feature
```
1. Propósito Geral: Pesquisar requisitos e planejar arquitetura
2. Desenvolvedor Frontend: Construir componentes de interface do usuário
3. Revisor de Código: Revisar qualidade e segurança do código
4. Documentador de Código: Criar documentação abrangente
```

#### Pipeline de Qualidade de Código
```
1. Revisor de Código: Verificações automatizadas de qualidade
2. Auditor de Segurança: Análise de vulnerabilidades
3. Refatorador de Código: Aplicar melhorias sugeridas
4. Documentador de Código: Atualizar documentação
```

## Como Começar

1. **Identifique o Tipo de Tarefa**: Determine qual subagente é mais apropriado
2. **Use a Ferramenta Task**: Invoque o subagente usando a ferramenta Task do Claude Code
3. **Forneça Instruções Claras**: Seja específico sobre o que você quer que seja realizado
4. **Revise os Resultados**: Cada subagente fornecerá uma resposta focada
5. **Encadeie Conforme Necessário**: Use múltiplos subagentes para fluxos complexos

## Uso Avançado

### Padrões de Subagentes Personalizados

Você pode criar fluxos sofisticados combinando subagentes com outros recursos do Claude Code:

- **Gerenciamento de Sessão**: Mantenha contexto entre invocações de subagentes
- **Permissões de Ferramentas**: Configure acesso específico a ferramentas para segurança
- **Formatação de Saída**: Use saída estruturada para automação
- **Tratamento de Erros**: Implemente padrões de fallback entre subagentes

### Otimização de Performance

- Use subagentes especializados para reduzir troca de contexto
- Aproveite execução paralela de subagentes quando possível
- Cache resultados comuns de subagentes para tarefas repetidas
- Monitore performance de subagentes com o rastreamento de custos do Claude Code

---

Para informações detalhadas sobre cada subagente, consulte os arquivos de documentação individuais no diretório `subagents/`.