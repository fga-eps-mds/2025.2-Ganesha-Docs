# 📖 Guia de Configuração do Repositório de Documentação (MkDocs)

Este guia padroniza o ambiente de desenvolvimento para a documentação, garantindo que todos os membros da equipe possam editar, visualizar e publicar o conteúdo Markdown usando o MkDocs.

## 1. ⚙️ Pré-Requisitos

Antes de começar, certifique-se de que você tem:

* **Python 3:** Instalado e no seu `PATH`.
* **Git:** Instalado.

## 2. 🐍 Configuração do Ambiente Python (Venv)

É fundamental isolar as dependências da documentação usando um Ambiente Virtual (`venv`).

### 2.1. Criação do Venv

Abra o terminal na raiz do repositório (`2025.2-Ganesha-Docs`) e execute:

```bash
# Cria a pasta 'venv' para isolamento
python -m venv venv