# 📄 Ata de Reunião #02 - Planejamento e Estrutura do Banco de Dados

| Tópico | Detalhe |
| :--- | :--- |
| **Data** | 29 de Outubro de 2025 |
| **Foco** | Revisão de Setup Inicial e Planejamento do Banco de Dados (Modelo) |
| **Próximo Encontro** | A Definir |

### 👥 Participantes

* Brenda
* Caio
* Daniel
* Eduarda
* Gabriel
* Guilherme

---

### ✅ Status das Entregas (Revisão da Ata #01)

| Entrega | Status | Observações |
| :--- | :--- | :--- |
| Configurar a estrutura de diretórios base (padrão MVC). | **CONCLUÍDO** | Estrutura Flask/React (Frontend/Backend) criada e versionada. |
| Criar o arquivo `.gitignore`. | **CONCLUÍDO** | `.gitignore` atualizado para Python, Node.js e arquivos de IDE (.idea/). |
| Criar o Markdown Guia (Gitflow/CC). | **ADIADO** | Nova data: 30/10. |
| Criar o arquivo de Ambiente Padrão. | **ADIADO** | Nova data: 31/10. |
| Definir/Criar o banco de dados inicial (MySQL). | **ADIADO** | Agora dividido em Modelagem (Todos) e Criação (Eduarda). |
| Criar *branches* iniciais para cada *feature*. | **ADIADO** | Dependente da definição das tabelas. |

---

### 🎯 Novas Tarefas e Prazos

O foco da próxima etapa é a **Modelagem do Banco de Dados** e a finalização da infraestrutura de documentação e ambiente.

#### 1. 📋 Divisão de Responsabilidades

| Tarefa | Responsável | Prazo |
| :--- | :--- | :--- |
| Terminar a Configuração do Repositório de Documentação (MkDocs). | **Gabriel** | 30/10/2025 |
| Criar o Markdown Guia (Conventional Commits/Gitflow). | **Gabriel** | 30/10/2025 |
| Estruturar as Tabelas (Modelagem do Projeto Inteiro). | **Todos** | 30/10 ou 31/10/2025 |
| Criar o Banco de Dados (Implementação). | **Eduarda** | 31/10/2025 |
| Criar o Arquivo de Ambiente Padrão (`.env.example`). | **Eduarda** | 31/10/2025 |

#### 2. 💡 Decisões e Notas Técnicas

* **Modelagem de Dados:** O grupo deverá usar a documentação do pacote `DBI` como referência para estruturar o modelo de dados antes de iniciar o código.
* **Base de Desenvolvimento:** A modelagem das tabelas é o principal impedimento (blocker) para iniciar o desenvolvimento de *features*.

---

### 📝 Próximos Passos

Gabriel deve focar em finalizar a infraestrutura (`docs` e `guia CC/Gitflow`) até o dia 30/10. O grupo deve colaborar na modelagem das tabelas do projeto inteiro.