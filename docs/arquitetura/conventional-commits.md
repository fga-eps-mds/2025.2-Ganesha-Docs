## 2. Padrão de Mensagens (Conventional Commits)

Todas as mensagens de commit devem seguir a estrutura do Conventional Commits para facilitar a geração de changelogs e a compreensão do histórico.

### 2.1. Estrutura da Mensagem

A mensagem do commit deve ser concisa e no formato imperativo (ex: "Adiciona...", "Corrige...", "Atualiza..."):

#### Campo Obrigatório: `<tipo>`

O **tipo** define a natureza da alteração. O uso correto influencia o versionamento automático:

| Tipo | Descrição | Deve gerar nova versão? |
| :--- | :--- | :--- |
| **`feat`** | Nova **feature** ou funcionalidade. | 🚀 **SIM** (Minor version) |
| **`fix`** | Correção de **bug**. | 🩹 **SIM** (Patch version) |
| **`docs`** | Alterações na **documentação** (MkDocs, README, etc.). | Não |
| **`style`** | Alterações que não afetam a lógica (espaços, formatação, ponto e vírgula, etc.). | Não |
| **`refactor`** | Reestruturação de código que não corrige bug nem adiciona funcionalidade. | Não |
| **`test`** | Adição ou alteração de testes unitários ou de integração. | Não |
| **`chore`** | Tarefas de manutenção (build, scripts, dependências, etc.). | Não |
| **`perf`** | Melhorias de performance. | Não |
| **`ci`** | Alterações nos arquivos de Integração Contínua (CI/CD). | Não |

#### Campo Opcional: `(<escopo>)`

O **escopo** define a parte específica do projeto que foi afetada (ex: `backend`, `frontend`, `auth`, `core`, `docs`).

#### Campo Obrigatório: `<descrição>`

Breve descrição da alteração, no presente e em modo imperativo (ex: "Adiciona validação", não "Adicionei validação").

### 2.2. Exemplos de Commits

| Exemplo | Análise |
| :--- | :--- |
| `feat(auth): Adiciona autenticacao por token JWT` | Nova funcionalidade (`feat`) no módulo de autenticação (`auth`). |
| `fix(core): Corrige divisao por zero no calculo de frete` | Correção de bug (`fix`) no código principal (`core`). |
| `docs(mkdocs): Atualiza guia de Conventional Commits` | Mudança apenas na documentação (`docs`) do MkDocs. |
| `refactor: Remove codigo duplicado da validacao de email` | Reorganização de código (`refactor`) sem escopo específico. |
| `BREAKING CHANGE: O campo 'user_id' foi renomeado para 'id_usuario'.` | Indica uma mudança que **quebra a compatibilidade** (deve estar no corpo ou rodapé). |